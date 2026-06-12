---
title: "No wifi on MSI x320 10.40"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by gaublius on 2011-08-09
Hi there,

I am completely new to Linux and need some help.
I was able to find out that I am not the only one experiencing problem of having no wifi on this crappy MSI x320 with Ubuntu 10.40 , but I can't seem to find any solution.

Anyone?

Again, I am totally new to Linux. 

THANKS!

---

### Post by JC Cheloven on 2011-08-10
To find out the model of your wifi card, please open a terminal and type the command ```
lspci
```
Then select with the mouse the output, do edit-copy from the menu, and paste it back here so thet we can see. 

PLease do the same with the command ```
ifconfig
```

Thanks.

---

### Post by gaublius on 2011-08-11
THanks for reply.

So here it is:

<....>


01:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe



tadas@tadas-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:6a:ef:4e  
          inet addr:84.32.68.210  Bcast:84.32.69.255  Mask:255.255.254.0
          inet6 addr: fe80::224:21ff:fe6a:ef4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78209423 (78.2 MB)  TX bytes:4607590 (4.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:639240 (639.2 KB)  TX bytes:639240 (639.2 KB)

THANKS!

---

### Post by JC Cheloven on 2011-08-11
OK, you have a RaLink RT3090 PCI wireless card. 
There are good news 
- as the manufacturer offers a [driver for linux]("http://www.ralinktech.com/support.php?s=2") (third from bottom at that page), 
- as there is a ppa (I think you shoud use version 1:2.3.1.7 because you're using ubuntu 10.04 right?)
- as there are solved threads [here]("http://ubuntuforums.org/showthread.php?t=1753477"), and [here]("http://ubuntuforums.org/showthread.php?t=1669283"). THis means that other people got theirs working.

You're new to gnu-linux, and probably you'll need a bit more of guidance, but please, try first by yourself (you'll get more satisfaction ;) ). It seems not too difficult. For example [here]("http://planetared.com/2011/02/ralink-rt3090-en-ubuntu-10-10/") is explained what to do (2 step process, easy!). If you don't find you way, please come back to ask.

---

