---
title: "Installing game with Wine?"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by McTwitch on 2010-11-10
I'm running Ubuntu 10.04 off of a portable harddrive. I have the program Wine installed, and I want to install Oblivion: The Elder Scrolls IV. The problem is, I haven't been able to install it regularly, and I can't seem to get it to work through Wine either. Any ideas?

---

### Post by Hippytaff on 2010-11-10
Sometimes it's best to use windows, especially for games, you could try running windows in a virtual box if you can't get it working with Wine, or you don't have a windows dual boot :-)

---

### Post by I'mGeorge on 2010-11-10
at wine hq it's rated platinum in [lucid lynx]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506&iTestingId=58356"). You could try install it with PlayOnLinux.

---

### Post by McTwitch on 2010-11-10
I don't really have the time or the know-how to set up a Virtual Box, and I do have a Window's machine to boot off of, but I have an extreme dislike for it. I'll take a look at PlayOnLinux, thanks for the tip.

---

### Post by NightwishFan on 2010-11-10
If you have a Nvidia card, Oblivion should work magnificently in Wine.

---

### Post by McTwitch on 2010-11-10
Right. I'm still having a few problems with Wine. If I had the time I could probably work through them, but I'm kind of in a stretch right now.
I'm trying to run PlayOnLinux, but whenever I choose a game, and hit "apply", the menu becomes unresponsive. So far, I've gotten no where either way. 
How can I find out if I have a  Nvidia card?

---

### Post by chris.noye on 2010-11-10
sudo lspci

---

### Post by McTwitch on 2011-01-17
Sorry it took me so long to reply. So many projects going at once. Anyway
I ran: ```
sudo lspci
``` But I've got no idea which line that came as a repsonse is what I'm looking for to find out if I have a Nvidia card. This is what I got out of it:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc RV710/730
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

Also, I am now running on a System 76 laptop, with Ubuntu 10.10, instead of a Portable Harddrive.

---

### Post by davidmohammed on 2011-01-17
this is your graphics card .... its an ATI not nvidia

02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

---

### Post by McTwitch on 2011-01-17
So is that completely uncompatable? Or, where do I find out if it is?

---

### Post by davidmohammed on 2011-01-17
dont think your graphics card is the issue.

What version of wine are you using?  WineHQ give your game a platinum rating for wine version 1.3.9

---

### Post by McTwitch on 2011-01-17
1.2.1 Guess I should update it. That might help a bit. I'll give a report once I've updated and attempted playing again.

---

### Post by JC Cheloven on 2011-01-17
Hey McTwitch, I'd be surprised if you succeded at playing this game: 

You said you're running an ubuntu install out of an external disk. A usb disk I assume. 
This is much less performant than a regular install. I didn't throughly read all posts in the thread ("I don't really have the time" either ;) ), but probably that's your only problem.

---

### Post by NightwishFan on 2011-01-17
With enough ram it should be ok.

---

### Post by McTwitch on 2011-01-17
Well, actually, in a previous post, though I should probably edit that first one to show the new stats, I'm running an Ubuntu 10.10 laptop from System 76. 

Anyway, the update didn't change anything, it's still not working. So, here's basically a recap.

I've managed to get Oblivion installed, finally. But now, when I hit the button for a new game, the game becomes unresponsive, and has to be force quit.

---

### Post by NightwishFan on 2011-01-17
I had oblivion working on Wine 1.2 without any tweaks.

---

### Post by kroq-gar78 on 2011-01-17
Try the development release of wine. It works without many glitches. right now its version 1.3.11

---

### Post by McTwitch on 2011-01-17
How did you install it? Apparently I'm doing something wrong.

---

### Post by NightwishFan on 2011-01-17
I installed like normal. I was using a Nvidia 6150se.

---

### Post by McTwitch on 2011-01-17
Ah, but I don't have a Nvidia. But that wouldn't make as much of a difference, would it?

---

### Post by NightwishFan on 2011-01-17
Possibly. I do not claim to be an expert on wine but it does work better with Nvidia usually. Though I am not sure why it does not at the moment. :/

---

### Post by McTwitch on 2011-01-17
Any advice? Other than getting a Nvidia, obviously.

---

### Post by NightwishFan on 2011-01-17
Start with a clean wine profile, perhaps back up the .wine directory and start over?

---

### Post by McTwitch on 2011-01-17
Sounds good. I'll put the results in my next post.

---

### Post by McTwitch on 2011-01-17
Right, the new install didn't change anything. Now I'm trying PlayOnLinux.

---

