---
title: "wireless card bc4318 problems iwconfig"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by bootandy on 2007-11-20
Hi,

Firstly I'm fairly new to Ubuntu and I think I've missed some crucial step out in getting my wireless card to work.

I have followed several wireless card driver guides such as this one. Using both the native and the bcm43XX driver with no luck:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

My system:
OS: gutsy gibon, 64bit clean install
Processor: 64bit intel core duo ,
Wireless card: (Linksys) BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

I am dual booting this machine with Windows XP which uses the network card fine & connects to the internet fine.

There are several wireless networks in my area I can see *none* of them in Ubunutu with tools like wifi-radar. 

My wireless network does use WPA encryption.

Cut and paste of command line:

>> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:F8:B1:40:B3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:febfe000-fec00000 

eth0:avah Link encap:Ethernet  HWaddr 00:18:F8:B1:40:B3  
          inet addr:169.254.8.155  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:febfe000-fec00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93920 (91.7 KB)  TX bytes:93920 (91.7 KB)


>>iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

>less /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp
wpa-driver wext
wpa-ssid BeBox
wpa-essid BeBox
wpa-ap-scan 2
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk ##cut##


Firstly I note that my network card has the 'ESSID' set to 'off/any' despite the fact that I have configured it to be BeBox in the interfaces file. I suspect this is the problem but I dont know how to fix it.

Any ideas?
cheers,
andy,

---

### Post by hooah212002 on 2007-11-20
Have you tried WICD? or just network manager. I have the same card and it works just fine.

---

### Post by bootandy on 2007-11-22
Yes i've tried the network manager and WiCD.

I think I'm going to re-install ubuntu and try again.

---

