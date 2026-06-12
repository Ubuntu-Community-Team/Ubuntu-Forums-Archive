---
title: "Weird Problems with Wifi After Install"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by codylambrecht on 2009-11-17
Hi,
I'm new to linux, obviously since I'm posting here. heh.
I am a member on a few other forums and have had done some modding with Android, but that's the only real linux knowledge I have other than what I have been able to find online.  I will try and make this as easy and less painstaking for everyone involved, if there's any more information that you need to know, just let me know and I'll get it asap!


[SIZE=3]**The problem:**[/SIZE][INDENT]When I ran the Ubuntu 9.10 LiveCD I downloaded and burnt from Ubuntu.com.
The wireless worked off of the LiveCD version, but only after a restricted driver prompt showed up in the notifications area and I clicked on it to install the necessary drivers.
There were two different wireless drivers located there, and I had chosen the second one that was compatible with way more cards than the first one.
After installing that it worked fine with the occasional timeouts that are known to happen with my school's wifi.
[/INDENT][SIZE=3]**Personal troubleshooting done:**[/SIZE][INDENT]I've searched the LiveCD for the driver files, used wlan for the search, and found the following file names:
linux-wlan-ng-doc_0.2.9+dfsg-2ubuntu2_all.deb
linux-wlan-ng_0.2.9+dfsg-2ubuntu2_i386.deb
I tried installing each one of those separately (and I uninstalled the previous one before trying the second one).
That didn't work.

I was trying to find a solution online using good ol' google, and most were saying to do one of the following two things:
Use WICD as supposedly that's helping people with the driver card that I have.
Or trying the Windows Driver program, ndisgtk.

When I tried to do the WICD solution, it said that there was already a wireless manager or something along those lines and that it could not be installed.

Then I dried the second solution (ndisgtk), installed the necessary files for it, and the instructions said to get the .inf file from the windows driver and load it into that program.
When I loaded that .inf file, it said that it was an invalid driver.
So I deleted the driver and then uninstalled the ndisgtk program.
[/INDENT][SIZE=3]**Addition information:**[/SIZE]
One of the threads I read said to go to the console and type "lspci" for the necessary info to help the individual, I did that and got the following:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```[INDENT]I'm also running windows7 in a dual boot, so I'm not sure if that could be affecting anything. I've been trying to resolve this on my own for the past few hours with no luck.  Any insight into how to solve this problem would be greatly appreciated as once I have the internet then it won't be as hard to troubleshoot myself since I won't have to reboot everytime to continue looking for the next possible solution.
[/INDENT]I appreciate any help you can offer as linux is really the last frontier for me in computers.  Hopefully someday soon I'll know enough to be on here helping others too!

---

### Post by teward on 2009-11-17
It seems that you have a Broadcom card.  Ubuntu and Broadcom cards seem to have compatibility issues.  I don't know how to fix them, though.  Others might.

---

### Post by Dude-PWB- on 2009-11-17
Try this link and look for your wireless adapter there.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by codylambrecht on 2009-11-17
Yeah, I read a couple forums that had said that about the Broadcom card *after* I had installed ubuntu. 
Figures.
But most said if the WICD program (found at [www.wicd.net](www.wicd.net)) was suppose to have better results with Broadcom cards, but it won't let me install that due to another wireless manager, or so it says.
I'd really like to get Ubuntu working though, as it is one of my favorite distros.

*Thanks for your time TrekCaptain, I appreciate it!*

---

### Post by Dude-PWB- on 2009-11-17
If you install wicd from synaptic, it should remove the default network manager when it installs. Synaptic tells you it is going to remove it when you mark wicd for installation.

---

### Post by codylambrecht on 2009-11-17
Thanks Dude-PWB-,
I'll have to check that out, I've got a handful of things to try now between those suggestions and a friend that's trying to help me out.
I'll report back if any of them work incase anyone else has the same problem as I do, that way they can find the info too!

Thanks for the quick responses! Much appreciated.

---

### Post by codylambrecht on 2009-11-18
Stupid Broadcom Wifi Card.
I tried using the driver I was linked to above...
I should have seen that link, but I was sooo brain dead yesterday. lol.

I've decided to try out LinuxMint.
I've been told by a few friends that their laptop works fine with it and they had the same problem as me and spent a long time trying to fix it before just installing LinuxMint and it worked.
So thanks for the Replies, I'll be trying LinuxMint and if it still doesn't work, I'll be back to Ubuntu.



Edit: I have tried LinuxMint, and I love it.
It runs 100% out of the box for me. It was based off Jaunty I believe (if not, an older version of Ubuntu).
I have no complaints about it and I've been moding it like crazy.

---

