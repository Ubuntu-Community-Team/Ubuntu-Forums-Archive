---
title: "slow wireless internet connection"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by germain99 on 2009-01-09
Hello everyone, this is my first post, i'm a newbie!
I have installed ubuntu intrepid, and i love it. First time for me using Linux and i have learned a great deal in the past 2 weeks(terminal, sudo etc.). One thing though, my internet speed is about half of vista. I have dual boot vista x64 and intrepid 8.10 and 10 MB/s vista and max. 5 MB/s intrepid if i'm lucky. I would love if this could get resolved thus being only issue so far. I have looked everywhere and this is my last resort. I have a Lite-On USB Wireless card and i think the following paste is usefull in determining my problem : this is what i tried so far, hope it helps

germain99@ubuntu:~$ sudo ispci
sudo: ispci: command not found
germain99@ubuntu:~$ sudo ndiswrapper
sudo: ndiswrapper: command not found
germain99@ubuntu:~$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
germain99@ubuntu:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.2kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Fetched 20.2kB in 4s (4537B/s)                        
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 126171 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...
germain99@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0            
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:bd:6b:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.103 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 0a:e0:49:90:d3:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
germain99@ubuntu:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0d.0 VGA compatible controller [0300]: nVidia Corporation GeForce 6150SE nForce 430 [10de:03d0] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 70)
01:0a.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]
germain99@ubuntu:~$ 

Thanx in advance, sorry for average English, i'm French Canadian.

---

### Post by Dedoimedo on 2009-01-09
Is the MTU the same for both? You may need to optimize the MTU for Ubuntu so that your machine / router / ISP gives you best throghput without fragmenting packets.

Check this one out please first. You'll see the MTU when you type ifconfig in the command line, for each individual network adapter separately.

Dedoimedo

---

### Post by germain99 on 2009-01-09
> **Dedoimedo said:**
> Is the MTU the same for both? You may need to optimize the MTU for Ubuntu so that your machine / router / ISP gives you best throghput without fragmenting packets.

Check this one out please first. You'll see the MTU when you type ifconfig in the command line, for each individual network adapter separately.

Dedoimedo
Thank you so much, i put it at 1500 and it's great 10 MB/s + i cheched out your site and it is also great, i bokkmarked it and will consult it frequently.

Thanx again, it is so exciting to make changes that actually work!

germain99

---

### Post by Dedoimedo on 2009-01-10
Good to hear! Excellent.
Cheers,
Dedoimedo

---

