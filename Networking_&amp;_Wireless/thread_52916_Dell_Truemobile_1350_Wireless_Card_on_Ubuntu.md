---
title: "Dell Truemobile 1350 Wireless Card on Ubuntu"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by Larry Kubin on 2005-07-29
Hello everyone. I need a little help getting my Dell 1350 Wireless card working on Kubuntu 5.04. I used ndiswrapper to install the card using the windows driver. I believe I installed everything correctly. However, when I try to actually connect to a wireless network, I get:

"No DHCPOFFERS received.
No working leases in persistent database - sleeping."

I will show the details of what I did so far:

First step: I installed the ndiswrapper-utils package. Everything is fine so far.


larry@ubuntu:/var/cache/apt/archives$ sudo dpkg -i ndiswrapper-utils_0.12+1.0rc2-1_i386.deb
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 58795 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper-utils_0.12+1.0rc2-1_i386.deb) ...
Setting up ndiswrapper-utils (0.12+1.0rc2-1) ...


Next step: I use ndiswrapper -i [my wireless driver]. This works fine.


larry@ubuntu:/$ sudo ndiswrapper -i /media/windows/Dell/Drivers/R81433/AR/bcmwl5a.inf
Installing bcmwl5a
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2

Then I used ndiswrapper -l to make sure my ndis driver is installed. Everything looks good:


larry@ubuntu:/$ ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present, hardware present


Then I do modprobe ndiswrapper -- things work as expected


larry@ubuntu:/$ sudo modprobe ndiswrapper
larry@ubuntu:/$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper


Running ifconfig yields:


larry@ubuntu:~$ ifconfig

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6656 (6.5 KiB)  TX bytes:6656 (6.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0B:7D:0B:A6:B5
          inet6 addr: fe80::20b:7dff:fe0b:a6b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:e0204000-e0205fff

running iwconfig yields:


wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Now when I run dhclient wlan0 I can't seem to connect to an access point. It scans but nothing is found. In KWifiManager, the connection speed/signal strength lights up green like everything is working, but it can't find any networks. Any ideas?

larry@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0b:7d:0b:a6:b5
Sending on   LPF/wlan0/00:0b:7d:0b:a6:b5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by spd106 on 2005-07-30
Does **$sudo iwlist wlan0 scan** find your AP?

Have you tried setting the essid?
**$sudo iwconfig wlan0 essid mshome**

It might be worth trying out the later source packages from the ndiswrapper website.

Hope this helps

---

### Post by fxalpha on 2005-08-12
Your ap is broadcasting and offering DHCP? You've prolly checked but when i got my 5port+wlan, the wlan was off. DHCP was enabled by default but wireless was disabled out of the box. i connected via cable then enabled wlan

---

### Post by Larry Kubin on 2005-08-13
I finally got my Dell 1350 card to work. This is on an Inspiron 700m. In case anyone else is interested:

The specific driver I used was in R94827.EXE from the Dell FTP site at:

[ftp://ftp.dell.com/network/](ftp://ftp.dell.com/network/)

I installed the Dell drivers in windows. Then I used ndiswrapper with bcmwl5a.inf (this file is in the drivers directory). 

I also had to change RadioState 0 to RadioState 1 in all of the *.conf files in the /etc/ndiswrapper/bcmwl5a directory.

To do this I typed:

sudo sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5a/*.conf

I found out about this extra step in the thread on wireless cards with Broadcom chipsets:

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

Thanks for your help everyone.

---

### Post by dizbah on 2005-08-19
Installed ndis drivers:
bcmwl5  invalid driver!
bcmwl5a invalid driver!

how do I fix this?

---

### Post by mindfrost82 on 2005-11-26
[QUOTE=dizbah]Installed ndis drivers:
bcmwl5  invalid driver!
bcmwl5a invalid driver!

how do I fix this?[/QUOTE]

I'm having the same problem no matter what driver I use.  I'm using Ubuntu 5.10.

---

