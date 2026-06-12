---
title: "BT Voyager 205 help needed"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by darrenb1976 on 2008-09-15
Hi. I'm hoping for some help. I'm an absolute beginner with regard to Ubuntu and just installed it today (hardy heron). I like the look of it so far, but have been unable to get connected to the internet... to be honest, I just don't know where to start.

I've got a BT Voyager 205 router and its connected to my Acer Aspire 3002LC laptop by ethernet. I understand that I'll have to set it up to work with Ubuntu, but I don't know how and I'm getting frustrated. I've looked around online for help, but don't seem to be getting anywhere :(

Please, make any advice you can give as clear and as simple as possible. Imagine you're helping a 4 year old ;)

thanks muchly, darren.

---

### Post by DFlame on 2008-09-15
Hey there, I used to have a 205 router myself. As far as I am aware, it's plug and play if you're using it with a BT broadband service. Lets get some more info first though. Plug everything in (ethernet between router & laptop, as well as connecting the line and microfilter to the router). Switch everything on and provide us with the output of the following commands in Terminal:

lspci
ifconfig

Also, what lights are showing on the router?

DFlame

---

### Post by DFlame on 2008-09-15
<doublepost removed>

---

### Post by darrenb1976 on 2008-09-15
Hi there!

OK, here's what came up:

ubuntu@darren-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter



ubuntu@darren-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:b8:76:e3  
          inet6 addr: fe80::2c0:9fff:feb8:76e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9600 (9.3 KB)  TX bytes:398 (398.0 B)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130679 (127.6 KB)  TX bytes:130679 (127.6 KB)

ubuntu@darren-laptop:~$ 


On the router the power, dsl and ethernet lights are on.

PS: Although I'm connected via a BT landline, I'm not with BT, I'm with Titan ADSL (and I've never tried the router with this service provider before)... does that make a difference?

---

### Post by DFlame on 2008-09-15
Can you access the router setup page in firefox? I believe it is [http://192.168.1.1](http://192.168.1.1) from the computer that is connected to the router.

DFlame

---

### Post by darrenb1976 on 2008-09-15
I couldn't access the router setup, all i got was a "Failed to Connect" page, it was pretty much the same in Opera.

I have two other router/modems, a Sagem F@st 800 E4 and a Thomson Speedtouch 330.

---

### Post by darrenb1976 on 2008-09-15
ok... i'm not exactly sure how, but I'm online now!

i tried the router setup page again and up it came, heh.

thanks muchly!

---

### Post by DFlame on 2008-09-16
No problem, I guess :P. If there's any more trouble just drop by again.

DFlame

---

