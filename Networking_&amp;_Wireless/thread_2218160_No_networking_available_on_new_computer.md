---
title: "No networking available on new computer"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by Poserman on 2014-04-19
Hi,

I don't have any network on my new computer. I installed 13.10 from USB and dindn't get an IP on my internal network card. Just to make sure it's not in the card itself I went out and bought myself an intel gp1000 card. That didn't work either. I installed Windows 7 as a test and it was working perfectly. Network was up out of the box. 14.04 came out and I installed that. I now get an IP address on my intel card but I can't get any data over it. When I ping google of do nslookup i do get a reply. 

46% packet loss, time 12037ms

I can't reach my router, I can't reach other computers on my internal LAN, I can't browse the internet, I can't update my system. I can't do anything. It was working fine in Windows, when I plug the cable in another computer it works right away. It takes about 3 minutes to get an IP address and then I can't do anything with it except ping things and do nslookup. 

I can't figure out what's wrong with it. Can anyone please take a look at these documents? Maybe something is there that I've overlooked. 

[http://users.ninthfloor.org/~brutus/faillog.txt](http://users.ninthfloor.org/~brutus/faillog.txt)
[http://users.ninthfloor.org/~brutus/syslog.txt](http://users.ninthfloor.org/~brutus/syslog.txt)
[http://users.ninthfloor.org/~brutus/dmesg.txt](http://users.ninthfloor.org/~brutus/dmesg.txt)

I removed the router for a moment and plugged the computer straight in the cable modem. I got an external IP address but can't connect to the internet (and again, I can ping with a huge latency and packet loss).

---

### Post by kc1di on 2014-04-19
Hi Poserman and welcome to Ubuntu,

Can you go to a terminal and type these command and post the output here.

```
lspci
```

```
rfkill list all
```

```
modprobe --list 
```

---

### Post by Poserman on 2014-04-19
rfkill list all doesn't give me an output. modprobe --list gives me an unrecognized option error. 

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao XT [Radeon R9 270X]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:06.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)

---

### Post by kc1di on 2014-04-20
Sorry I was thinking of a wireless card. 

The both ethernet cards are recognized and should be active, but aren't working to connect to your router is that correct?

Do you have any fire walls on the router?

Here is[ a page]("https://help.ubuntu.com/10.04/serverguide/network-configuration.html") that may be of help in sorting out why your connection is being lost.

you may want to install the ethtool that's discribed there.

---

