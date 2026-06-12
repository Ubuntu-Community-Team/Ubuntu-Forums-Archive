---
title: "Ubuntu 14.04 on Dell E1705 WiFi STILL not working"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by Mike_Goltsman on 2014-09-09
Installed a fresh 14.04, no Enet no WiFi. Follow a bunch of suggestions for versions other than 14.04 - purged bcmwl-kernel-source, installed linux-firmware-nonfree. This seemed to activate the Enet but not the WiFi. Here is some system info:

```
mike@OldLaptop:~$ uname -a
Linux OldLaptop 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

```

```
mike@OldLaptop:~$ lspci -nn -d 14e4:
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

```

mike@OldLaptop:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


```

Based on the sticky note in this forum, linux-firmware-nonfree is the right package to enable the WiFi for my card. And yet, no dice. I am just about ready to throw in the towel and go buy a supported USB WiFi dongle (they don't really break the bank these days - BTW a suggestion for an economical WiFi USB dongle would also be welcome), but it irks me to leave it without exlaining WHY this does not work. I have been around computers longer than I am willing to admit but am a shameful noob in Linux. Would appreciate suggestions on how to go digging to figure out what it is that my hardware and Linux configurations don't agree on.

Cheers,
Mike.

---

### Post by weatherman2 on 2014-09-09
"WHY doesn't this not work?"  Because Broadcom wireless cards are notorious for having install/driver issues in Linux, and the solutions often change from release to release.   (It may be due to non-open source drivers not being available for some Broadcom chipsets, so good drivers may not automatically be available when installing.)  I usually don't waste my time with Broadcom wireless card and simply replace them, because doing so is usually easier and cheaper than buying a USB wireless card.  (But not in HP or Lenovo laptops - because they don't allow use of non-approved "whitelsted cards" in their laptops.)

In your E1705, replacing the internal wireless card is very easy.  Power it off, unplug the power, remove the battery, turn it over...and find the panel on the bottom removed with one (two?) screws to expose the wireless card.  There is either a clip or one screw holding the card in (I had an E1705 but died and I removed the wireless card before recycling it but can't remember the exact details.).  And there are two antenna wires clipped on - just pop them off.  Replace the new card, clip the antenna wires back on.  Easy.

I recommend an Intel WiFi Link 5100.  This is an 802.11n dual band wireless card I have used in several Ubuntu laptops with excellent results.  You need a FULL HEIGHT card (not half height) for the E1705.  The exact part number is "512AN_MMW" .  There are better mini-PCI wireless cards than the 5100 available but they are mostly half-height cards that can't be secured in the laptop without an adapter.  The 5100 is a great deal and will be a huge upgrade from that old G Broadcom card, anyway.

You can find used Intel 5100 cards on eBay usually for under $10 USD or even under $5 USD shipped.  _IMPORTANT_: you don't need a "Dell" version of the Intel card, but you *don't* want one for HP, Lenovo, or IBM!  (Those versions may work OK in Linux but if you ever want to run Windows again you may have problems getting a driver to work.)  Get a Dell, Sony, Toshiba, Gateway, or Acer version of the 5100 and you should be fine.  Buy a used card - don't get a "new" one shipped from Asia, as the ones I used to buy seemed to be mismarked or non-functional "samples."  All the used cards I have bought on eBay have worked fine.

---

### Post by Mike_Goltsman on 2014-09-10
So, the issue is that Broadcom tweaked the design of these cards enough to change the driver interface frequently, and provided adequate intelligence in its Windows driver suite but not quite so consistently in Linux distribution - and the drivers can't be fixed because they are not OSS? I could live with that. If even the cards with the same PCI ID require different approach based on circumstances, then certainly nobody but Broadcom can sort out this mess. I would be curious whether there are some system logs etc. that I could examine (like I said - I am new to Linux but too curious for my own good) to figure out that yes the right driver did try to load but no, it did not succeed because of this here fault.

At any rate, thanks for the recommendation for a replacement card - looks like it should not be a big deal to procure and swap out.

---

### Post by chili555 on 2014-09-10
With all respect to my colleague weatherman2, the Broadcom 4311 is very easy to get going, assuming the firmware is correctly installed and the switch is not off. Let's do some diagnostics. Please open a terminal and run and post:```
dmesg | grep b43
rfkill list all
```Thanks.

---

### Post by Mike_Goltsman on 2014-09-10
Here we are:

```

[    4.107160] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    4.176173] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[    4.224090] b43 ssb0:0: Direct firmware load failed with error -2
[    4.224096] b43 ssb0:0: Falling back to user helper
[    4.647273] b43 ssb0:0: Direct firmware load failed with error -2
[    4.647280] b43 ssb0:0: Falling back to user helper
[    4.667400] b43 ssb0:0: Direct firmware load failed with error -2
[    4.667402] b43 ssb0:0: Falling back to user helper
[    4.723846] b43 ssb0:0: Direct firmware load failed with error -2
[    4.723848] b43 ssb0:0: Falling back to user helper
[    4.752110] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    4.752112] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    4.752114] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

and no output for "rfkill list all".

So, there's some clueing right there. I will try to "carefully read all instructions", but would appreciate assistance.

Cheers,
Mike

P.S. after "carefully reading all instructions", I am sure I can follow them but am not sure if they are close enough for the distribution that I am running. Will wait to see if can get any advice here before going and tearing it all to bits in an attempt to fix it.

---

### Post by chili555 on 2014-09-10
As you see, you need firmware. Please get a temporary internet connection; ethernet, tether or however. Open a terminal and run:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```After a bit of churning and downloading, reboot and enjoy your wireless!

---

### Post by Mike_Goltsman on 2014-09-10
Huh. That did it. Thank you so much for your help. 

So, the reason for this mess was that the driver package that I use for the wifi is "linux-firmware-nonfree" which is too generic to include the b43 firmware? Seems odd - to include the driver that won't work without the firmware but not the firmware package or at least a dependency to pull in that package? Is it because the same package would require a terabyte of various proprietary firmware packages if all of them were included "just in case"? So the least bad approach is to include the common ones (or none) and let those that need a specific package figure it out the way I did? One would think that there should be some scripting available in the post-install for "linux-firmware-nonfree" to figure out which hardware is actually present and pull in the relevant packages still?

 Just curious...

---

### Post by chili555 on 2014-09-10
Not exactly. As a matter of fact, it is a good bit more complicated. The b43 firmware was improperly, because it violates Broadcom patents, included in nonfree until just a few days ago. At that time, you and a few other cases blew up in our faces.

Now we use the Broadcom-approved method above and all is right in the universe again. The sticky is being corrected in the next day or so. 

Glad it's working!

---

### Post by weatherman2 on 2014-09-10
There have glitches with installing Broadcom wireless drivers for years, as long as I have been Ubuntu on laptops.  (On the other hand: TomatoUSB Linux-based firmware works only on Broadcom-based routers and it extremely solid.)

Although people do report issues with Intel wireless cards, personally I have never had to do anything to make an Intel wireless card work - they have worked automatically with a good dozen or more installs now.  For the original poster's E1705: I say it's still worth the $5 USD and 10 minutes to swap in a 5100 wireless card to get 802.11n + dual band WiFi, that should work in future Linux releases without jumping through any hoops.

---

### Post by varunendra on 2014-09-11
> **weatherman2 said:**
> I say it's still worth the $5 USD and 10 minutes..
+ the time to walk to the nearby shop, pick'n pay, return home, open the cover......

Oh my, did I already get past 10 x 10 minutes? :p

OR,

Connect via working Ethernet > run the supplied commands 
= less than 2 minutes + "enjoy (hopefully) until the laptop or the OS dies by itself" --> true for this particular card.

Will have to be done on every fresh install, but 2 minutes (assuming a working Ethernet connection) isn't much trouble, is it?
I don't hate Intel (not even Realtek!), but pushing for it doesn't seem necessary to me here.

---

### Post by chili555 on 2014-09-11
> Will have to be done on every fresh install, Indeed it will, however, you could save your entire /lib/firmware/b43 file to a USB or CD and, after install, drag and drop the b43 folder to your desktop. Then:```
sudo mkdir /lib/firmware/b43
sudo cp ~/Desktop/b43/*  /lib/firmware/b43
```Then unload and reload the driver so it sees and uses the shiny new firmware:```
sudo modprobe -r b43 && sudo modprobe b43
```Stick the USB or CD in the drawer and use it again and again.

Less than US$5 and less than 10 minutes.

---

