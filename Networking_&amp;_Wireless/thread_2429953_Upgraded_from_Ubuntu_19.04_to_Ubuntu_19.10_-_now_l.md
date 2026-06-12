---
title: "Upgraded from Ubuntu 19.04 to Ubuntu 19.10 - now laptop freezes after couple minutes"
date: 2019-10-25
forum: Networking &amp; Wireless
---

### Post by Milleuros on 2019-10-25
Hello,

I recently got a new laptop which sports some very recent hardware, a Lenovo Thinkpad X1 Extreme Gen2. I installed Ubuntu 19.04 on it (dual-boot with the preinstalled Windows 10), motivated by needing newest support.

Got a whole range of issues on it. Wifi card not detected, Nvidia graphics card not detected, microphone, couldn't even connect a beamer on it. I suspected some driver issues and after Googleing around I figured out the support would be added with newest Linux kernel / Ubuntu release.

Today I upgraded to Ubuntu 19.10. The system now detects the Wifi card (yay!) but it freezes completely after a couple minutes. Ranging from 2-3 minutes after boot to 20mn. The machine doesn't respond and I need to hard reboot. 

I could try a fresh 19.10 install but I have a priori no guarantee that it would work.


What do you think is going on? How would I troubleshoot this?


Thanks,


**EDIT 2019-10-30** : I have narrowed down the issue to incompatibility (seemingly) with the network adapter Intel AX200. In short, my computer freezes completely unless I quickly turn on "airplane mode" at login. See the replies for more infos. It seems to be common, found e.g. this: [URL="https://bugzilla.redhat.com/show_bug.cgi?id=1738361"]https://bugzilla.redhat.com/show_bug.cgi?id=1738361

[/URL]**EDIT 2019-10-30 #2 :** Here is the output of the wireless info script: [https://paste.ubuntu.com/p/jY9xP3dTVx/](https://paste.ubuntu.com/p/jY9xP3dTVx/)

---

### Post by mörgæs on 2019-10-25
> **Milleuros said:**
> 
I could try a fresh 19.10 install but I have a priori no guarantee that it would work.


Though there is no guarantee I think it's worth a try.

---

### Post by Milleuros on 2019-10-28
Hi again,

I didn't reinstall 19.10 yet but I narrowed down the issue. I've seen that my computer does not freezes if I immediately disable the wifi (airplane mode) at boot. So this sounds like an issue with the wifi adapter and/or drivers.

The output of lspci :

```
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:1b.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #17 (rev f0)
00:1b.4 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #21 (rev f0)
00:1c.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #1 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #15 (rev f0)
00:1e.0 Communication controller: Intel Corporation Device a328 (rev 10)
00:1f.0 ISA bridge: Intel Corporation Device a30e (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (7) I219-V (rev 10)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1f91 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 10fa (rev a1)
02:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2018/PC SN720 NVMe SSD
04:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] (rev 06)
05:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] (rev 06)
05:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] (rev 06)
05:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] (rev 06)
05:04.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] (rev 06)
06:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 4C 2018] (rev 06)
2c:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 4C 2018] (rev 06)
52:00.0 Network controller: Intel Corporation Device 2723 (rev 1a)
53:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)

```

I see "Intel corporation Device 2723" near the bottom, which sounds awfully like: "we don't know what this is". 

When I was on 19.04 I tried to install IWLWIFI backport drivers following these instructions: [https://askubuntu.com/a/1156246](https://askubuntu.com/a/1156246) . 

I will be trying to use a fresh Ubuntu 19.10 from a bootable drive, to check whether reinstalling the system would work or not. If it doesn't, what do you suggest?

---

### Post by HermanAB on 2019-10-28
In general, if one distribution doesn't work - try another one.  There are many: Fedora, Arch, Debian, Gentoo, PCLinuxOS, OpenBSD... the list goes on and on.  

Every distro lab doesn't have every laptop in the world, but one of them may have yours.  Therefore one of the other versions of UNIX may work, but you won't know till you try it...

---

### Post by Milleuros on 2019-10-29
Hi,

The problem with this suggestion is that another distribution  may or may not work at all. I narrowed down the issue to the Wifi  adapter, but another distrib might have issues with something else (e.g.  the GPU being a recent GTX1650). Due to time constraints, and due to me  being used to high-level Ubuntu (instead of low-level Arch for  example), I really do not want to spend weeks trying each distrib one by  one until one works (if there is one!).  I also see people having  issues with this Adapter on the Redhat bugzilla, on CentOS systems and  on Juno among others, so this is widespread.

I ran a fresh 19.10  from an USB drive and the same issue happened. I also managed to find  the exact model of my Wifi adapter: Intel Wi-Fi 6 AX200 160MHz
There  are Linux drivers over there:  [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)  

I downloaded the .tar file, extracted it and moved the file  *iwlwifi-cc-a0-46.ucode* to */lib/firmware*. However I'm not  exactly sure how to tell my system to use this new driver.  This is the  view of the "Additional drivers" from the software manager: 

[https://i.imgur.com/aK4DoDV.png](https://i.imgur.com/aK4DoDV.png)

The  iwlwifi option is grey and I cannot pick it. Choosing the only  available option "Continue using a manually installed driver" doesn't  seem to do anything, because as soon as I close and relaunch the  software manager it comes back to the same view.

This is the output of **modinfo iwlwifi** : [https://paste.ubuntu.com/p/gYNDyPtfPJ/](https://paste.ubuntu.com/p/gYNDyPtfPJ/)

I don't see my custom driver. I also check **dmsg** :

```
david@David-Thinkpad:~/Desktop/iwlwifi-cc-46.3cfab8da.0$ dmesg | grep iwlwifi
[    3.247267] iwlwifi 0000:52:00.0: enabling device (0000 -> 0002)
[    3.283435] iwlwifi 0000:52:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    3.283438] iwlwifi 0000:52:00.0: Found debug destination: EXTERNAL_DRAM
[    3.283440] iwlwifi 0000:52:00.0: Found debug configuration: 0
[    3.283733] iwlwifi 0000:52:00.0: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[    3.508337] iwlwifi 0000:52:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    3.520709] iwlwifi 0000:52:00.0: Applying debug destination EXTERNAL_DRAM
[    3.521009] iwlwifi 0000:52:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    3.701186] iwlwifi 0000:52:00.0: base HW address: dc:fb:48:7f:bc:a0
[    3.720831] iwlwifi 0000:52:00.0 wlp82s0: renamed from wlan0
[    5.964726] iwlwifi 0000:52:00.0: Applying debug destination EXTERNAL_DRAM
[    6.132654] iwlwifi 0000:52:00.0: FW already configured (0) - re-configuring
[    6.139175] iwlwifi 0000:52:00.0: BIOS contains WGDS but no WRDS

```

It  looks like the card is detected but the firmware loaded is version 48,  whereas from the name of the file I downloaded I'm expecting version 46.  

How can I tell my computer to use the correct firmware ?

If  there is no way, can I **black list** my Wifi adapter? Tell my  computer to forget about it, not use it at all, and instead I use some  USB wifi adapter that I have lying around (and which worked on Ubuntu  19.04).

---

### Post by mörgæs on 2019-10-29
If you push the report button you can send a message to the moderators asking them to move the thread to the networking forum.

---

### Post by Irihapeti on 2019-10-30
*Thread moved to **Networking & Wireless**.*

---

### Post by Milleuros on 2019-11-01
So I downgraded to Ubuntu 18.04 LTS. I will use an USB Wifi adapter instead of battling the built-in Wifi and drivers. 

It seems that on 19.10, the card is detected but something goes wrong and it leads to constant freezes. On 18.04, the card isn't even detected which also means the system is stable.

---

### Post by hk42 on 2019-11-01
> **Milleuros said:**
> 

If  there is no way, can I **black list** my Wifi adapter? Tell my  computer to forget about it, not use it at all, and instead I use some  USB wifi adapter that I have lying around (and which worked on Ubuntu  19.04).

Probably the driver is loaded as a module.
Those are located in /usr/lib/modules folder and renaming the bad one as *.bad could be a (dirty but useful) solution

---

### Post by praseodym on 2019-11-01
What about the backport driver in 18.04 which is LTS?

---

