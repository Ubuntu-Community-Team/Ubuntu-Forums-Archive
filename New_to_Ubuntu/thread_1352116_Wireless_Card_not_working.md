---
title: "Wireless Card not working"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-11
Ubunteros,

I have a D-Link wireless card model WDA-1320. It's 802.11G.

I like this particular card and model because I have 3 PC's throughout the house that I have them in. All the PC's are running Ubuntu 8.04LTS.

Each time that I installed this specific card the entire process was straight forward. The card was always immeadiately recognized and the only thing I needed to do was enter the Wi-Fi networks password and I was off and running.

I just finished putting together a PC for my Dad. Because I did not have a card for his PC readily available, I borrowed one from my other PC. In the meantime I mail ordered one for his machine (i.e. WDA-1320).

Yesterday the card I mail ordered arrived. It might sound wierd but I wanted to put the mail ordered card into the machine I build for Dad and take the loaner out and put it back into the machine where it came from.

In theory, because both cards are the same model and brand this should be a simple swap. But now this new card isn't even recognised. I'm unsure as to what I should do next. If someone could guide me I'd be most appreciatitive.

Thank You!

---

### Post by cartisdm on 2009-12-11
Does it not even recognize that a new card has been installed?  At the very least it should have picked up the new hardware and configured it for the correct drivers.

(Yes, they may be the exact same card in theory but hardware can always vary from device to device - particuarly the firmware etc)

---

### Post by suomalainen on 2009-12-11
Hello All,

I did a lspci in terminal and this was the output I received. I guess it looks like the card isn't even recognised????

What can I do?


0:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---

### Post by suomalainen on 2009-12-11
UPDATE.

I put the new card I mail ordered into the PC I borrowed a card from. This machine is a Dell Optiplex. I kept the card that I borrowed in the HP a500n.

Now everything works! I did notice that the card I mail ordered has a f/w of 1.01 and the older card 1.00.

I guess the combination of f/w, h/w & s/w just needs to be the right combination......

Thanks!

---

### Post by cartisdm on 2009-12-11
> **suomalainen said:**
> UPDATE.

I put the new card I mail ordered into the PC I borrowed a card from. This machine is a Dell Optiplex. I kept the card that I borrowed in the HP a500n.

Now everything works! I did notice that the card I mail ordered has a f/w of 1.01 and the older card 1.00.

I guess the combination of f/w, h/w & s/w just needs to be the right combination......

Thanks!

Strange situation that it wouldn't recognize the new hardware and grab the needed drivers but glad to see you are satisfied with the setup.

---

### Post by suomalainen on 2009-12-11
Cartisdm,

Do you think the difference in f/m could have such an impact?

Thanks

---

### Post by cartisdm on 2009-12-11
> **suomalainen said:**
> Cartisdm,

Do you think the difference in f/m could have such an impact?

Thanks

9 times out of 10, no.  But my past experiences with hardware have shown me that even the slightest changes can drive you crazy when you want something to perform a certain way.  Since your dad's computer didn't recognize it as "new" hardware it was likely trying to use the card as a mirror copy of the old one (without making any adjustments to the way it reads it). Something somewhere was just different enough to cause a hangup.

As for working in your computer, I would imagine that it either picked up the hardware as new and made adjustments as necessary or isn't hitting that little hangup as your dad's computer and reads the card seamlessly.

Similar to how sometimes you can swap out a harddrive with an OS installed and put it in another computer w/ the exact same components and sometimes it will work, other times it will crash because of the hardware changes

---

### Post by suomalainen on 2009-12-11
You kinda pointed to something. When I placed the older f/w version card back into the PC from where it came, I could not log on......

I thought I tried everything and to no avail......

Then I right clicked on "network connections" and choose "edit wireless networks". I "removed" my network and closed out of this tool. I then rebooted my PC....

Viola... I was back up and running..... I guess this file held old info as per my card or network information ???????? Do you know????

Although I'm tempted to see if this resolves the experience I found with my Dad's computer I'm more happy now that 2 PC's are up and running instead of only one.

---

### Post by cartisdm on 2009-12-11
> **suomalainen said:**
> You kinda pointed to something. When I placed the older f/w version card back into the PC from where it came, I could not log on......

I thought I tried everything and to no avail......

Then I right clicked on "network connections" and choose "edit wireless networks". I "removed" my network and closed out of this tool. I then rebooted my PC....

Viola... I was back up and running..... I guess this file held old info as per my card or network information ???????? Do you know????

Although I'm tempted to see if this resolves the experience I found with my Dad's computer I'm more happy now that 2 PC's are up and running instead of only one.

I'm not 100% sure where the network information is stored on your computer, I assume it has a log file somewhere in your directory.  This log file is probably written in a specific layout that the card interprets.  By clearing the stored network and rebooting it likely writes a new log file and thus is able to read it correctly.

This was certainly an unusual situation but I'm glad you're up and running with two PCs after the initial holdup.:D

---

### Post by suomalainen on 2009-12-11
Yea, I'm glad too that I'm up and running.... Especially since Dad's plane lands in 1hr 10min!!!!

I wonder how Ubuntu 10.04LTS will perform and if I will have issues once it's released? Hopefully not.....

By the way, I got this card off of ebay from a company called Digital Outlet for only $9.95 and it came with free shipping.

---

### Post by cartisdm on 2009-12-11
> **suomalainen said:**
> By the way, I got this card off of ebay from a company called Digital Outlet for only $9.95 and it came with free shipping.

Sweet deal. I just ordered a bluetooth dongle for my HP Mini that cost $2.28, including shipping! I don't even understand how it's possible but all the reviews were outstanding and even if it ends up being a scam.....its only 2 bucks haha.

[Here is the site]("http://www.dealextreme.com/details.dx/sku.11866").  They have some other pretty good deals too that I might look into if my bluetooth device works out

---

