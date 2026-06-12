---
title: "Asus USB-AC51 (Mediatek) works with wicd, but can't connect with NetworkManager"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by whocarez2 on 2017-01-22
Hello,

I've got a Asus USB-AC51 Wifi dongle and want to use it in Ubuntu 16.04.1 LTS. Compiled the driver (Mediatek mt7610u_sta) and installed it, but I can't connect with NetworkManager (1.2.2-0ubuntu0.16.04.3). It manages the ra0 device as well as the internal wlan0 device and sees all the networks, but no signal strength and I can't connect. 

```
nmcli dev wifi
``` shows the following (first ra0, second wlan0):

```

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TP-LINK_1       <MAC 'TP-LINK_1' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  0       ____  WPA1 WPA2  no        
maxter          <MAC 'maxter' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  0       ____  WPA2       no        
TP-LINK_D69D14  <MAC 'TP-LINK_D69D14' [AC3]>  Infra  7     2442 MHz  54 Mbit/s  0       ____  --         no        
Sunday          <MAC 'Sunday' [AC9]>  Infra  9     2452 MHz  54 Mbit/s  0       ____  WPA1 WPA2  no        
WiFi-0          <MAC 'WiFi-0' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  0       ____  WPA2       no        

SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TP-LINK_D69D14        <MAC 'TP-LINK_D69D14' [AC3]>  Infra  7     2442 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
WiFi-0                <MAC 'WiFi-0' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
TP-LINK_1             <MAC 'TP-LINK_1' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
ambasadoria           <MAC 'ambasadoria' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
maxter                <MAC 'maxter' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
Sunday                <MAC 'Sunday' [AC9]>  Infra  9     2452 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no        
Global Apple Network  <MAC 'Global Apple Network' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
2.WiFi-0              <MAC '2.WiFi-0' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
Keenetic-5214         <MAC '2.WiFi-0' [AN18]>  Infra  1     2412 MHz  54 Mbit/s  17      &#9602;___  WPA2       no        
Admin                 <MAC 'Admin' [AC11]>  Infra  1     2412 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        

```

Strange is, that if I use wicd it sees not only the networks, but also can connect. So there is a problem with the NetworkManager.
The whole configuration ist here: [ATTACH]273313[/ATTACH]

Any solution? Thank you!

---

### Post by whocarez2 on 2017-04-20
I could solve the problem by myself. It turned out, that **upstart** was still installed. Maybe that hindered NetworkManager to start properly with the USB dongle inserted. To exclude problems with systemd and NetworkManager I reinstalled all already installed packets. Now it is working. The following commands brought me the solution.

```

sudo apt-get remove --purge upstart

sudo dpkg --get-selections | grep -v deinstall | grep systemd
apt-get install --reinstall libpam-systemd libsystemd-dev libsystemd0 python3-systemd systemd systemd-shim systemd-sysv

sudo dpkg --get-selections | grep -v deinstall | grep network-manager
sudo apt-get install --reinstall network-manager network-manager-gnome network-manager-openvpn network-manager-pptp

```

After a restart everything worked as it should and I could remove **wicd** too.

---

