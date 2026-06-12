---
title: "rt2500 Wireless Driver Help Needed"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by pittman on 2006-12-05
Hello everyone,

I've recently managed to convince my sister that Ubuntu would be quite a bit more stable on her laptop than the decrepit Windows install that crashed every five minutes on her. So I get around to install Ubuntu and everything works fine, right out of the box.

Except the wireless. And no matter what I do, no matter what I try, I cannot get it to work in any way. I've tried every walkthrough I can find, I've compiled the drivers from source, I've created then with module-assistant, I've wrestled with iwconfig, rutilt, and the gnome network manager. Nothing seems to work, and I'm about at my wits end now.

The machine I'm attempting to install it on is an Averatec 3700 laptop. Therefore it has a RaLink RT2500 card in it which, according to most places I've read, work right out of the box with the rt2500 driver from [rt2x00.serialmonkey.com]("rt2x00.serialmonkey.com") (which is, as far as I can tell, included with Ubuntu). But it doesn't.

I'm attempting to install Dapper Drake, if that makes any difference. 

Right now I have the wireless device "ra0" showing up in iwconfig (although, like I said, it won't connect through iwconfig). It also shows up in the gnome network manager, and rutilt can see it. None of them can actually connect with it though. 

There some strange stuff in dmesg about "irq 185: Nobody Cared (try booting with the irqpoll option)" but I'm not sure if that's related or not. Obviously it is hard to get an actual quote from dmesg, as I am not posting from the machine I'm working on.

I'm really hoping this is a simple fix for some one out there who knows more about what they're doing than I do, as I need this up and running for my sister asap.

Thanks for the help in advance. I'm heading off to get some sleep, so I'll be back in about 10 hours. Hopefully I'll just be able to plug in someones solution!

Scott

---

### Post by pittman on 2006-12-05
I really need to go to bed: I forgot to mention that, occasionally the keyboard will simply stop responding after I attempt (well, really as soon as I start) to connect to a wireless network. This happens intermittently, and it happens more with the gnome network manager than anything else. It's obviously related, but I don't see how.

Thanks again,

Scott

---

### Post by thundercow on 2006-12-10
Dude, I got the same problem--I have tried everything, and read every post on here. I think I might be a bit farther along with this, and whenever I enable the card, the computer gets very strange and slow and the mouse stops responding except in momentary spurts every 3 seconds. If I then disable the rt2500 card, it works fine. I am just going to get a pcmcia wireless card--I just don't want to get one that ubuntu is going to have problems with.

---

### Post by FrodoB on 2006-12-10
See:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29#head-afca59bb303accf7d6ee9144facd385f7c55fde3](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29#head-afca59bb303accf7d6ee9144facd385f7c55fde3)

---

### Post by am7146 on 2006-12-12
I've got the same problem with my Averatec 3270 laptop.  I've posted a thread over in the rt2500 board:

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2642](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2642)

No real progress yet.  So far, I've installed the rt2500 beta, latest CVS, and I've tried ndiswrappers around the Win2K drivers I used when I had this laptop under WinXP.  No joy so far. ](*,)   I'm just lucky that I'm close enough to the base station that I can pull a wire over and plug it in eth0. 

On the other hand, I've gotten very good at downloading, making, and installing new drivers.  

(by the way, this is my first time using Ubuntu and--aside from the pain I'm having with the wlan--it rocks.  Amazingly simple install.  Picked up graphics and sound no prob.  Firefox on the CD.  Fast.  Easy.  For a surfing machine, it's easy and perfect!)

Andy-

---

### Post by smellydog on 2006-12-15
Well, good news for me and perhaps all of you too.  After scouring all sources on the web that i could find (aprox. two weeks of wasted time) I did manage to get my wireless working in my Averatec 3270 running Edgy.  I had ALL of the symptoms that you all described and I hope that this fix works for you.

In the file /etc/X11/xorg.conf (must use sudo), i edited/added the following string under the VIA VGA adapter to read the following.

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
	**Option		"DisableIRQ"**
EndSection

This was able to deconflict an IRQ setting with the video driver or something (thus the screen locking up and the choppy mouse pointer?) I am new to Ubuntu and Linux as a whole so i am just sharing what worked for me.  No problems since.

ALSO, i had to fix my touchpad so it was not so wacked.  Give this a try in the same xorg.conf file

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

Don't forget to add the following string at the end of the file

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	**InputDevice	"Synaptics Touchpad"**
EndSection

Then use the synaptic package manager to download and install gsynaptics or some other graphical touchpad configuration tool.

Well I really hope that this was of some help for all of you

Smellydog

---

### Post by FamuLinux on 2007-01-19
Just an additional side note for posterity. I have an Averatec 3200 series laptop (3250HX-01) and I recently upgraded to Edgy 6.10. The irq poll issue from earlier versions *is* annoying but easy to fix. The error message that suggests disabling IRQ polling is valid; edit your grub startup script.

The issue with the serialmokey drivers can be avoided entirely by getting the linux drivers straight from Ralink ([http://www.ralinktech.com/ralink/Home/Support/Linux.html)](http://www.ralinktech.com/ralink/Home/Support/Linux.html)). They provide source tarballs that come with a GUI config utility. These drivers work great, and combined with the GUI you can even have support for WPA/PSK. The only difficulty is compiling Qt, then using Qt to compile the drivers. Go through synaptic package manager and you will be fine. *don't compile the drivers with qt version 3.2.1! Use something higher*

---

