---
title: "Audio Help"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by deckroid on 2011-02-21
Hi

I just installed Ubuntu on my Aspire 6530 laptop and so far, I like it.  I have a question about my audio though.  

I have done the searching for this, and what I have found either is from 2007-08 and doesn't work/isn't relevant now or I don't understand the ins and outs of using the Terminal yet.  

I am trying to get my sound to sound better than it does.  I have a surround sound dolby home theater 5.1  system inside this little machine (ok it's a Virtual Surround Sound system but it still used to sound great).  Earlier today, when it was Windows 7, I had no issues with movies or Pandora or mp3s.  Now, it sounds like an old transistor radio that's inside a desk drawer.  I have tested movies, mp3s and online content.  Same issue. Yes, there is sound but the quality is so low it might as well not even work.

Here is my lspci info: 

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
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
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)

I have gone into Sound Preferences and under Hardware there are two items listed. 

Internal Audio and RS780 Azalia controller.

Under Internal Audio, there are 5 choices but only two produce sound, and they are the same poor quality sound.

If I chose RS780, there is no sound.  

Under Output, the same two choices are there and I have tried different variances to see if that would make a difference.  Nothing.  

I have installed Wine and gone and gotten the different Window drivers from Acer and Realtek; no changes.  I have downloaded the Unix driver and followed the Readme, as closely as I could and still no change.

I have searched and tried all the things I found to no avail.

I have rebooted after each download and install. 

This is now going on 7 hours of searching and trying different things.  I am off to bed so I can start fresh in the AM. 

Thanks in advance for any assistance you can give me.

---

### Post by mikewhatever on 2011-02-21
> **deckroid said:**
> 
...
Under Internal Audio, there are 5 choices but only two produce sound, and they are the same poor quality sound.

...

Perhaps the others are simply muted? Run 'alsamixer' in a terminal window and see what you can unmute. (Arrow keys to navigate, 'm' to mute/unmute)

---

### Post by deckroid on 2011-02-21
I thought of that, so I checked and here is what I have in alsamixer...

Master
PCM
Front
LFE
Line
CD
Mic
Mic Boost
S/PDIF is either on or off, has no bar
S/PDIF D same thing. Either muted or not, but no bar either way
Beep

I went through and unmuted everything.  No change.

Thank you for the reply.

** I really think the fix here is going to be a simple Choose This Instead of That kind of thing... the kind that my in-laws have me come over and fix on a regular basis on their Vista machine.

---

