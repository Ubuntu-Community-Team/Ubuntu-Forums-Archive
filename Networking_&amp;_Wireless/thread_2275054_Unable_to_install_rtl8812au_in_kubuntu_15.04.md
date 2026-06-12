---
title: "Unable to install rtl8812au in kubuntu 15.04"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by Tim_Jutte on 2015-04-24
I am pretty new to linux, and also forum posts generally. So, I apologize about any formatting errors or issues with my question, but I can't seem to figure this one out via lurking.

I upgraded to kubuntu 15.04 and my TP-Link T4U USB wireless adapter stopped working. I was using the rtl8812au driver in 14.10 and 14.04, but when i try to compile it in 15.04, I get the following error after using the make command in the terminal:

```
 [FONT=monospace][COLOR=#000000]cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko [/COLOR]
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko 
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order 
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~ 
rm -fr .tmp_versions 
tim@tim-All-Series:~/Downloads/driver/rtl8812AU_8821AU_linux-master$ make 
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.19.0-15-generic/build M=/home
/tim/Downloads/driver/rtl8812AU_8821AU_linux-master  modules 
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-15-generic' 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_cmd
.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_sec
urity.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_deb
ug.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_io.
o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_ioc
tl_query.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_ioc
tl_set.o                                                                        
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_iee
e80211.o                                                                        
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_mlm
e.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_mlm
e_ext.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_wla
n_util.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_vht
.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_pwr
ctrl.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_rf.
o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_rec
v.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_sta
_mgt.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_ap.
o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_xmi
t.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_p2p
.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_tdl
s.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_br_
ext.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_iol
.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/rtw_sre
set.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/core/efuse/r
tw_efuse.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/osdep
_service.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/os_intfs.o 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/os_intfs.
c:1695:2: warning: initialization from incompatible pointer type 
  .ndo_select_queue = rtw_select_queue, 
  ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/os_intfs.
c:1695:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/usb_intf.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/usb_ops_linux.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/ioctl_linux.o 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_lin
ux.c: In function ‘rtw_mp_efuse_get’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_lin
ux.c:8887:65: warning: iteration 16u invokes undefined behavior [-Waggressive-l
oop-optimizations] 
     sprintf(extra, "%s%02X ", extra, pEfuseHal->fakeEfuseInitMap[i+j]); 
                                                                 ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_lin
ux.c:8875:3: note: containing loop 
   for (i = 0; i < EFUSE_MAP_SIZE; i += 16) 
   ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_lin
ux.c:9307:69: warning: iteration 16u invokes undefined behavior [-Waggressive-l
oop-optimizations] 
     sprintf(extra, "%s %02X", extra, pEfuseHal->fakeEfuseModifiedMap[i+j]); 
                                                                     ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_lin
ux.c:9295:3: note: containing loop 
   for (i=0; i<EFUSE_MAP_SIZE; i+=16) 
   ^ 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/xmit_linux.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/mlme_linux.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/recv_linux.o 
  CC [M]  /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux
/ioctl_cfg80211.o 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: In function ‘cfg80211_rtw_add_key’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:1250:35: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ 
qualifier from pointer target type 
   _rtw_memcpy(param->u.crypt.seq, params->seq, params->seq_len); 
                                   ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz); 
             ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:1256:35: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ 
qualifier from pointer target type 
   _rtw_memcpy(param->u.crypt.key, params->key, params->key_len); 
                                   ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz); 
             ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: In function ‘cfg80211_rtw_connect’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2550:30: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ 
qualifier from pointer target type 
  _rtw_memcpy(ndis_ssid.Ssid, sme->ssid, sme->ssid_len); 
                              ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz); 
             ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2587:49: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ 
qualifier from pointer target type 
    if(_rtw_memcmp(pnetwork->network.MacAddress, sme->bssid, ETH_ALEN) == _FALS
E) 
                                                 ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern int _rtw_memcmp(void *dst, void *src, u32 sz); 
            ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2593:49: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ 
qualifier from pointer target type 
     || _rtw_memcmp(pnetwork->network.Ssid.Ssid, sme->ssid, sme->ssid_len) == _
FALSE 
                                                 ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern int _rtw_memcmp(void *dst, void *src, u32 sz); 
            ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2601:14: warning: assignment discards ‘const’ qualifier from pointer ta
rget type 
    src_bssid = sme->bssid; 
              ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2682:42: warning: passing argument 2 of ‘rtw_cfg80211_set_wpa_ie’ disca
rds ‘const’ qualifier from pointer target type 
  ret = rtw_cfg80211_set_wpa_ie(padapter, sme->ie, sme->ie_len); 
                                          ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2243:12: note: expected ‘u8 *’ but argument is of type ‘const u8 *’ 
 static int rtw_cfg80211_set_wpa_ie(_adapter *padapter, u8 *pie, size_t ielen) 
            ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: In function ‘cfg80211_rtw_set_pmksa’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2913:20: warning: passing argument 1 of ‘_rtw_memcmp’ discards ‘const’ 
qualifier from pointer target type 
  if ( _rtw_memcmp( pmksa->bssid, strZeroMacAddress, ETH_ALEN ) == _TRUE ) 
                    ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern int _rtw_memcmp(void *dst, void *src, u32 sz); 
            ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2923:59: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ 
qualifier from pointer target type 
   if( _rtw_memcmp( psecuritypriv->PMKIDList[index].Bssid, pmksa->bssid, ETH_AL
EN) ==_TRUE ) 
                                                           ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern int _rtw_memcmp(void *dst, void *src, u32 sz); 
            ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2927:56: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ 
qualifier from pointer target type 
    _rtw_memcpy( psecuritypriv->PMKIDList[index].PMKID, pmksa->pmkid, WLAN_PMKI
D_LEN); 
                                                        ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz); 
             ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2941:74: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ 
qualifier from pointer target type 
   _rtw_memcpy(psecuritypriv->PMKIDList[psecuritypriv->PMKIDIndex].Bssid, pmksa
->bssid, ETH_ALEN); 
                                                                          ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz); 
             ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2942:74: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ 
qualifier from pointer target type 
   _rtw_memcpy(psecuritypriv->PMKIDList[psecuritypriv->PMKIDIndex].PMKID, pmksa
->pmkid, WLAN_PMKID_LEN); 
                                                                          ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz); 
             ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: In function ‘cfg80211_rtw_del_pmksa’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:2967:59: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ 
qualifier from pointer target type 
   if( _rtw_memcmp( psecuritypriv->PMKIDList[index].Bssid, pmksa->bssid, ETH_AL
EN) ==_TRUE ) 
                                                           ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/osdep_service.
h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’ 
 extern int _rtw_memcmp(void *dst, void *src, u32 sz); 
            ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:141:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: In function ‘rtw_cfg80211_rx_action_p2p’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/ioctl_cfg80211
.h:114:71: error: too many arguments to function ‘cfg80211_rx_mgmt’ 
   #define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211
_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp) 
                                                                       ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:3883:2: note: in expansion of macro ‘rtw_cfg80211_rx_mgmt’ 
  rtw_cfg80211_rx_mgmt(padapter, freq, 0, pmgmt_frame, frame_len, GFP_ATOMIC); 
  ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/osdep_service_linux.h:76:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/osdep_service.h:41, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
include/net/cfg80211.h:4612:6: note: declared here 
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm, 
      ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:141:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: In function ‘rtw_cfg80211_rx_p2p_action_public’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/ioctl_cfg80211
.h:114:71: error: too many arguments to function ‘cfg80211_rx_mgmt’ 
   #define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211
_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp) 
                                                                       ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:3921:2: note: in expansion of macro ‘rtw_cfg80211_rx_mgmt’ 
  rtw_cfg80211_rx_mgmt(padapter, freq, 0, pmgmt_frame, frame_len, GFP_ATOMIC); 
  ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/osdep_service_linux.h:76:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/osdep_service.h:41, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
include/net/cfg80211.h:4612:6: note: declared here 
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm, 
      ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:141:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: In function ‘rtw_cfg80211_rx_action’: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/include/ioctl_cfg80211
.h:114:71: error: too many arguments to function ‘cfg80211_rx_mgmt’ 
   #define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211
_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp) 
                                                                       ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:3951:2: note: in expansion of macro ‘rtw_cfg80211_rx_mgmt’ 
  rtw_cfg80211_rx_mgmt(adapter, freq, 0, frame, frame_len, GFP_ATOMIC); 
  ^ 
In file included from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/osdep_service_linux.h:76:0, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/osdep_service.h:41, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
include/drv_types.h:32, 
                 from /home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/
os_dep/linux/ioctl_cfg80211.c:22: 
include/net/cfg80211.h:4612:6: note: declared here 
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm, 
      ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c: At top level: 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5041:2: warning: initialization from incompatible pointer type 
  .get_station = cfg80211_rtw_get_station, 
  ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5041:2: warning: (near initialization for ‘rtw_cfg80211_ops.get_station
’) 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5069:2: warning: initialization from incompatible pointer type 
  .add_station = cfg80211_rtw_add_station, 
  ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5069:2: warning: (near initialization for ‘rtw_cfg80211_ops.add_station
’) 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5070:2: warning: initialization from incompatible pointer type 
  .del_station = cfg80211_rtw_del_station, 
  ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5070:2: warning: (near initialization for ‘rtw_cfg80211_ops.del_station
’) 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5071:2: warning: initialization from incompatible pointer type 
  .change_station = cfg80211_rtw_change_station, 
  ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5071:2: warning: (near initialization for ‘rtw_cfg80211_ops.change_stat
ion’) 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5087:2: warning: initialization from incompatible pointer type 
  .mgmt_tx = cfg80211_rtw_mgmt_tx, 
  ^ 
/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/linux/ioctl_cfg
80211.c:5087:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’) 
scripts/Makefile.build:257: recipe for target '/home/tim/Downloads/driver/rtl88
12AU_8821AU_linux-master/os_dep/linux/ioctl_cfg80211.o' failed 
make[2]: *** [/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master/os_dep/l
inux/ioctl_cfg80211.o] Error 1 
Makefile:1394: recipe for target '_module_/home/tim/Downloads/driver/rtl8812AU_
8821AU_linux-master' failed 
make[1]: *** [_module_/home/tim/Downloads/driver/rtl8812AU_8821AU_linux-master]
 Error 2 
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-15-generic' 
Makefile:1040: recipe for target 'modules' failed 
make: *** [modules] Error 2
[/FONT]

```

and then after sudo make install:

```
 [FONT=monospace][COLOR=#000000]install -p -m 644 8812au.ko  /lib/modules/3.19.0-15-generic/kernel/drivers/net/[/COLOR]
wireless/ 
install: cannot stat ‘8812au.ko’: No such file or directory 
Makefile:1046: recipe for target 'install' failed 
make: *** [install] Error 1[/FONT]

```

After reading numerous posts I installed/upgraded both linux-source and linux-headers, but the result is the same. I cannot figure out how to get the drivers installed.

Thank you in advance for any assistance, and again, I am sorry if I butchered either the question or the post.

---

### Post by rlm703 on 2015-04-24
I have the same issue with my ASUS AC56 adapter which uses the same driver. I have found a few forks of working version with update kernels but they seem to be on old versions of the official release. I have a working (poor) connection which the newer versions (old kernel 3.10) have improved range. I have tried a few items and cant remember exactly when I had it working but i have to start with a fresh install this weekend (ubuntu 15.04) and will get the process down. I will repost once (if) i have some more details. For now, try this fork, also has instructions for build/install. I think this is the fork that worked for me. [https://github.com/scrivy/rtl8812AU_8821AU_linux](https://github.com/scrivy/rtl8812AU_8821AU_linux)

---

### Post by savimonty2 on 2015-04-24
I have the Edimax 1200 USB adapter which uses rtl8812au.
Ubuntu 15.04 which was just released yesterday.
Try this. Worked for me.

I tried patching from [https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch](https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch). 
*(I failed. May be something I'm missing. **This might help some advanced users.*[I]) 

[/I]But I just used the idea from the patches and edited some source by hand. (dirty way I know) 
Was late to work and I needed my 5ghz. 
Tried one last simple shot.

Going back, I cloned a git project from  [https://github.com/scrivy/rtl8812AU_8821AU_linux](https://github.com/scrivy/rtl8812AU_8821AU_linux)

```
git clone https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch
cd rtl8812AU_8821AU_linux
cd include
```

Now I made a small edit (use your own favorite editor)
```

cp ioctl_cfg80211.h ioctl_cfg80211.h.old # create a backup to revert back if you need to in the worst case
gedit ioctl_cfg80211.h
```


Go to line 113/114 and change
```
  
// 3.12 added a flags argument which is just set to zero
#define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp)

```

Change to

```

// 3.12 added a flags argument which is just set to zero //.. I think they reverted back to pre 3.12 .. may be I am wrong
#define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, gfp)
```


Save. Close the editor.


```
cd ..
make
sudo make install
sudo modprobe 8812au
```

Voila! LED turned on. Got my 100 megs.
(uname = Linux pc-name 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux)

Good luck.

---

### Post by Tim_Jutte on 2015-04-24
That worked like a charm, savimonty. I really appreciate all the help guys.

---

### Post by jmunita on 2015-04-25
Works!!! Thanks a lot!!

---

### Post by jettles on 2015-05-08
This works thanks, however it will not reconnect on boot up. I had to execute the last section of code again to get it back up. (Ubuntu 14.04)
Any thoughts?

---

### Post by savimonty2 on 2015-05-08
This set of instructions does not work with Ubuntu 14.04. 
I think I remember using the same git clone from scrivy but _**without**_ the modifications to ioctl_cfg8011.h. 
But I'm not sure.

---

### Post by savimonty2 on 2015-05-08
Now if your Ubuntu 15.04 has been updated by a software center update your uname should be something like this

Current uname = Linux <pc-name> 3.19.0-16-generic #16-Ubuntu SMP Thu Apr 30 16:09:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

This (kernel) update will wipe any new modules you have manually installed. 
IMHO you should be able to make these modules permanent following some other threads. But I've never tried or looked.

Just go back to source folder [COLOR=#000000][FONT=Ubuntu Mono]rtl8812AU_8821AU_linux[/FONT][/COLOR] (modifications to ioctl_80211.h unchanged) and perform the following

```

make clean
make
sudo make install
sudo modprobe 8812au

```

This should turn that LED back on and your 5ghz

---

### Post by Peter_Symmons on 2015-06-02
...sorry I`m very much a beginner, so please be patient, but like you I really want to get at those 5GHz

I have cloned the `scrivy` project but am unable to get the patch into it when I input

git clone [https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch](https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch)
cd rtl8812AU_8821AU_linux
cd include

I get the error message

Cloning into 'linux-3.18.patch'...
fatal: repository 'https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch/' not found
peter@peter-VPCCW17FX:~$ cd rtl8812AU_8821AU_linux
peter@peter-VPCCW17FX:~/rtl8812AU_8821AU_linux$ cd 
peter@peter-VPCCW17FX:~$ 
peter@peter-VPCCW17FX:~$ include
 
I have found the patch and I could copy the source as text so I know its there.  I am probably making some silly syntax error
and would appreciate guidance.

---

### Post by Wagde_Zabit on 2015-08-10
> **savimonty2 said:**
> I have the Edimax 1200 USB adapter which uses rtl8812au.
Ubuntu 15.04 which was just released yesterday.
Try this. Worked for me.

I tried patching from [https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch](https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch). 
*(I failed. May be something I'm missing. **This might help some advanced users.*[I]) 

[/I]But I just used the idea from the patches and edited some source by hand. (dirty way I know) 
Was late to work and I needed my 5ghz. 
Tried one last simple shot.

Going back, I cloned a git project from  [https://github.com/scrivy/rtl8812AU_8821AU_linux](https://github.com/scrivy/rtl8812AU_8821AU_linux)

```
git clone https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch
cd rtl8812AU_8821AU_linux
cd include
```

Now I made a small edit (use your own favorite editor)
```

cp ioctl_cfg80211.h ioctl_cfg80211.h.old # create a backup to revert back if you need to in the worst case
gedit ioctl_cfg80211.h
```


Go to line 113/114 and change
```
  
// 3.12 added a flags argument which is just set to zero
#define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp)

```

Change to

```

// 3.12 added a flags argument which is just set to zero //.. I think they reverted back to pre 3.12 .. may be I am wrong
#define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, gfp)
```


Save. Close the editor.


```
cd ..
make
sudo make install
sudo modprobe 8812au
```

Voila! LED turned on. Got my 100 megs.
(uname = Linux pc-name 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux)

Good luck.

Hi

In your fix the last parameter for the cfg80211_rx_mgmt() is gfp, and in the patch you followed the last parameter is 0.
What should it be? I think it should be 0 because they deleted the gfp parameter

Thanx
Wagde

---

