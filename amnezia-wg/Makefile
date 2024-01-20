# This is free software, licensed under the MIT License.

include $(TOPDIR)/rules.mk

PKG_NAME:=amneziawg-go
PKG_VERSION:=0.1.8
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/amnezia-vpn/amneziawg-go/archive/refs/tags/v${PKG_VERSION}
PKG_HASH:=6021478e0600b544cabde03d1d2a0dfcee8b1ddf42b6037ea2e216250133c027

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
#PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/amnezia-vpn/amnezia-wg
GO_PKG_LDFLAGS_X:=\
	main.Build=$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../../packages/lang/golang/golang-package.mk

define Package/amneziawg-go
  SECTION:=net
  CATEGORY:=Network
  TITLE:=amnezia-wg
  DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Build/Compile
  $(call GoPackage/Build/Compile)
endef

define Package/amneziawg-go/description
  AmneziaWG is a contemporary version of the WireGuard protocol. It's a fork of
  WireGuard-Go and offers protection against detection by Deep Packet Inspection
  (DPI) systems. At the same time, it retains the simplified architecture and
  high performance of the original.
endef

define Package/amneziawg-go/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/amnezia-wg $(1)/usr/sbin/
endef

$(eval $(call GoBinPackage,amneziawg-go))
$(eval $(call BuildPackage,amneziawg-go))
