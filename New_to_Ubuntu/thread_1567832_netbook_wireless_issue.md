---
title: "netbook wireless issue"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Lexfilez on 2010-09-04
I just installed the newest version of Ubuntu remix today and it all went seemingly fine, but try as I might it will not pick up my wireless router, and I plugged it in by cord to the router and that will not work either. Is there a trick I am missing?:(

---

### Post by candtalan on 2010-09-05
What is the make, type, and model number of your netbook please?

---

### Post by Lexfilez on 2010-09-07
Hp Mini 1010NR, it works plugged in to mthe router but still no wireless. My mini has a button you slid to the left to turn on the wireless.

---

### Post by bredman on 2010-09-07
Can you post the output of the following commands?
ifconfig
iwconfig
lspci

This will tell us
1. What network interfaces are available
2. The WiFi configuration
3. The hardware plugged into your comupter

---

### Post by Lexfilez on 2010-09-18
How would i get those reading? i am a little computer dumb, and sorry for taking a long time to answre i was out of town on business.

---

### Post by candtalan on 2010-09-18
> **Lexfilez said:**
> How would i get those reading? i am a little computer dumb, and sorry for taking a long time to answre i was out of town on business.

Obtain a Terminal (looks like DOS window, but it is not)

You can get a terminal perhaps by:

Applications>Accessories>Terminal

then type into the terminal
ifconfig
(return)

Note the response. It is possible to highlight the text and copy it, and paste it into say, a message here.

Do the same also for 
iwconfig

and then for 
lspci

hth

---

### Post by Lexfilez on 2010-09-18
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:22:64:66:66:0b  
          inet addr:172.16.1.34  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::222:64ff:fe66:660b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2528321 (2.5 MB)  TX bytes:428910 (428.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)




iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDoff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS throff   Fragment thr off
          Power Managementoff


lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

---

### Post by macem29 on 2010-09-18
I'm using that same remix and for some unknown reason when I boot it, every now and
then networking is checked off, minor, but annoying...right clicking on the icon in top
panel allows turning it back on...could be as simple as that?

my install is on an Acer Aspire One A0A110 and the wireless on/off switch is no longer functioning, but I can live with that

---

### Post by Lexfilez on 2010-09-18
> **macem29 said:**
> I'm using that same remix and for some unknown reason when I boot it, every now and
then networking is checked off, minor, but annoying...right clicking on the icon in top
panel allows turning it back on...could be as simple as that?

my install is on an Acer Aspire One A0A110 and the wireless on/off switch is no longer functioning, but I can live with that

I right clicked at the top and the wireless is enabled. So frustrating i tell ya. so yours works in live mode?

---

### Post by macem29 on 2010-09-18
yep, functioned in live mode off a thumb drive, would have had reservations about install otherwise...
installed and all is good, the little wifi on-off switch still does not do anything, but the LED that's part
of it does, flashes when stuff is going back and forth....different chipset in my box though: Atheros wifi

---

