---
title: "Cannot get LAN connection working on Thinkpad r31"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by LutefiskJoe on 2008-08-15
Hi Folks...

I'll preface this by saying that I am especially clueless when it comes to networking issues, so I'm hoping that someone more clued in might be able to identify my problems connecting straight away.

I'm running 8.0.4.1 on a Thinkpad R31, using a wired LAN connection to a Siemens Gigaset SE587 wlan dsl router

Here is the output of 

**lshw -C network** 

```

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 42
       serial: 00:00:e2:87:08:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.3 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

```


I've also attached networktools.txt, which is all the details i can get from System>Administration>Network Tools. I'd paste it in here directly, but all my beatiful columns become somewhat of a dog's dinner in here.

It may be worth mentioning that I have a dual boot on the machine with Puppy Linux. Puppy connects automatically via DHCP with no problems, and I have Ubuntu set to connect automatically via DHCP as well.

I'm stumped at the moment. Any assistance/ suggestions would be greatly appreciated!! I'll be certain to post my solution, should it be found, so you'll probably be helping out a great many more people!

Many Thanks!!

---

### Post by LutefiskJoe on 2008-08-15
OK... Some more information....I'm not sure if this has anything to do with the connection problems, but it very well may...

In order to fix the crazy mouse problem detailed here, which I experienced in Puppy Linux, I added i8042.nomux=1 to /boot/grub/menu.lst...it fixed the mouse problem, but I could no longer get online!! 

I know that the issue with the crazy mouse behaviour was fixed in Hardy and that that boot option isn't necessary... Does anyone know of a means of "unfixing" this in Ubuntu, so I might isolate the cause of my lack of connectivity? 

I tried i8042.nomux=0,
but this does nothing for my internet connection, and doesn't roll the mouse behaviour back either...I'm not familiar with this boot option and am really just taking stabs in the dark at this point.

Can anyone enlighten me? Please Please Please!

---

