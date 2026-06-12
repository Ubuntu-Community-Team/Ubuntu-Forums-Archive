---
title: "Can't get online with 7.10, but 7.04 and Debian 4.0 works."
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by rvb on 2007-11-01
I bought a new computer with a Gigabyte GA-G33M-S2H motherboard which uses an RTL 8110SC chip. I could connect to internet with Ubuntu 7.04 and Debian 4.0 but I'm having problems with 7.10. I've made three different installation cd's, first one (alternate install, amd64)  gave me an error during installation about the kernel, so I assumed there was something wrong with the cd, the second one (alternate install, i386) gave me an error about DHCP during installation and I couldn't get it to connect to internet. When I tried to reinstall with that same disc I got another error about something so I assumed there was something wrong with that one too. I made a new disc (regular install, i386) on another computer with another cd burner and can't get any connection to internet with that one either.

I found this thread: 
Realtek 8110SC Onboard LAN
[http://forums.fedoraforum.org/showthread.php?t=141938](http://forums.fedoraforum.org/showthread.php?t=141938)

But the onboard lan seemed to work just fine under 7.04 and Debian 4.0 so why won't it work in 7.10? I'd use Debian 4.0 but it doesn't have drivers for Intel G33 by default and neither has 7.04.

--edit--

According to the Debian installation the network interface is:
eth1: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Eternet

---

### Post by noob12 on 2007-11-04
Could you post the output of these commands?  (You may need to use a usb jump drive or shared partition to get the text off to post.)

```

lspci -nn

sudo lshw -C network

sudo ethtool eth0

```

---

### Post by CD_7 on 2008-04-21
I have run into the same problem with 7.10. I am using a Gigabyte GA-MA69GM-S2H MB and 7.04 & 7.10 install without any issues (I am suing 7.10 now). However, the ATI Graphics Card ("ATI Card Proprietary driver missing") and the network do not work. The graphics card isn't problem at the moment as VGA mode appear to be okay (hope the S-Video & HDMI work!) but network is completely dead!  Here are the output for the commands on noob12's email.

"lspci -nn" returns:

00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon X1200 Series [1002:791e]
01:05.2 Audio device [0403]: ATI Technologies Inc Radeon X1200 Series Audio Controller [1002:7919]
02:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7146 [1131:7146] (rev 01)



"sudo lshw -C network"

This command displays.....

PCI (System) 
SCSI

And then, hangs. If I run it in the background, it returns....

Bash 1: Command not found.


"sudo ethtool eth0" retursn...

Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

Thanks for any help.

---

### Post by CD_7 on 2008-04-21
Since my earlier posting, I have loaded v 8.04 LTS RC. This version has not detected the NW controller (RTL 8110 SC) either. Incidentally, XP detects it and works with drivers supplied with the MB. 

I have downloaded the driver from the RTL site but having problems with 'make'. Need to debug this but won't be able to do that for a few days. I am a little puzzled as to why the standard build has not detected the controller. Any comments would be of help.

---

### Post by mrbuntuman on 2008-04-21
try that,its a long shot but here how i finally got online. (using a diff network adapter but this may just work for you)

pico /etc/network/interface

make it look something like this:

auto <ur interface>
iface <ur interface> inet dhcp

got that from 
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

hope this help a little, 
cheers

---

### Post by CD_7 on 2008-04-22
mrbuntuman, thanks for the suggestion. Tried it and still no joy! I have reported it as a bug.

---

### Post by CD_7 on 2008-04-25
The latest version of 8.04 LTS has solved this problem. The network controller now works.

---

