---
title: "Wireless connects to AP but no IP addres"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by bollo on 2007-12-28
I am using Ubuntu 7.10 and can connect to my router via hardware OK. I need to switch to wireless and can not get it to work. The NIC can connect to AP but I am not getting an IP address back from the router. In the syslog I see messages for DHCPDISCOVER and then NO DHCPOFFERS received.

NIC: Linksys WUSB54G v4
Router: Linksys WRT54G v8

iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"paustin"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1D:7E:56:49:B1   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:56:49:B1
                    ESSID:"paustin"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz
                    Signal level=-39 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000022598bb48b

sudo lshw -C network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:9a:f4:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

cat /etc/network/interfaces
auto lo
iface lo inet loopback
#iface eth0 inet dhcp
auto ath0
#iface ath0 inet dhcp
iface eth0 inet dhcp
iface wlan0 inet dhcp
wpa-psk 6543feecab646cf82e3772c4a010e53a01cb7be7d0087fd626d023e3297
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid paustin
auto wlan0
auto eth0

---

### Post by rustybronco on 2007-12-28
Try this method  [http://ubuntuforums.org/showthread.php?p=3609183#post3609183](http://ubuntuforums.org/showthread.php?p=3609183#post3609183)
I know it works with wep encription, then you will have the get wpa working.

---

### Post by bollo on 2007-12-29
I tried the RT2570 driver and still get the same result. The NIC can attach to AP but I can not get an IP address.

Any other ideas?

---

