---
title: "dell 1450 + ndiswrapper ... No internet on Ubuntu 8"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by camerong on 2008-04-26
Hey,

I deleted windows and installed Ubuntu 8. I can't get my internet working.

I have a dell wireless USB adaptor 1450 and the dellnic.inf loaded into ndiswrapper, but nothing works. here are some outputs for troubleshooting help:

> cameron@cameron-desktop:~$ sudo lshw -C network
[sudo] password for cameron: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:7e:09:78
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.4-1 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:58:c1:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+dellnic driverversion=1.52+Dell,09/26/2004, 3.01.12.0 link=no multicast=yes wireless=IEEE 802.11g


cameron@cameron-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:21 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


cameron@cameron-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:7e:09:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xcce0 Memory:ef7e0000-ef800000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79562 (77.6 KB)  TX bytes:79562 (77.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:58:c1:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:14:a5:58:c1:63  
          inet addr:169.254.7.90  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

cameron@cameron-desktop:~$ ndiswrapper -l
dellnic : driver installed
	device (413C:8104) present (alternate driver: p54usb)


Please help me get this working ASAP. I went through the documentation from the 7.0 docs on setting up wireless to no avail.

Any ideas? Gimma a command and I'll post the output.

---

### Post by camerong on 2008-04-26
cmon.. can anyone help? I can't even use my computer until this gets sorted out. I read all these things about this UBUNTU being more accessable than ever and finally people-ready and it won't even work..

any ideas at all...?

---

### Post by nullmind on 2008-04-27
What happens if you iwlist scan ? Are you trying to use Network Manager, for example using the network applet in the notification area to connect to wireless networks. Have you tried the "Connect to other wireless network" entering your ESSID and keys manually.

Cheers,
Kris

---

### Post by camerong on 2008-04-27
iwlist scan returns all avaliable wireless networks. THere is about 8 of them, all password protected. The applet scan version lists them all correctly also. 

I have tried entering my details manually, and it just tries to connect and fails. As it does when i try to connect when roaming.

I think the problem is that currently the essid is set to any/off. I know this because some command gave me as output "ESSID: any/off"

But I cant figure out how to fix this and when i manually try to (as sudo) set the essid it doesnt do anything. it doesnt give me an error either. it's weird.

any commands i can execute to help clear things up?
thanks, and please help further.

---

### Post by camerong on 2008-04-27
I MADE SOME PROGRESS! a little bit. I followed a stickied tutorial at the top of this section and did the following.

> cameron@cameron-desktop:~$ ndiswrapper -l
dellnic : driver installed
	device (413C:8104) present (alternate driver: p54usb)
cameron@cameron-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:7e:09:78
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.4-1 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:58:c1:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+dellnic driverversion=1.52+Dell,09/26/2004, 3.01.12.0 multicast=yes wireless=IEEE 802.11g
cameron@cameron-desktop:~$ sudo ifconfig wlan0 down
[sudo] password for cameron: 
cameron@cameron-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:a5:58:c1:63
Sending on   LPF/wlan0/00:14:a5:58:c1:63
Sending on   Socket/fallback
cameron@cameron-desktop:~$ sudo ifconfig wlan0 up
**cameron@cameron-desktop:~$ sudo iwconfig wlan0 essid "K6VA3"**
cameron@cameron-desktop:~$ sudo iwconfig wlan0 key 1801549F5C
cameron@cameron-desktop:~$ sudo iwconfig wlan0 key open
cameron@cameron-desktop:~$ sudo iwconfig wlan0 mode Managed
cameron@cameron-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:a5:58:c1:63
Sending on   LPF/wlan0/00:14:a5:58:c1:63
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.5 from 192.168.1.1
DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
[B]No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]


The important parts are in bold, i think. I said I made progress becuase previously my ESSID was set to any/off, and now as you can see from below, it is set to the correct essid:

> cameron@cameron-desktop:~$ ifconfig
eth0
      Link encap:Ethernet  HWaddr 00:12:3f:7e:09:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xcce0 Memory:ef7e0000-ef800000 

lo
        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76884 (75.0 KB)  TX bytes:76884 (75.0 KB)

**wlan0**
     Link encap:Ethernet  HWaddr 00:14:a5:58:c1:63  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe58:c163/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31068 (30.3 KB)  TX bytes:10498 (10.2 KB)

cameron@cameron-desktop:~$ iwconfig
lo
        no wireless extensions.

eth0
      no wireless extensions.

**wlan0**
     IEEE 802.11g  **ESSID:"K6VA3"**  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:F2:67:E1   
          Bit Rate=54 Mb/s   Tx-Power:21 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So how come I'm not getting any DHCP offers?? :confused: Please help, I feel like we're close.

---

### Post by camerong on 2008-04-27
Searching the forums, this appears to be a very common problem but I can't find a single solution posted...

wtf?

---

### Post by camerong on 2008-04-27
I'm writing this from Ubuntu!

I blacklisted all the ISLSMs and "e100". I don't know if this actually did anything. More likely, it just took a few tries on the dhclient command. If I can get this all working via startup script i'll mark this thread as solved. thanks to that guy for this awesome stickied guide, and whomever tried to help here.

---

### Post by kevdog on 2008-04-27
What are ISLMS's?  I not familar with these.

---

### Post by conorsulli on 2008-08-20
This is driving me mad!!! its pathetic that this 1450 usb cant work, I have also looked at many threads

---

