---
title: "5 in 1 card reader"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by kennyg1 on 2010-04-10
I have an acer aspire 3050 that I installed ubuntu 9.10 (karmic) on and all is well except for a couple of issues.  The card reader is not showing up or working.  My lg vu is not recognized as mass storage (or anything else) and the touchpad is too sensitive. The GUI properties are really not working. It shows a few adjustments, but they have no effect.  Can anyone point me to where I need to be to get more info on fixing these.  I installed pmount but that did not do anything.

---

### Post by norm7446 on 2010-04-10
Have you tried putting in a memory card into your 5 in 1 reader. If not try it, if the card does not mount onto the desktop have a look in places on the top bar of the desktop. As for your Touch pad have a look on the below
Ubuntu documentation page.

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Hope this helps.

---

### Post by philodice on 2010-04-11
I booted up with a card in the reader and it worked from then on.  I have an Acer Aspire One so I hope this helps.
Lots of people have this problem with the acer.

---

### Post by kennyg1 on 2010-04-11
> **norm7446 said:**
> Have you tried putting in a memory card into your 5 in 1 reader. If not try it, if the card does not mount onto the desktop have a look in places on the top bar of the desktop. As for your Touch pad have a look on the below
Ubuntu documentation page.

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Hope this helps.

Yes, I have put the card in.  I dosent recognize the card reader at all.  I dont see it under "computer" or at the top of the desktop.

---

### Post by norm7446 on 2010-04-11
Put the card back in. Then open a terminal ( press CTRl + ALT + T ) and type  lsusb  at the prompt and press return. This should give you a list of a items attached on the USB ports of which your card reader should be one. If it still does not show up then... Pass. Sorry. As I have never had a prob with usb when using Ubnutu.

---

### Post by kennyg1 on 2010-04-11
> **norm7446 said:**
> Put the card back in. Then open a terminal ( press CTRl + ALT + T ) and type  lsusb  at the prompt and press return. This should give you a list of a items attached on the USB ports of which your card reader should be one. If it still does not show up then... Pass. Sorry. As I have never had a prob with usb when using Ubnutu.
Thanks, but still a no go here!!

---

### Post by durand on 2010-04-11
lsusb lists all the usb devices plugged into your system. Is the card reader there? It might be easier for you to copy and paste the output here within code tags. Also, try running "dmesg" right after plugging in your card reader. Post that here as well.

---

### Post by kennyg1 on 2010-04-11
> **durand said:**
> lsusb lists all the usb devices plugged into your system. Is the card reader there? It might be easier for you to copy and paste the output here within code tags. Also, try running "dmesg" right after plugging in your card reader. Post that here as well.

the card reader is on-board, not plugged in to a usb port.  Are we talking about the same thing?  I will copy paste anything you need to see.  Just walk me through it.  I know how to open a terminal and it say this:

kenny@kenny-laptop:~$

---

### Post by kennyg1 on 2010-04-11
> **kennyg1 said:**
> the card reader is on-board, not plugged in to a usb port.  Are we talking about the same thing?  I will copy paste anything you need to see.  Just walk me through it.  I know how to open a terminal and it say this:

kenny@kenny-laptop:~$

kenny@kenny-laptop:~$ dmesg |tail
[   26.340093] [drm] writeback test succeeded in 1 usecs
[   36.401682] wlan0: authenticate with AP 00:1e:e5:b4:bd:5f
[   36.403916] wlan0: authenticated
[   36.403923] wlan0: associate with AP 00:1e:e5:b4:bd:5f
[   36.406031] wlan0: RX AssocResp from 00:1e:e5:b4:bd:5f (capab=0x401 status=0 aid=2)
[   36.406036] wlan0: associated
[   36.406725] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.796009] wlan0: no IPv6 routers present
[   85.640123] Marking TSC unstable due to cpufreq changes
[   86.176046] Clocksource tsc unstable (delta = -277739745 ns)
kenny@kenny-laptop:~$

---

### Post by steveneddy on 2010-04-11
Run

```
lsusb
```

in terminal and post the output in this thread.

Just because it isn't plugged into a USB post doesn't mean that it isn't on the USB bus. Most peripherals in your PC are connected through USB, but just INSIDE of the computer.

---

### Post by kennyg1 on 2010-04-11
> **steveneddy said:**
> Run

```
lsusb
```in terminal and post the output in this thread.

Just because it isn't plugged into a USB post doesn't mean that it isn't on the USB bus. Most peripherals in your PC are connected through USB, but just INSIDE of the computer.

Ok:

kenny@kenny-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kenny@kenny-laptop:~$

---

### Post by durand on 2010-04-11
Oh sorry, I just assumed that it was usb because it was in a netbook. "lspci" might reveal it instead. That's how my card reader is connected. And I guess that's why dmesg doesn't show anything either. Hmm. Try putting a card in and then typing dmesg. It has to give an error as to why it isn't working..

---

### Post by kennyg1 on 2010-04-11
> **durand said:**
> Oh sorry, I just assumed that it was usb because it was in a netbook. "lspci" might reveal it instead. That's how my card reader is connected. And I guess that's why dmesg doesn't show anything either. Hmm. Try putting a card in and then typing dmesg. It has to give an error as to why it isn't working..

I put the command lspci in this what I got:

kenny@kenny-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
kenny@kenny-laptop:~$

---

### Post by kennyg1 on 2010-04-11
> **kennyg1 said:**
> I put the command lspci in this what I got:

kenny@kenny-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
kenny@kenny-laptop:~$ 

It looks like at 08:01: the card reader is there??  but it does not read the card is not read.  Could this be a software issue??

---

### Post by durand on 2010-04-11
Hmmmm, I did a bit of research and I can't really find a solution :S Maybe you could search a bit more? Sorry :S

---

### Post by egalvan on 2010-04-11
```
08:01.0 CardBus bridge: **ENE Technology Inc CB-712/4 Cardbus Controller (**rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
```

This is the enumeration for the card reader stuff...
Seems this reader is hung on the CardBus bus, not the USB bus.

ENE Technology was NOT supported as of 7.04 (ancient, I know ).
But I could not find any newer sources, as Hardware4Linux was not connecting...

---

### Post by durand on 2010-04-11
> **egalvan said:**
> 
ENE Technology was NOT supported as of 7.04 (ancient, I know ).
But I could not find any newer sources, as Hardware4Linux was not connecting...

Yeah, I got the same results, however apparently it worked in kernel 2.6.20...
[https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ene-technology-card-readers-538244/](https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ene-technology-card-readers-538244/)

---

### Post by kennyg1 on 2010-04-12
[QUOTE=durand;9109617]Yeah, I got the same results, however apparently it worked in kernel 2.6.20...
[https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ene-technology-card-readers-538244/](https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ene-technology-card-readers-538244/)[/QUOTE

Thanks for all your help.  Maybe the next release (lucid) will have the driver.  I will continue to learn more and research more.  Thanks again for all your help!!!

---

### Post by Kellemora on 2010-04-12
FWIW:  I tried taking the 5 card reader from an eMach and stuck it in my new box.  It didn't read any cards I plugged into it, but showed up just fine in the listing.
Moved it to another USB plug on the Mobo and then it worked just fine.

However, since I sit behind the computers, enjoying all the heat that blows my way, hi hi...... I saw a 5 card remote reader with a 6 foot cord for only 9.99 and picked it up.  Did nothing but plug it in and reads everything I shove into it.

And also leaves TONS of folders mounted on my desktop, same as viewing other drives and folders.
Seems like they should go away when you close the folder and not hang around.

Heck, you plug in 25 SD cards of images and go back to your desktop and it's filled with tons of folders that need to be unmounted.

I'm mentioning that, just in case their is a setting or something I haven't learned yet.  Or learned and forgotten is more like it!

TTUL
Gary

---

### Post by kennyg1 on 2010-04-12
> **Kellemora said:**
> FWIW:  I tried taking the 5 card reader from an eMach and stuck it in my new box.  It didn't read any cards I plugged into it, but showed up just fine in the listing.
Moved it to another USB plug on the Mobo and then it worked just fine.

However, since I sit behind the computers, enjoying all the heat that blows my way, hi hi...... I saw a 5 card remote reader with a 6 foot cord for only 9.99 and picked it up.  Did nothing but plug it in and reads everything I shove into it.

And also leaves TONS of folders mounted on my desktop, same as viewing other drives and folders.
Seems like they should go away when you close the folder and not hang around.

Heck, you plug in 25 SD cards of images and go back to your desktop and it's filled with tons of folders that need to be unmounted.

I'm mentioning that, just in case their is a setting or something I haven't learned yet.  Or learned and forgotten is more like it!

TTUL
Gary

Thanks!! That is an option I haven't considered.  I could deal with the folders left on desktop as I just load images for forums and motorcycle pics.  I will check into getting a reader (usb)

---

### Post by steveneddy on 2010-04-12
I have a spare USB card reader that I use on occasion in case the onboard card reader fails or someone needs to read a card and doesn't have a onboard card port.

This may be your "fix" besides running an older kernel. Easier to have an external reader IMHO.

---

### Post by kennyg1 on 2010-04-13
> **steveneddy said:**
> I have a spare USB card reader that I use on occasion in case the onboard card reader fails or someone needs to read a card and doesn't have a onboard card port.

This may be your "fix" besides running an older kernel. Easier to have an external reader IMHO.

Would you mind recommending a usb card reader that I should have success with??

---

### Post by philodice on 2010-04-15
I went back and checked my 5-1 card reader, and I apologize for saying it worked earlier.  It doesn't.

---

