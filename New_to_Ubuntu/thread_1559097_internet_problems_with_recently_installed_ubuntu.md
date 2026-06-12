---
title: "internet problems with recently installed ubuntu"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by srChubs on 2010-08-23
I just installed ubuntu 10.04 on a laptop that i have and there is no internet connection symbol in the top left corner. So I used the command nm-tool to see if i had one and the state of the connection says connected. the laptop is a toshiba satellite a505. please help

---

### Post by venturax on 2010-08-23
Have you tried to investigate if the Network Manager is running?

or you could try to re-install it..

```

$ sudo apt-get install network-manager-gnome
$ nm-applet

```

---

### Post by Peter09 on 2010-08-23
can you post the output of
 
```
ifconfig
```

---

### Post by srChubs on 2010-08-23
let me try

---

### Post by srChubs on 2010-08-23
i dont know if this has anything to do with it but when i sign in it says "a program is still running, power manger -not responding" and i tried the sudo apps and that didnt seem to do anything. and when i type ifconfig it pops up 3 sections of writing, i dont know where to find the output. when i first got on and realized i couldn't connect to the internet i tried to connect to a hidden one by using the name of my connection and the password. and it says it is connected and has connection speed.

---

### Post by srChubs on 2010-08-23
now in the top right it shows where the connections should be and when i click on it nothing is there, it says disconnected under wired and wireless

---

### Post by Peter09 on 2010-08-23
need to see ifconfig output (when your hard wired link is not connected)
 
and also
 
```
lshw -C network
```
 
have you updated your machine across the internet since it was installed?

---

### Post by srChubs on 2010-08-23
ifconfig...

eth0      Link encap:Ethernet  HWaddr 00:26:6c:42:c6:6d  
          inet6 addr: fe80::226:6cff:fe42:c66d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8850 (8.8 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:34 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:c6:0e:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:f80d8000-f80d8100 

lshw -C network...

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:42:c6:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:34 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 00:26:b6:c6:0e:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:10 ioport:3000(size=256) memory:d6400000-d6403fff

---

### Post by Peter09 on 2010-08-23
It appears that you should be connected. When you do not have a wired connection connected, what do you see when you left click on the network icon?

---

### Post by srChubs on 2010-08-23
it says-

wired network
     disconnected
wireless network
     disconnected
vpn connections   >
connect to hidden wireless network...
create new wireless network...

---

### Post by Peter09 on 2010-08-23
Some machines have a hardware switch to turn of the wireless adapter and some machines can turn of the wireless adapter using  a function key. Make sure that the wireless adapter is switched on.

Also have you updated your machine since installation - its best to do so as this can also bring updated drivers down.

---

### Post by Peter09 on 2010-08-25
try this command in a terminal
 
```
ifconfig wlan0 up
```

---

### Post by srChubs on 2010-08-26
that does not work either. hmmmmmm

---

### Post by Peter09 on 2010-08-26
There appears to be a resolution to this problem here
 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9128360](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9128360)
 
however the problem appears to be a bug in the Manufacturers driver and requires you to download and install a new version from the RealTek website, if you feel up to it try it - the thread gives you all the instructions.

---

### Post by srChubs on 2010-08-26
alright, i tried that one too, and it seems to not work. I tried to install jaunty jackalop 9.04 and it gives me a stupid error that i have gotten before called busybox something rather. I fixed it on a old computer i had but i dont remember how. this is a mess

---

### Post by srChubs on 2010-08-26
mmk i installed windows 7 ultimate then duel booted with ubuntu 10.04 and i had to reinstall the drivers on the toshiba website for the wifi drivers. but for ubuntu it still doesn't work. You have helped me enough, i dont want to bother you anymore about it, but if i find a solution i will definitely let you know. thanks for your help

---

