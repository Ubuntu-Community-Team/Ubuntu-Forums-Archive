---
title: "Unable to get wireless to work"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by akabugeyes on 2008-02-26
Hi all, I recently installed Ubuntu 7.10. I really like Ubuntu, but after many hours trying to get it to work, I can't seem to get it to work.

I installed ndiswrapper because I think I need to use it.

I have installed some drivers, including those that I thought would be the ones I needed, but it didn't seem to help.

Here is some info I can provide, I am real new to this and believe me I did many searches before posting this (I usually refrain from asking for help unless I just can't seem to solve it myself):

```
jack@jack-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d4:18:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.3 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```When I run ndiswrapper -l I have some drivers which I thought might have worked that I installed through ndiswrapper:

```
netmw245 : driver installed
wg311v3 : driver installed
yk51x86 : invalid driver!
yk60x86 : invalid driver!

```But no "present" message underneath any of them.

The yk60x86 driver in fact is the one that is associated with what appears to be for my "88E8038" controller. But it comes back as invalid, so I suppose it is not.

If anyone can offer any advice of what I can try I would really appreciate it! I am fairly inexperienced Linux user but I hope to be able to use Ubuntu as my primary OS on my laptop.

Thanks,

Jack

---

### Post by Sam Lars on 2008-02-26
How about the output of lspci?  It doesn't seem that lshw saw much in the way of wireless.
Are you sure that's the right one?  Did you have the whole folder with the .sys files, too, when you added it to ndiswrapper?
You might also try ndisgtk for a graphical taste of ndiswrapper.

---

### Post by akabugeyes on 2008-02-26
Thank you for your response.

I installed the graphical interface, thanks, it seems to make the general process of installing new drivers a little easier plus I now see the message "Hardware present: No" message next to the drivers that are installed successfully but do not help me in getting my wireless working.

As for way of lspci:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```As for having the .sys files in the same directory, yes I did. In fact I think one time when I only had a .inf file it let me know that it was missing the .sys file and I then added the .sys file accordingly.

---

### Post by Sam Lars on 2008-02-26
You may be in luck ;)
Try getting your drivers from [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)").
I found a thread [here]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=417084") (where I found that link) where someone appears to have gotten the same device working.

---

