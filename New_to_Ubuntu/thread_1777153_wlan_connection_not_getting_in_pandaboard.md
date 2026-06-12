---
title: "wlan connection not getting in pandaboard"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by ssprabu on 2011-06-07
Hiiiiiiiiiiiiiiii,
i am using panda board omap4..and i succeeded in implementing android froyo L27.10.2 in this .then i booted successfuly,after that i tried to enable wifi.it scanned successfully and showed nearby asscess points.but when tried to connect to our wifi host accesspoint,which password we know...it shows like this.......


../Connection> Bssid_list, Connect, Disassociate, Status, Full_bssid_list, wPs/
c                                                                               
ADDRCONF(NETDEV_CHANGE): tiwlan0: link becomes ready                            
TIWLAN: 1604.389426: conn                    , CONSOLE:-------------------------
TIWLAN: 1604.398032: conn                    , CONSOLE:               CONN LOST 
TIWLAN: 1604.406576: conn                    , CONSOLE:-------------------------
TIWLAN: 1604.415151: -------------------------------------                      
TIWLAN: 1604.420613:                CONN LOST       

i am giving my wpa_supplicant.conf here...


ctrl_interface=tiwlan0
update_config=1
ap_scan=1
eapol_version=1
fast_reauth=1
network={
    ssid="SpanIDEA_WL"
    scan_ssid=1
    key_mgmt=WPA-PSK
	psk="1b4490f11e7243c86dadd54d87e917b9daf5a9e22b1a0bad2dcf3177fdba7c30"
    eap=wext
    priority=1
}

is any modification needed here????


pls help......

regards
 s sprabu

---

