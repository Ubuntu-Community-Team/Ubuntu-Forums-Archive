---
title: "Wifi will not work"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by taloravia on 2014-09-30
Hello,
I am running Ubuntu 14.04.1 LTS 64 bit off of my Microsoft surface pro 2. However, I cannot connect to any wifi networks (no networks are even showing up). I have the same issue when running live via USB (only way that I can install ubuntu on my tablet). I opened the terminal and ran iwconfig and I get lo no wireless extensions. I am not really sure where to go from here, and would appreciate any help.

---

### Post by kc1di on 2014-09-30
Hi taloravia, and welcome to Ubuntu,

could you go to a terminal and type the following command and list the output here.
```
lspci
```

Will try to help.

---

### Post by taloravia on 2014-09-30
Here is what the terminal spits out:  [http://pastebin.com/59VnxR2T](http://pastebin.com/59VnxR2T)

---

### Post by Bucky Ball on 2014-09-30
You have installed Ubuntu inside Windows? As in a Wubi install with Ubuntu not on its own partition? Wubi is no longer supported by Canonical or these forums. Please install Ubuntu to its own partition and either dual-boot with Windows or run Ubuntu solo (or as a virtual machine, naturally). Thanks.

Please see [HERE.]("http://ubuntuforums.org/showthread.php?t=2229766&highlight=wubi+staff+recommendations")

---

### Post by chuckrp on 2014-09-30
I am having the same issues. Running Linux Mint 16 and on Saturday wifi disappeared. Tried updating with no luck. Moved card to new slot and finally updated to Mint 17. Still nothing. I have completely updated system. There is no wireless networks showing, no even the one I have. Can some one offer a suggestion?

---

### Post by taloravia on 2014-10-01
I did have linux dual booted on this system, and I am in the process of repairing that. I also have it dual booted on my desktop and it is giving me a similar issue with my wifi. When I can I will post a log with the terminal output.

---

### Post by kc1di on 2014-10-01
Please do post the out put for a hardware install system Not WUBI.  --
The post you gave shows no wifi card recognized. 

As to Cuckrp - same thing post the output of ```
lspci
```
But you should start a separate thread.  As your problem will be different than this one.
Have you tried the Mint extra driver tool?

---

### Post by Bucky Ball on 2014-10-01
> **kc1di said:**
> 

As to Cuckrp ... you should start a separate thread.  As your problem will be different than this one.


              ^^^
@Cuckrp: This.

Please start a new thread in ***Other Operating Systems and Projects***. Mint is not supported in the Ubuntu support sub-forums here. While you should feel free to post about your issues in that sub-forum, Mint has a fairly active community so you may try posting there as well to improve your chances. 

Best not to hijack threads. Your issue has little to do wth the OP's. Good luck. ;)

---

### Post by hakuna_matata on 2014-10-01
> **taloravia said:**
> Here is what the terminal spits out:  [http://pastebin.com/59VnxR2T](http://pastebin.com/59VnxR2T)
Please post the output of
```
lsusb
```
too.

IMHO Wubi is no reason for an incomplete output of lspci. Additionally, I'm not sure that you are using Wubi.....

---

### Post by Knightwise on 2015-02-14
I'm kinda having the same issues , here is my lsusb output
(surface pro 1 , ubuntu 14.04)

Bus 002 Device 005: ID 045e:0794 Microsoft Corp. 
Bus 002 Device 004: ID 03eb:8209 Atmel Corp. 
Bus 002 Device 003: ID 045e:07a9 Microsoft Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:0795 Microsoft Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1286:2044 Marvell Semiconductor, Inc. 
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

