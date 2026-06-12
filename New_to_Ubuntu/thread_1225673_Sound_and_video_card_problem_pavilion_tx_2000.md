---
title: "Sound and video card problem pavilion tx 2000"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by markmai86 on 2009-07-28
Hello,

I have just installed the latest version of Ubuntu and I'm pretty new to this. I have partitionned my hard drive so I can have some programs I still need in windows.

The problem is that my sound works perfectly with windows and I have only a modem sound like with ubuntu (only beeps...)

I have tried some command lines I found on the net but nothing worked. Maybe the sound is set to a settings which prevents other sounds that beeps, but I can't solve the problem.

I have tried all the options and autodetect in the sound settings preferences (in the system menu) and nothing worked after testing (where I suppose I should here any kind of sound).

So basically when I receive mail with Evolution I get a beep and that is about the only sound I have.

I also think my video card is not installed as the games I have installed are running really slow... but I really have no idea on how to set up the video card.

Thanks for helping me

PS:  I have a laptop HP pavillion tx 2000 from 2008


the output of lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
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
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by gali98 on 2009-08-03
Hmmm... You don't have the tx2000... I think you have a tx2500... (since you have ATI graphics.) Confirm this by looking on the bottom sticker by the model: tag.
There are *several* threads on how to get everything to work. (Just search with "tx2*" without the quotes.)

On your two issues, 
Graphics:
Go to System->Administration->Hardware Drivers 
and enable everything. 
Sound I am not quite sure about, so search the forums with that tag I gave you and you will find plenty of threads. Just look for something like "HOWTO: Set up tx2500 blah blah"
Kory

---

### Post by Favux on 2009-08-03
Hi markmai86,

For the TX2500 you want to add the line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
to the end of the alsa-base.conf file.  Which used to be called alsa-base before Jaunty.  To do that in a terminal enter:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add the line to the end.  Save and restart.

Hope this helps.

---

### Post by dado_eyad on 2009-09-29
i have the sound working
and i installed all the drivers
but still the system hangs on full screen

how can i fix it????

---

