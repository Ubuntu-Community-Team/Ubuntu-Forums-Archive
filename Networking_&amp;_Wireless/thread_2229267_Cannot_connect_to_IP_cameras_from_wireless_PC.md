---
title: "Cannot connect to IP cameras from wireless PC"
date: 2014-06-12
forum: Networking &amp; Wireless
---

### Post by SageOfSmeg on 2014-06-12
Long posting, sorry!
 
Details...
Wireless Access Point 1, primary
- WAP#1
- ZyXEL WAP3205
- Host Name: WAP3205
- IP address: 192.168.1.60
- Access Point Mode
 
Wireless Access Point 2, repeater
- WAP#2
- ZyXEL WAP3205
- Host Name: WAP3205Ext1
- IP address: 192.168.1.80
- Universal Repeater Mode
 
PC1 ("Protek")
- Intel Pentium II, 350 MHz
- Type: desktop
- OS: (dual boot) Windows98/Lubuntu12.04
- Name: gjdpc1
- Connections
-- Wired, IP address: 192.168.1.61
-- Wireless (none)
 
PC2 (self-build)
- Intel Pentium 4, 3.0GHz
- Type: desktop
- OS: (dual boot) WindowsXP/Ubuntu12.04
- Name: gjdpc2
- Connections
-- Wired, IP address: 192.168.1.62
-- Wireless, IP address: 192.168.1.72
 
PC3 (ASUS Eee Pc 4g-bk026)
- Intel Celeron M, 900MHz
- Type: mini netbook/laptop
- OS: Lubuntu12.04 (only)
- Name: gjdpc3
- Connections
-- Wired, IP address: 192.168.1.63
-- Wireless, IP address: 192.168.1.73
 
IP Camera #1
-- Wireless, IP address: 192.168.1.101:5387
 
IP Camera #2
-- Wireless, IP address: 192.168.1.102:...
etc. for up to 6 cameras
 
I have DHCP switched off on all devices, they all use static IP addresses.
All IP addresses are on subnet 255.255.255.0
All are using the same gateway (192.168.1.43) and DNS servers where applicable.
MAC Address filtering has been disabled.
 
Problem...
I cannot connect to any of the IP cameras dotted around my home if I am using a wireless service from my laptop (gjdpc3) or main desktop PC (gjdpc2).
If I use wired connections on gjdpc1/2/3 then there is no problem, but wireless connections produce the error:  "Firefox can't establish a connection to the server at 192.168.1.101:5387"
and so on for each camera.
This happens in Firefox, Chromium and other browsers, so I am assuming that it not a browser issue but a networking issue.
It also happens regardless of which operating system I am using - Windows/Ubuntu/Lubuntu.
All other internet access is successful. I can successfully connect between each PC using ssh.
 
My main wired broadband router has port redirection capabilities that I have enabled on my cameras for access when I am away from home. Interestingly, if I try and connect using the PUBLIC port redirection IP addresses I can connect to the cameras without any problems. It is only the LOCAL IP addresses that throw up this connectivity issue.
 
Based on what I have explained, I am wondering if this issue relates to the fact that I am trying to connect to my cameras (using the local 192.168.1.101/2/3/etc. addresses) when also using my laptop on wireless connections within the same building using the same wireless access points.
 
Any suggestions/clues?
 
 
For reference...
```
gjd@gjdpc3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:28:b4:1b
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000
 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:149458 (149.4 KB)  TX bytes:149458 (149.4 KB)
 
wlan0     Link encap:Ethernet  HWaddr 00:15:af:8c:98:2c
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe8c:982c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1458763 (1.4 MB)  TX bytes:190385 (190.3 KB)
 
 
 
gjd@gjdpc3:~$ iwconfig
lo        no wireless extensions.
 
wlan0     IEEE 802.11bg  ESSID:"scrotumfartbox"
          Mode:Managed  Frequency:2.452 GHz  Access Point: CC:5D:4E:4D:44:C7
          Bit Rate=48 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0
 
eth0      no wireless extensions.
 
 
gjd@gjdpc3:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp
 
 
 
gjd@gjdpc3:~$ sudo cat /etc/NetworkManager/system-connections/wired1
[sudo] password for gjd:
 
[802-3-ethernet]
duplex=full
mac-address=00:1F:C6:28:B4:1B
 
[connection]
id=wired1
uuid=42ce496c-0d47-448a-bee9-30cede596036
type=802-3-ethernet
timestamp=1402241113
 
[ipv6]
method=auto
 
[ipv4]
method=manual
dns=<withheld>
addresses1=192.168.1.63;24;192.168.1.43;
 
 
 
gjd@gjdpc3:~$ sudo cat /etc/NetworkManager/system-connections/wireless1
 
[connection]
id=wireless1
uuid=0f01af67-b285-4fd2-91a0-aa37edcf5da0
type=802-11-wireless
timestamp=1402422620
 
[802-11-wireless]
ssid=scrotumfartbox
mode=infrastructure
mac-address=00:15:AF:8C:98:2C
security=802-11-wireless-security
 
[802-11-wireless-security]
key-mgmt=wpa-psk
psk=<withheld>
 
[ipv4]
method=manual
dns=<withheld>
addresses1=192.168.1.73;24;192.168.1.43;
 
[ipv6]
method=auto

```

---

