---
title: "Wireless?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by meteoradew on 2011-02-28
So I finally got Ubuntu 10.10 working on my computer. The Internet works fine when I have my Ethernet cable plugged in but when I try to go on when it is unplugged it says I have no wireless connections and I don't know how to find them.

help?

---

### Post by zenwalker on 2011-02-28
First make sure your wireless card is supported by the Linux. Then second, configure it via network tool.

---

### Post by meteoradew on 2011-02-28
> **zenwalker said:**
> First make sure your wireless card is supported by the Linux. Then second, configure it via network tool.

How do i do this?

---

### Post by amjain on 2011-02-28
> **meteoradew said:**
> So I finally got Ubuntu 10.10 working on my computer. The Internet works fine when I have my Ethernet cable plugged in but when I try to go on when it is unplugged it says I have no wireless connections and I don't know how to find them.

help?


In the top panel, check if you wireless icon ( if you are not connected there will be red exclamation mark). Right Click and check if wireless is enable. If its enabled, left click and see what all wifi networks are available. If you can see some name there but not yours, probably your router is not broad casting the SSID.

---

### Post by johntaylor1887 on 2011-02-28
You may need wireless drivers. Check in system>administration>additional drivers.

---

### Post by meteoradew on 2011-02-28
> **amjain said:**
> In the top panel, check if you wireless icon ( if you are not connected there will be red exclamation mark). Right Click and check if wireless is enable. If its enabled, left click and see what all wifi networks are available. If you can see some name there but not yours, probably your router is not broad casting the SSID.

I have no idea how to tell if it is enabled or not. I do get the exclamation, when i right click it brings up a menu with:
Enable Networking (with a check next to it)
Enable Notifications (with a check next to it)
Connection information (greyed out and unclickable)
Edit connections...
About


and i have checked the additional drivers and nothing comes up.

---

### Post by zenwalker on 2011-02-28
Edit connections. 

First of all, lets see if your wireless is detected by the system.

do 

lspci or lsusb 
command on terminal as root and see the output if your wireless chip vendor name is mentioned.

---

### Post by meteoradew on 2011-02-28
> **zenwalker said:**
> Edit connections. 

First of all, lets see if your wireless is detected by the system.

do 

lspci or lsusb 
command on terminal as root and see the output if your wireless chip vendor name is mentioned.

aj@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by zenwalker on 2011-02-28
Seems like system support your realtek chip. Now lets check if your wirelesss network is enabled. 
Do this:

ifconfig -a 

as root.

---

### Post by zenwalker on 2011-02-28
This thread helps you more [http://ubuntuforums.org/showthread.php?t=1696156](http://ubuntuforums.org/showthread.php?t=1696156)

---

### Post by meteoradew on 2011-02-28
> **zenwalker said:**
> Seems like system support your realtek chip. Now lets check if your wirelesss network is enabled. 
Do this:

ifconfig -a 

as root.

eth0      Link encap:Ethernet  HWaddr 88:ae:1d:52:c0:ed  
          inet addr:172.20.12.35  Bcast:172.20.12.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:fe52:c0ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:191245032 (191.2 MB)  TX bytes:9934874 (9.9 MB)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22248 (22.2 KB)  TX bytes:22248 (22.2 KB)

---

### Post by zenwalker on 2011-02-28
Follow this thread plz [http://ubuntuforums.org/showthread.php?t=1696156](http://ubuntuforums.org/showthread.php?t=1696156)

---

### Post by meteoradew on 2011-02-28
> **zenwalker said:**
> Follow this thread plz [http://ubuntuforums.org/showthread.php?t=1696156](http://ubuntuforums.org/showthread.php?t=1696156)

Yeah, I'm not that good. haha i tried figuring it out and tried figuring out how to follow that, but i just started using Ubuntu and Linux today so I'm sort of an idiot.

---

### Post by zenwalker on 2011-02-28
Even i was an idiot when i started it out. But self efforts does paid me well. Just keep following links!

---

