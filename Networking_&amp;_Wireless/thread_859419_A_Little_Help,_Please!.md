---
title: "A Little Help, Please!"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by wizn3sk1 on 2008-07-14
So I've been trying to connect to my wireless connection for a few weeks now and still have had no luck...
Here's some information for those who might know what they are doing and can offer some help!
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:09:5B:53:6F:BC   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=96/100  Signal level=-38 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:09:5B:53:6F:BC   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=96/100  Signal level=-38 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:77:13:19  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:446211 (435.7 KB)  TX bytes:71968 (70.2 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1728 (1.6 KB)  TX bytes:1728 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:46:b9:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:24688 (24.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-46-B9-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:77:13:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.10 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:fc:46:b9:bc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Also, I've attached a screenshot of my network monitor app as well as the networks that my computer is picking up.  The thing that confuses me is that the network manager shows an 80% connection to 'Wiz' but the network monitor still says disconnected.:(

If there is anything else I might need, let me know!

-wizn3sk1

---

### Post by Embiggens on 2008-07-15
Hi, I'm no expert but it could be a router issue?  Maybe you tried this, but what happens if you type > ping [www.google.com](www.google.com)

---

### Post by wizn3sk1 on 2008-07-17
Hey thanks for replying.
I typed that into the terminal and all I got was:
"ping: unknown host www.google.com"
or something along those lines...
I'm beginning to think it's just my network that doesn't like me anymore since I've switched to Ubuntu...
Any other suggestions??

---

### Post by Embiggens on 2008-07-20
ok, sorry for the slow reply here.  On looking at your initial post again, I realized that you have a connection, but it is through your ethernet interface.  That screenshot indicates that you're connected to wiz, but your command line output does not.  It does appear that your wireless card is recognized correctly, so this should be do-able.  First remove your ethernet connection then enter the following:
> sudo iwconfig wlan0 essid "wiz"
(you need the quotes).  Then typing > iwconfig should show that you're connected to wiz.  Then> sudo dhclient wlan0
This will grab an ip address from your router assuming that's how it's configured. And you should be good at that point. If that works, you can then set up your /etc/network/interfaces file to connect directly to your network when you re-boot.

Depending on what company router you have, you can always test your connection by seeing if you can connect directly to the internal ip address of your router: 192.168.1.1 if it's linksys (not sure about other companies).

Let me know if that works.

---

