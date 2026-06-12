---
title: "ifconfig cant see wlan0 and other questions"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by IronFox on 2007-06-20
just got done with the mind numbing task of getting my bcm4306 wireless card to work in my zd8115 laptop but, of course, all is still not well.  Used about 4 different tuts here and used ndiswrapper and bcmwl5 drivers to get where i am now.  I have ndiswrapper to turn on during boot but for some reason when i use ifconfig, there is no wireless wlan0.

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid ACTIONTEC
wireless-key xxxxxxxxxxxxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid ACTIONTEC
wireless-key xxxxxxxxxxxxxxxxxxxxxxx


auto eth1


Why did it save my wireless info under eth1 and not wlan0? (I added that to wlan0 but didnt take it off of eth1 in fear of screwing something up)

But still...
> root@jordan-laptop:/home/jordan# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:A2:1F:F2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

No wlan0.  What am I doing wrong? Also i heard if you got your wired still on it can mess with it, but each time i try to disable it, it just turns back on.

---

### Post by kevdog on 2007-06-20
Alright - just a shot in the dark, but look at the contents of your /etc/iftab file.  Likely one of the devices labeled in their need to be changed from eth0/eth1 to wlan0.

If you post the contents of your iftab file Im sure I could help you!

---

### Post by IronFox on 2007-06-20
eth0 mac 00:c0:9f:a2:1f:f2: arp 1
eth1 mac 00:90:4b:ea:ec:09: arp 1

I just renamed eth1 to wlan0 and still nothing comes up on ifconfig, only eth0 and lo.

---

### Post by kevdog on 2007-06-20
Ok, well lets first troubleshoot your ndiswrapper installation

Please post results of:
ndiswrapper -v

and

ndiswrapper -l  <-----That's a lowercase "L"

Let's start there and make sure everything is Ok, then we will proceed.

---

