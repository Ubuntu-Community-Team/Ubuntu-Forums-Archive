---
title: "atheros help please"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Pooka2132 on 2008-05-15
I've followed several different threads and Ive tried using unencrypted,wpa,wep and wpa2. I have disable the hal on the atheros and see it says its an ar242x but in fact it is a 5700.
Unbuntu 8.04 hardy 64 bit installed dual boot vista home premium.
Compaq 6700 everything else works great and I did order a wireless usb more compatible but I would to get this one figured out too.

any gurus wanna help this newb out would be appreciated.


WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:05:7f:f2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.103 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:1a:5d:99
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.51+,06/21/2007,5.3.0.56 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
pooka@pooka-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:05:7f:f2  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe05:7ff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:826727 (807.3 KB)  TX bytes:145988 (142.5 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13574 (13.2 KB)  TX bytes:13574 (13.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:1a:5d:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f6000000-f6010000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3a:1a:5d:99  
          inet addr:169.254.5.83  Bcast:169.254.255.255  Mask:255.255.0.0WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:05:7f:f2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.103 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:1a:5d:99
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.51+,06/21/2007,5.3.0.56 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
pooka@pooka-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:05:7f:f2  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe05:7ff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:826727 (807.3 KB)  TX bytes:145988 (142.5 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13574 (13.2 KB)  TX bytes:13574 (13.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:1a:5d:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f6000000-f6010000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3a:1a:5d:99  
          inet addr:169.254.5.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f6000000-f6010000 

pooka@pooka-laptop:~$ 


          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f6000000-f6010000 

pooka@pooka-laptop:~$

---

### Post by Thanoulis on 2008-05-15
I'm not sure if this gonna help, but, did you try the *madwifi* driver?

---

### Post by Pooka2132 on 2008-05-15
yes that was one of the solutions Ive tried, when doing that one the machine did not see any wireless cards. using the wrapper it sees it and sees the beacon of my router I just can't connect.

---

### Post by packman1234 on 2008-05-16
I have the exact same card and problem!!
Please let me know if someone figures it out..

Thanks
Bob

---

### Post by T3h_Dohtem on 2008-05-16
ive been fighting with this on my laptop for months, everything i can find seems to show that this is an ongoing problem.

linux + atheros = fail

i have seen that some people say certain older revisions of the madwifi driver are actually able to run different cards, you just have to find the right revision for your specific chipset :/

the closest i've come is at one time being able to connect to my router flawlessly with excellent speeds from far outside my house, but when i go back inside it won't connect until i'm less than four feet from my router. even then it shows signal strength at about 50%

this is by far the strangest problem i have ever had with ubuntu, and the longest running. although, i must say, i've had no better luck with the 3 or 4 other distros i tried as well, it's not an ubuntu specific problem

bump, anyone have any luck with this yet?

---

### Post by nicedude on 2008-05-16
TO ANYONE WITH A AR5007 WIRELESS ADAPTER USING HARDY HERON 8.04

The best driver available for your card is the madwifi driver ( madwifi help ticket #1679 ) but to use it you must use 32bit Ubuntu as there are no 64bit drivers available at this time.

If you want to use your card with 64bit then you must use Ndiswrapper to use your card ( This is not the best solution and you will be limited in its functions ) 

WIth Ndiswrapper drivers you will not be able to use MONITOR mode with your card so no kismet etc.

The 32bit Ubuntu software will work just fine to run your 64bit PC ( And I see no difference in performance between the two in normal use ). For example while I write this I am watching a movie as well on my laptop and it all plays just fine, so unless you will be compiling rainbow cracking tables with your machine or some other insane CPU intensive task you will not notice a difference.

I have made a step by step guide for installing AR5007 into hardy heron 8.04 that works 100% - it is lengthy and requires you to remove some things from default install to allow your card to function properly

I assure you it works however since I am writing this with madwifi AR5007 over a 128bit WEP connection right now ( I know WEP can be cracked but I use it since its simple and I am 300 Yards from the road so you would have to be on my land to crack it - and well within rifle range :-) ) it will function with wap as well for those who live in a congested wifi environment and need the security.

HERE IS LINK TO MY GUIDE READ THE WHOLE THING BEFORE STARTING SO YOU WILL UNDERSTAND WHAT YOU WILL BE DOING

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

---

