---
title: "[SOLVED] Wireless doesn't work - sort of"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by MarkHowells on 2008-07-10
Hi,

I'm struggling to get Kubuntu 8.04 w KDE4 onto a Dell Laptop and have it use my wireless interface (Intel 3945ABG) ... :(

KNetworkManager reports "No active device".  However the drivers are working OK (I think) as iwlist reports;

[FONT="Courier New"]$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:37:B9:17
                    ESSID:"MyESSID"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=84/100  Signal level=-49 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000044d258b120
[/FONT]
but 
[FONT="Courier New"]dhclient wlan0[/FONT]

gives no joy and leaves the interface unaffected. I've read that the interfaces file can cause problems but mine only contains the loopback entry 

[FONT="Courier New"]$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
[/FONT]
...that should leave both the wired and wireless interfaces available to be managed by KNetworkManager right? 

I'm a bit stumped as to what to do next. Any help would be appreciated.

Cheers

Mark

---

### Post by MarkHowells on 2008-07-12
Well, a simple answer. I simply added my username to the group 'netdev' 

[FONT="Courier New"]sudo usermod -a -G netdev mark[/FONT]

logout and login and all is well.

---

