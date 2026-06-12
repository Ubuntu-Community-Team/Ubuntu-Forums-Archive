---
title: "Pretty big wireless internet problem."
date: 2009-12-09
forum: New to Ubuntu
---

### Post by iheartcoa on 2009-12-09
After many days of successfully using the 9.10 live CD, I finally decided to completely wipe out Windows Vista and install 9.10 on my laptop.  While running the live CD my wireless internet didn't work immediately, but the drivers pop-up came up and after installing the drivers, it worked fine.  Okay, so I installed today and NO MORE INTERNET FOR ME!  The driver pop-up has not come up and I am completely confused...I don't even know what kind of chip I have or where to begin.  For reference I have a HP Pavilion dv4-1225dx.  Please help!

---

### Post by CaptainMark on 2009-12-09
do you get anything if you go to system>admin>hardware drivers if it popped up in the live cd it should be listed there

EDIT: try this with a wired connection too, should work

---

### Post by iheartcoa on 2009-12-09
Yep I tried that and nothing came up.

---

### Post by stoogiebuncho on 2009-12-09
1) Make sure your computer is connected to the internet via a wired connection.
2) Go to System > Administration > Hardware Drivers
3) If there are no drivers there for you to enable, restart the computer (leave it connected to the internet via your ethernet cable)
4) Once it's restarted, look in Hardware Drivers again.  I don't know why, but restarting almost always makes it find the driver.

---

### Post by iheartcoa on 2009-12-09
Argh I connected to a wired connection (which works perfectly), restarted, and tried the hardwire drivers again.  Still nothing.  The wireless icon on my keyboard is red when it should be white, and it won't turn white if I touch it.

---

### Post by bkratz on 2009-12-09
> **iheartcoa said:**
> After many days of successfully using the 9.10 live CD, I finally decided to completely wipe out Windows Vista and install 9.10 on my laptop.  While running the live CD my wireless internet didn't work immediately, but the drivers pop-up came up and after installing the drivers, it worked fine.  Okay, so I installed today and NO MORE INTERNET FOR ME!  The driver pop-up has not come up and I am completely confused...I don't even know what kind of chip I have or where to begin.  For reference I have a HP Pavilion dv4-1225dx.  Please help!




Do you remember the name of the driver that popped up, could it have been something like b43?

---

### Post by iheartcoa on 2009-12-09
I don't remember!  I do remember seeing Broadcom, though.

---

### Post by bkratz on 2009-12-09
[quote=iheartcoa;8471707]I don't remember!  I do remember seeing Broadcom, though.[/quote


Ok,  go to the terminal and type in   lspci | grep Wireless

(that is LSPCI in lowercase)

And see if it tells you a part number something like BCMXXXX


if you don't know how to get to the terminal just ask

---

### Post by sldavid on 2009-12-09
If the command 'lspci | grep wireless' produces no results try the same command with a capital W. Like this:

lspci | grep Wireless

I only caught this because it applied to me.

Good luck.

---

### Post by teward on 2009-12-09
do this:

lspci

show us teh output.  we can determine the driver from the card make/model stuff

---

### Post by bkratz on 2009-12-09
Sorry it was supposed to be capitalized!!

---

### Post by iheartcoa on 2009-12-09
I tried the command both ways and neither produced any results...just gave me a new empty command line.

---

### Post by bkratz on 2009-12-09
OK, just try lspci and decode the output!

---

### Post by iheartcoa on 2009-12-09
Here's what it gave me when I just put in lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
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
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by bkratz on 2009-12-09
OK this thread will give you what you need, if not just ask again.

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

Good Luck

---

### Post by Palanthas on 2009-12-09
Perhaps try running the Live CD again and see what driver pops up.

(oops sorry, I was still back on message #6)

---

### Post by teward on 2009-12-09
You'll need the drivers for this:

Broadcom Corporation BCM4312 802.11b/g (rev 01)

But the drivers exist only as Winblows drivers, so you'll need to use ndiswrapper.

---

### Post by bkratz on 2009-12-09
> **TrekCaptainUSA said:**
> You'll need the drivers for this:

Broadcom Corporation BCM4312 802.11b/g (rev 01)

But the drivers exist only as Winblows drivers, so you'll need to use ndiswrapper.



Please see the thread in my last post

---

### Post by iheartcoa on 2009-12-09
Hmm...in the terminal it said it couldn't find package linux-backports-modules-karmic?

---

### Post by bkratz on 2009-12-09
> **iheartcoa said:**
> Hmm...in the terminal it said it couldn't find package linux-backports-modules-karmic?

Did you put in the rest?   

 sudo apt-get install linux-backports-modules-karmic b43-fwcutter

---

### Post by iheartcoa on 2009-12-09
Yes I did.

---

### Post by bkratz on 2009-12-09
You are still hooked up to the wired connection right.

If so,
Go to system--administration--synaptic package manager
put in password
press the reload button
search for b43
it should come up with the b43-fwcutter there

and mark it for installation

---

### Post by iheartcoa on 2009-12-09
Okay I did that and still no change.

---

### Post by bkratz on 2009-12-09
> **iheartcoa said:**
> Okay I did that and still no change.



Now reboot and see it there are any hardware drivers to enable

---

