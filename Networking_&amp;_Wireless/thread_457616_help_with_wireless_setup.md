---
title: "help with wireless setup"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by super hawk on 2007-05-28
Hi
I'm a noob to Linux and Ubuntu who installed Ubuntu through Wubi (latest version) less than an hour ago. My wireless network was detected and I entered in all the settings, but I still can't connect to the internet. Can anyone help me out?
Thanks

---

### Post by sonicj on 2007-05-28
whats wubi?

---

### Post by super hawk on 2007-05-29
Wubi is an unofficial Ubuntu installer that lets you install Ubuntu to a .DISK file so you can install it without messing with your partitions.

Wubi Website:
[www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html")

---

### Post by jglen490 on 2007-05-29
You might want to check into the 3rd Party support pages here at Ubuntu for Wubi-specific help.  This is a little different from the "standard" Ubuntu install.

---

### Post by handydan918 on 2007-05-30
What kind of wireless card/chip do you have? 
Try typing "lspci" in a terminal and post the output.

---

### Post by super hawk on 2007-05-30
When I typed that into the terminal, I got this:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
04:07.0 Communication controller: Conexant HSF 56k Data/Fax Modem
*****@ubuntu:~$

---

### Post by handydan918 on 2007-06-02
Ahh, yes. The famous broadcom problem.

<Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)>

If it isn't working, you may need to use ndiswrapper. 
see [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

You have my sympathy. I got stuck with a broadcom 4318 chip. But I was able to get it working with ndiswrapper.

If the link above doesn't get it done, have a look [here]("http://www.mepis.org/docs/en/index.php/Using_Ndiswrapper"), too.
HTH!

---

### Post by kevdog on 2007-06-02
I also have the same broadcom rev 03 chipset -- used the bcm43xx cutter approach to install drivers.  It seemed to work for me (instead of ndiswrapper!)

---

### Post by handydan918 on 2007-06-02
> **kevdog said:**
> I also have the same broadcom rev 03 chipset -- used the bcm43xx cutter approach to install drivers.  It seemed to work for me (instead of ndiswrapper!)
Well, by all means, tell the man HOW!
:D

---

### Post by buickpwr6 on 2007-06-03
Please tell same problem here..

---

### Post by SiliconAlleyCat on 2007-06-03
Also a n00b - can't get Ubuntu to recognize D-Link's wireless-N adapters.  Naturally I had to update my wireless network to "N" shortly before trying Ubuntu! Would "Ndiswrapper" be my answer?

---

### Post by super hawk on 2007-06-04
When I tried installing the driver, it worked, but it told me that the driver was invalid. I tried the driver off of the  ndiswrapper website and off the CD that came with my card. Can anyone find me a valid driver of find a way to make my driver valid? 

Thanks

---

### Post by kevdog on 2007-06-04
Here is the link for that I used:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx)

There is only one downside to the whole process -- it seems that maximum bitrate with the bcm43xx drivers is 11Mb/s -- basically equivalent to 802.11b.

If you are using a 802.11g card (which you are), the only way to reach bitrate of 54 Mb/s is to install the network drivers via ndiswrapper.

I had the bcm43xx drivers working for months, and then just this weekend reinstalled with ndiswrapper.  I really havent noticed any difference.  The ndiswraper approach is much, much more difficult, however once I was comfortable with ubuntu and actually compiling programs for the installation it wasnt too bad.  Im glad however that I had a few months with ubuntu under my belt before tackling the problem however.

---

### Post by super hawk on 2007-06-05
Thanks for the link. I'm going to try it out now.

---

### Post by super hawk on 2007-06-06
I ran the program, and I got this message:
```

Removing ndiswrapper...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
 ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 225kB disk space will be freed.
Do you want to continue [Y/n]? y



```
Can anyone tell me what to do now?

Edit: I probably should of included thsi earlier, but I waited over 10 minutes and nothing happened

---

