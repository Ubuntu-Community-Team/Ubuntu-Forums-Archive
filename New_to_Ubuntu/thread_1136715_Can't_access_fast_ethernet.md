---
title: "Can't access fast ethernet"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by mrcycling on 2009-04-25
Just another newbie question ... I have been trying out Ubuntu for a bit now in hopes of saying bye bye to Windoze, but have been completely unable to get my fast ethernet adapter to function.  I have been searching the forums and web, trying the suggestions from various posts without success.  I held off on posting my question until the release of 9.04 in case it had the magic cure, but alas I still can not access the internet via my ethernet.

Currently have Ubuntu 9.04 dual booted with Vista on a two year old Gateway laptop.  I know the issue is not physical with either the cables or usb to fast ethernet adapter, as everything works fine when running in Vista (that is how I am posting at the moment).  

Based on the Network Manager it seems the system knows of the adapter, but it is listed as disconnected and it is greyed out without a select button.  And below the two wired network listings are a number of nearby wireless points, all with a select button.

Network Manager at top bar:
Wired Network (ADMTek ADM8511 Pegasus II Ethernet)
disconnected

Wired Network (GATEWAY 2000 88E8038 PCI-E Fast Ethernet Controller)
disconnected



After reading some of the other posts, I have already done some of the common "check this and let us know" requests from before ...


mrcycling@ubuntu:~$ lspci -v
02:00.0 Ethernet Controller: Marvell Technology Group Ltd  88E8038 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: Gateway 2000 Device 0366
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at d4000000 (64 bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

03:00.0 Network Controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1000
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at d6000000 (32 bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945



mrcycling@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:eb:bb:18  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3952 (3.9 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:30:be:10:60:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 



mrcycling@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:eb:bb:18  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3952 (3.9 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:30:be:10:60:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15032 (15.0 KB)  TX bytes:15032 (15.0 KB)


mrcycling@ubuntu:~$ lsusb
Bus 002 Device 002:ID07a6:8511 ADMtek ADM8511 Pegasus II Ethernet
...

---

### Post by The Cog on 2009-04-25
Am I right in thinking you had a cable plugged into one of those ethernet ports when you did the ifconfig listings? I see that eth0 shows the word RUNNING which normally means that a cable is plugged in and working.

However, the packet counters show no packets sent or received, which is not a good sign. Do you want to use DHCP, or static IP configuration? If DHCP, try the command **sudo dhclient** and see where it gets you, then **ifconfig** to see if packets have been sent or received and an IP address assigned.

---

### Post by mrcycling on 2009-04-25
I ran with sudo dhclient, it showed several lines of 'listening" and "sending", then proceeded with several tries of DHCPDISCOVER through the various eth0, eth1, lo, etc.  And then finished with NO DHCPOFFERS received.

And ifconfig showed no packets for eth0 or eth1.

On a side note to The Cog, I noticed an example you posted in response to another thread "network issue in jaunty", it had the same ip addresses as I do now.  Are you not in London at the moment ?

---

### Post by The Cog on 2009-04-25
Sorry, I don't know what's wrong then. The lack of a packet count even after dhclient tried to send DHCP requests suggests maybe a driver problem.  But that is pretty-much what you suspected already. 

Addresses beginning with 192.168 are not public internet addresses. They are guaranteed never to be assigned publicly. So they are commonly used in private networks the world over. So are 172.16.0.0-172.31.255.255 and anythong beginning with 10.. These address ranges are always hidden from the internet behind address translating routers. I am still in London.

---

### Post by mrcycling on 2009-04-25
Thanks for the info about 192.168 ... ya learn something new everyday.

Now if I can just figure out how to get the jaunty jackalope to connect with the internet ....

As a total neophyte, any suggestions on checking the driver, testing and / or replacing ?

---

### Post by mrcycling on 2009-04-26
Tried booting without the USB Fast Ethernet adapter plugged in (as suggested in another thread).  When I plugged it in the Network manager showed the adapter (greyed out) but listed it as "device not managed", then later changed status to "disconnected"

---

### Post by The Cog on 2009-04-26
I discovered yesterday (in another post here) that the command **lspci -v** tells you which drivers are in use on all your PCI devices. Nice to know. 

Don't trust the network manager. Go underneath it and use the command line utilities to see what's really happening. Things like lshw, lspci -v, ifconfig -a.

---

### Post by mrcycling on 2009-04-27
At this point nothing much is bringing me forward.  I did plug in my phone (running Windows Mobile 6) and Ubuntu hooked up to the internet through it.  But I will be darned if I can get the fast ethernet adapter to work.

Hopefully someone will be able to forward some other avenues to try or instructions of something else to configure.

---

### Post by mrcycling on 2009-04-28
Bumping it up one last time in hopes that someone might have an idea.  Otherwise it looks like windoze wins round two.  I like everything else about Ubuntu, but if I can't access the internet with it, I can't work ... kind of like a glass hammer for a carpenter ... looks nice but useless for work.

---

