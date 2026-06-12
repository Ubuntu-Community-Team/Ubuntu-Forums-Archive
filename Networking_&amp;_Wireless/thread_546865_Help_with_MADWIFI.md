---
title: "Help with MADWIFI"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by peterv6 on 2007-09-09
I have a D-Link 2330 card that is working intermittently in Fiesty.  I'm thinking of trying to update MADWIFI but their site says I need to confirm some system requirements (listed below), but I'm new to Linux, so....

**[COLOR="Blue"]Can someone tell me how to verify these things on my system?[/COLOR]**

** *Linux Kernel 2.4.23+ and 2.6.x series**
 
** *Kernel Source and Headers of running kernel**
** *No module versioning support**
          o option CONFIG_MODVERSIONS 
**  *Wireless Extensions support in kernel**
          o v14+ required, v17+ recommended; option CONFIG_NET_RADIO (kernel 2.6.22 and later: CONFIG_WLAN_80211) 
**    * Sysctl support in kernel**
          o option CONFIG_SYSCTL 
**    * Crypto API support in kernel**
          o option CONFIG_CRYPTO 
**    * HMAC support**
          o option CONFIG_CRYPTO_HMAC 
**    * AES support (for WPA networks)**
          o option CONFIG_CRYPTO_AES 

[B][COLOR="Blue"]Also, how would I check for, and "include" these in the kernel?
[/COLOR][/B]
The following options should be included in your kernel for the best MadWifi experience:
Kernel 2.6.x: ¶

    * Loadable module support &#8594; Module versioning support: disabled
    * Device Drivers &#8594; Network device support &#8594; Wireless LAN (non-hamradio) &#8594; Wireless LAN drivers (non-hamradio) & Wireless Extensions: enabled (NOTE: in kernel v2.6.22.2 (and probably some previous ones) it is located in Networking &#8594; Wireless &#8594; Wireless extensions)
    * Cryptographic options &#8594; Cryptographic API: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; HMAC support: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; AES cipher algorithm: enabled (optional, needed for WPA/WPA2 with CCMP)

**[COLOR="Red"]I'm very grateful for any and all help![/COLOR]**

---

### Post by azimout on 2008-06-30
your kernel configuration is in the /boot/config-<kernel version> file...

---

