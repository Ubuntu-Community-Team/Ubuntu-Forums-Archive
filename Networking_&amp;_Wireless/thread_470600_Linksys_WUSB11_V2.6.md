---
title: "Linksys WUSB11 V2.6"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by Bartikky on 2007-06-11
Hi, I''ve been having problems connecting to my wireless router in order to get on the internet. Initially Ubuntu connected to my neighbours unsecured wireless router without me having to help, I first assumed that it had connected to my router but later looked at properties of the wireless connection and unticked free roaming to find that the only router it had picked up was not mine. 

Ubuntu now and again picked up my router but couldn't get it to connect, I entered in the wireless name (ESSID) 'BTVOYAGER2091-6B', enter in the network password with WEP (hexadecimal) selected. I then selected Static IP Adress and entered in the IP address, Subnet mask (which it automatically inserts after I've inserted the IP) and the Gateway address. I've installed ndiswrapper-utils-1.9 (architexture: i386) and ndiswrapper-common.

I'll be back with an ouput of the commands iwconfig and lsusb...

EDIT: Here are the posts, along with ifconfig, I hope these all help

> 'lsusb'

Bus 005 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 005 Device 002: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 005 Device 005: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0ed1:6680 WinMaxGroup USB Flash Disk 64M-B
Bus 002 Device 001: ID 0000:0000  

'iwconfig'

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"BTVOYAGER2091-6B"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

'ifconfig'

eth0      Link encap:Ethernet  HWaddr 00:0F:EA:A1:9D:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:450 (450.0 b)  TX bytes:450 (450.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:0C:B9:A0  
          inet6 addr: fe80::20c:41ff:fe0c:b9a0/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:90 (90.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:0C:41:0C:B9:A0  
          inet addr:169.254.6.183  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST  MTU:1500  Metric:1

I also installed WUSB11v4_08272004_dr%2C0.exe driver. There's some other things I changed in Network Settings aswell, but I can't quite remember what I've done... By the way this is Ubuntu 7.04 Feisty Fawn I'm using.

---

### Post by ugm6hr on 2007-06-11
Haven't got that wifi card, but it might be worth taking head of the ndiswrapper advice:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

It suggests using ndiswrapper with lswlusb.inf from:
[ftp://ftp.linksys.com/pub/network/wusb11v25.zip](ftp://ftp.linksys.com/pub/network/wusb11v25.zip)

I found ndisgtk useful to chose your .inf file for ndiswrapper (using GUI), and then add ndiswrapper to modprobe (can't remember how I did that).

---

