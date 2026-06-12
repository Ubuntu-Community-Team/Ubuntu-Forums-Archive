---
title: "Help needed with wireless settings in 7.1"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by eugene_kan on 2008-11-13
[FONT="Times New Roman"][SIZE="3"]Dear all! I have now spent many hours trying to fix it, so could you please help – I am completely new to Ubuntu – so some things may not seem obvious to me -:))

I have installed Ubuntu 7.1 on my Compaq Presario F500 laptop recently, and cannot get wireless working with my router.

I've got a PC running under Windows XP which is connected to Internet via LAN. So the idea is to set up my Belkin 54g router as a wireless access point so that I can have Internet on the laptop.

Ubuntu can see my router (yes, the light is blue), and it even connects to Belkin as a local network. But when it comes to internet, nothing happens. I also can access internet-based interface of my Belkin router from the laptop, but unfortunately I've got no idea what settings I should use. Strangely enough I cannot access this internet based interface from my Win XP PC... 

I already tried setting a new wireless network in XP, and then adding a new computer (i.e. Ubuntu laptop) to it using WEP-key. It seemed to recognize the network, but I still can't get Internet access.
I am afraid I would need a step-by-step guide to solve that problem...

Many thanks to everybody in advance[/SIZE][/FONT]

Here are the results of ifconfig and lshw -C network:

yevgeny@yevgeny-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:E8:90:F4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1A:73:24:C3:0A  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe24:c30a/64 &#1056;”&#1056;&#1105;&#1056;°&#1056;&#1111;&#1056;°&#1056;·&#1056;&#1109;&#1056;&#1029;:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:22 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1240 (1.2 KB)  TX bytes:13827885 (13.1 MB)
          Interrupt:255 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1056;”&#1056;&#1105;&#1056;°&#1056;&#1111;&#1056;°&#1056;·&#1056;&#1109;&#1056;&#1029;:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

yevgeny@yevgeny-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:24:c3:0a
       width: 32 bits

---

