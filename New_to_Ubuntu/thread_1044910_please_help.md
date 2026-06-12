---
title: "please help"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by marcmarcmarc on 2009-01-19
hello everyone, i have just joined this and really need help with ubuntu or any linux distro (and with spelling but thats another thing so sorry for spelling mistakes). Any way i am trying to get a linux live distro to work on my laptop and get wifi working. i am using a hp g6000 laptop that comes with vista installed but really want a linux live distro to get me online with wifi. i am so very new to this os, like two weeks old to linux, and i love it. i have downloaded so many live cds of every os i can think of and all  the ones that work i love so want to use linux more. but my problem is none of them allow me to get online with wifi. i know its a problem with my computer because i gave a copy of my live cd ubuntu to a friend and his sony viao got straight online with wifi..... please please help i am a real newby. i have got linux live to boot from cds and my usb but i can not for the life of me get my laptop to get on wifi. ethernet is fine but i need wifi....thankyou in advance and sorry for waffeling on but a really simple explanation is what i am after (if thats possible with this problem) thankyou thankyou thankyou all

---

### Post by adult swim on 2009-01-19
Go to a terminal applications>accessories>terminal and enter in ```
lspci
``` copy and paste that here. If you don't have an Ethernet connection maybe save the output to a USB drive and then use a computer with Internet to paste it.

---

### Post by networm1230 on 2009-01-19
> **marcmarcmarc said:**
> hello everyone, i have just joined this and really need help with ubuntu or any linux distro (and with spelling but thats another thing so sorry for spelling mistakes). Any way i am trying to get a linux live distro to work on my laptop and get wifi working. i am using a hp g6000 laptop that comes with vista installed but really want a linux live distro to get me online with wifi. i am so very new to this os, like two weeks old to linux, and i love it. i have downloaded so many live cds of every os i can think of and all  the ones that work i love so want to use linux more. but my problem is none of them allow me to get online with wifi. i know its a problem with my computer because i gave a copy of my live cd ubuntu to a friend and his sony viao got straight online with wifi..... please please help i am a real newby. i have got linux live to boot from cds and my usb but i can not for the life of me get my laptop to get on wifi. ethernet is fine but i need wifi....thankyou in advance and sorry for waffeling on but a really simple explanation is what i am after (if thats possible with this problem) thankyou thankyou thankyou all

hello friend and will come to Linux

I do not have wifi and never used it so I cant help you directly. I have no experience with wireless computing. but hear are some sites that mite help you out.

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
[http://thedailyubuntu.blogspot.com/2007/09/wifi-radar-ubuntu-wireless-application.html](http://thedailyubuntu.blogspot.com/2007/09/wifi-radar-ubuntu-wireless-application.html)
[http://www.youtube.com/watch?v=465rGa_uXfY](http://www.youtube.com/watch?v=465rGa_uXfY)

---

### Post by networm1230 on 2009-01-19
> **adult swim said:**
> Go to a terminal applications>accessories>terminal and enter in ```
lspci
``` copy and paste that here. If you don't have an Ethernet connection maybe save the output to a USB drive and then use a computer with Internet to paste it.

cool! I like your avatar nice skull

---

### Post by marcmarcmarc on 2009-01-20
hi thanks for getting back to me this is the results from typing in terminal

ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
ubuntu@ubuntu:~$

---

### Post by anewguy on 2009-01-20
Your wireless, the Atheros, will need a special driver, and I don't know of a way (maybe someone else does) of installing that when you are running off the LiveCD.  It can be done if you are dual-booting, etc..  There are a lot of posts in the forum about getting Atheros chipsets to work - you may want to use the search function and check them.

Dave :)

---

### Post by marcmarcmarc on 2009-01-20
i see **** its never straight foward with me. i will try and search for advice. do you or anyone else know of a distro that will work with this atheros chipset on a live cd ???

---

### Post by The Cog on 2009-01-20
Try Linux Mint. I haven't tried it myself, but I have read that they include non-free drivers like that in their distro - something that Ubuntu chooses not to do.

---

### Post by tjwoosta on 2009-01-20
in order to get a driver on the live cd, thats not already included, you will probably need to remaster your own livecd

(or just find a livecd that already has the drivers)

---

### Post by marcmarcmarc on 2009-01-20
i am running my live cd from a usb so does this mean that when i get the driver to work it will save to my usb and work straight away next time

---

### Post by marcmarcmarc on 2009-01-20
also i have tried mint but will try again

---

