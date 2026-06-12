---
title: "Wireless PCi network card stops Xubuntu 18.04 from booting"
date: 2021-01-24
forum: Networking &amp; Wireless
---

### Post by fozziebear on 2021-01-24
I have installed Xubuntu 18.04 on an old Dell 4550 P4 tower to give away to someone doing home schooling during this pandemic. 
Most people need wifi to connect to a router or hotspot so I bought a cheap Belkin Wireless G PCI card on a well known auction site. However now that it is installed in the system the boot process for Xubuntu halts. 
Initially this showed a black screen so I thought I would add nomodeset to Grub. This time it boots as far as the Xubuntu splash screen and halts.
Ive tried the card in each of the three pci slots but it makes no difference. The card has a Realtek RTL 8185L chip and if relevant I removed an old dial up PCI modem to install the wifi card. The PC has an add in graphics card as no onboard video.
Does anyone have any suggestions please.
Fozzie

---

### Post by CelticWarrior on 2021-01-24
This one? -> [https://www.cnet.com/products/dell-dimension-4550-mt-p4-2-53-ghz-512-mb-30-gb-lcd-17/](https://www.cnet.com/products/dell-dimension-4550-mt-p4-2-53-ghz-512-mb-30-gb-lcd-17/)
If so, I'm afraid your noble intentions are wishful thinking. A 20 years old desktop is simply not suited for the usage you want to give it, even you find a working WiFi solution. I suspect the card you bought is faulty but it can also be just too much for the old machine. After all, in spite of being almost obsolete as are all "g" standard devices, the card itself is likely 10 years newer than the computer.

The Nvidia card, at best, works with the open-source driver (Nvidia dropped support for that card a very long time ago).
The RAM is insufficient for any modern OS (with a desktop environment).
Networking is likely possible with the integrated Ethernet NIC but you need realistic expectations.

For home schooling? Absolutely no way.

It can still work acceptably in some server roles with an headless OS like Ubuntu Server. Or for retrocomputing with Windows XP and period appropriate games and other software but in that case NOT connected to the internet, NEVER.

---

### Post by fozziebear on 2021-01-24
Thank you,
I appreciate that this is far from ideal but when you take the fact that in some households children are sharing a mobile phone to do home schooling then "almost" anything is better than that. 
The system has a 2.8Ghz P4 and 1Gb ram and Xubuntu 32bit installed. Although very slow to boot once in the OS you could use firefox to get on the internet. I was trying to sort out wireless networking as many people have their routers in the entrance hall or are using hotspots on their mobile phones to connect to the internet. In the last lockdown I supplied several similar old repurposed systems to great effect.
 I can change the video card to something other than an Nvidia if indeed the existing card is that make. It booted and ran prior to installing the card so what could have changed. You are correct it could be a damaged card but will try that in a windows PC first to establish its working.
Should I try reinstalling Xubuntu with the network card already in place?
Fozzie

---

### Post by DuckHook on 2021-01-24
> **fozziebear said:**
> Thank you,
I appreciate that this is far from ideal but when you take the fact that in some households children are sharing a mobile phone to do home schooling then "almost" anything is better than that.
While true enough, the resulting product must at least be functional. My grandchildren had to home&#8209;school for a portion of the pandemic and if your clients' experience is similar to theirs, then this involved some video&#8209;chatting and groupware&#8209;like activities. CelticWarrior is right that your old P4 will likely give up the ghost under that sort of load.

My old P4 machine with 1GB would regularly crash or freeze with a modern GUI, no matter what I tried in the 'buntu ecosystem. I eventually got barely passable performance out of it by installing the super lightweight distro: Bodhi. Even then, a single running instance of Firefox maxed out the RAM. Trying to launch any further app resulted in disk thrashing from too much swapping, and that old disk was painfully slow for swap. I kinda&#8209;sorta worked around that issue by using Midori which uses less resources than FF. And this was a few years ago (I no longer have that machine). Modern OSes have just become even bigger and more resource intensive since.

If you are absolutely intent on rehabilitating this ancient box, then at a minimum, you will need to beef it up to 2GB RAM. Unfortunately, generation 1 DDR is hard to get these days and proving to be expensive.

Even with enough RAM, I'm not sure that the CPU is up to video&#8209;chatting and groupware, but it's up to you whether you want to give it a try.

I'm not a WIFI expert, so perhaps you can wait for one of our network gurus to chime in on your WIFI issue. I do know that the less you pile on to this box, the better, so it would be advisable to forego WIFI altogether and try to hook this thing into a router by old fashioned ethernet cable.

---

