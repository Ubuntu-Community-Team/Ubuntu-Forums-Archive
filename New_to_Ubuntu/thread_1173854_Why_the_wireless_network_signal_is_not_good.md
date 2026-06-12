---
title: "Why the wireless network signal is not good?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by DSClear on 2009-05-30
I have a dual system in my laptop, xp and ubuntu 9.04. Why the wireless network connection under ubuntu is always slower than xp? Say in XP I can get the wireless signal by 80%, but in ubuntu I could only have 45%. 

Is there anyway to optmize the network connection in ubuntu so I can get stronger wireless network signal?

Thanks.

---

### Post by SunnyRabbiera on 2009-05-30
This more or less depends on the card, as linux is not windows most hardware doesnt like to work with it as linux isint owned by some billion dollar company that cares more about money then its customers.
Wireless has always been an issue with linux but its not entirely our fault.

---

### Post by Crosbie on 2009-05-30
Is it actually running slower, or just reporting a weaker signal strength?  Try a sample download under each OS (assuming the source is stable) and see whether there's a speed difference.  

It may be that either Linux is under-reporting - or Windows is over-reporting - the signal strength.  If so, and the speed is actually constant, then hey, this is just cosmetic.

---

### Post by DSClear on 2009-05-30
Yeah, you are right, you remind me that I have installed a previous version of Ubuntu, and it didn't have the wireless feature that time. The speed of wireless connection is indeed slow, I am now downloading updates package under a normal speed at 8KB, I am using ADSL 2M, so it's not comparable with xp. But anyway, this version of Ubuntu is really nice and I think will only switch to xp once need download big files. I hope linux will improve the wireless drivers in future, thanks anyway.

---

### Post by jonathanysp on 2009-05-30
mm for me the wireless seems to be better in linux! anyways are you using ndiswrapper or drivers that came with ubuntu? maybe try compiling them yourself that may be better. Im not sure tho

---

### Post by 3rdalbum on 2009-05-30
What chipset does your wireless card use? (running "lspci" and/or "lsusb" in a terminal will tell you)

There's only one chipset that I'm aware of that gives low signal strength (actually low signal quality) and slower speeds than it should, and that's the RTL8187. Unfortunately it seems that whenever you buy a wireless device that's advertised as being "Linux-compatible", it's the RTL8187 :-(

You can compile the Aircrack driver (sorry I don't have the URL to hand for this) which will give you good speed and range, but it will limit you to WEP encryption. Alternately, you can do as I'm currently doing and search out another card until the problem is fixed. The RTL8187 chipset used to work acceptably well on Ubuntu until 8.10.

---

### Post by growled on 2009-05-30
I would think the difference might be in the driver. That is, if both OSes are in fact reporting the right signal amount. Can you tell any differences when using them?

---

### Post by DSClear on 2009-05-30
It report my laptop is using  **Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) **This should be a very regular wireless card, isn't it? I pasted other devices here:
CPU: Duo T2370
HD: Hitachi 120G
Board: Intel PM965
Graphic: HD2400
Memory: 1G DDR2
I don't know how to compile or crack a driver, but I have a question, if bought a new wireless card and installed in my laptop, will it conflict with the one built-in the board?

I have just tried with download mp3 file from the same site in xp and ubuntu, both maintained 120k/s, maybe the server of Ubuntu update server is too busy that make the speed very slow. So it seems the signal reported in either Ubuntu or xp is not accurate, however even the signal looks weaker than xp, but the speed of download is almost the same.

---

### Post by raymondh on 2009-05-30
> **3rdalbum said:**
> There's only one chipset that I'm aware of that gives low signal strength (actually low signal quality) and slower speeds than it should, and that's the RTL8187. Unfortunately it seems that whenever you buy a wireless device that's advertised as being "Linux-compatible", it's the RTL8187 :-(


I have no problems with speed and quality using the rtl8187 on my MSIWind and 9.04 ....I digress.... back to the OP and thread.

---

### Post by 73ckn797 on 2009-05-30
I have experienced similar issue using a Trendnet Wireless card on the desktop. Weak signal strength and slower speed. I installed the XP driver from the CD provided (your case will vary unless you have a disk with the drivers provided). I used "ndisgtk" found in Synaptic. It is a GUI tool that accomplishes the same as using "ndiswrapper" from the command line. That fixed my situation on 2 desktop units.

---

### Post by Qchan on 2009-12-01
[b][color=darkred]
I found the solution. Appears to have a lot to do with the drivers. I had a similar issue on my Ubuntu laptop. I'd even have the antenna on the router touch the top lid of the laptop and still get about 60% which didn't make any sense at all!

Then I went here:
[http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/](http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/)

Follow those instructions and you should be all set. If that's too much of a hassle for you to do, then basically it tells you to install the backports wireless drivers. You can do that by enabling them in the software sources and then opening terminal and typing:

[/b][/color]
> 
sudo apt-get update && sudo apt-get install linux-backports-modules-wireless-karmic-generic

[b][color=darkred]

This only applies to Karmic Koala, but it should be available in other versions of Ubuntu if you just change the name of whats there.
[/b][/color]

---

