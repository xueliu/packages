
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lora-gateway
PKG_VERSION:=5.0.1
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/Lora-net/lora_gateway/tar.gz/v$(PKG_VERSION)?
PKG_MD5SUM:=5d07f8471e1a67920787e3879afe0cb6
PKG_MAINTAINER:=Xue Liu <liuxuenetmail@gmail.com>
PKG_LICENSE_FILES:=LICENSE
PKG_BUILD_DIR:=$(BUILD_DIR)/lora_gateway-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/lora-gateway-tests
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=LoRaWAN
  TITLE:=Test programs for lora gateway
endef

define Package/lora-gateway-utils
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=LoRaWAN
  TITLE:=Utilities for lora gateway
endef

TARGET_CFLAGS += $(FPIC) -Wall -Wextra -std=c99 -Iinc -I. -lm \
                -DSPI_SPEED=$(CONFIG_SX1301_SPI_SPEED) \
                -DSPI_DEV_PATH=\\\"\"$(CONFIG_SX1301_SPI_PATH)\\\"\"

define Package/lora-gateway-tests/install
        $(INSTALL_DIR) $(1)/usr/sbin
        $(INSTALL_BIN) $(PKG_BUILD_DIR)/*_test/*_test $(1)/usr/sbin
endef

define Package/lora-gateway-utils/install
        $(INSTALL_DIR) $(1)/usr/sbin
        $(INSTALL_BIN) $(PKG_BUILD_DIR)/util_pkt_logger/util_pkt_logger $(1)/usr/sbin
        $(INSTALL_BIN) $(PKG_BUILD_DIR)/util_spectral_scan/util_spectral_scan $(1)/usr/sbin
        $(INSTALL_BIN) $(PKG_BUILD_DIR)/util_tx_continuous/util_tx_continuous $(1)/usr/sbin
        $(INSTALL_BIN) $(PKG_BUILD_DIR)/util_spi_stress/util_spi_stress $(1)/usr/sbin
endef

$(eval $(call BuildPackage,lora-gateway-tests))
$(eval $(call BuildPackage,lora-gateway-utils))
