---
title: "wlan0, wireless card, ndiswrapper, not working"
date: 2005-04-01
forum: Networking &amp; Wireless
---

### Post by willhig on 2005-04-01
Hello,

I am rather new to linux having installed it only a week ago. Immediately I was faced with difficulties having to install and configure a wireless card.

Currently I am using the latest Warty with the NDISwrapper it installs via Synaptec (connected via ethernet - it works, but it cannot be permenant) and I have installed the necessary driver. I added wlan0 the network interface list as well, though I cannot activate it. Each time I click "activate" or check the box beside it, it almost immediately unchecks. I even deleted the ethernet interface...

Also I cannot boot with the card in. When it reaches "Configuring Network Interfaces", it pauses for a few minutes, then spews loads of information, ending in a "...failed - not syncing".

Once again, I'm completely new to linux, so I'm terrible at using non-GUI interfaces... is there a solution? Should I try Hoary? Should I use a different card? Or have I done something wrong / missed anything? Thanks ^_^.

---

### Post by p0ke on 2005-04-01
more information about your card (chipset, etc.) and your hardware will help in troubleshooting.

---

### Post by stevenyu on 2005-04-01
I just got ndiswrapper working in Hoary:

WIFI NIC - Netgear WG311V2 (TI Chipset)

I need to actually remove the acx100 module from the /lib kernel driver wireless module, otherwise ndiswrapper will not load.  Once it been remove, and ndiswrapper , just make sure you have done "**ndiswrapper -m**" to write the entry to modprobe.conf, as well as "**depmod -a**" to update the module listing.

Hope this help   :roll:

---

### Post by az on 2005-04-02
Manufacturers do not care all that much about your right to use free and open source software.   That is why this sort of thig is as painful as it it.

What is the make of your card.  Be specific if there is a hardware revision.

You may already have a linux driver trying to work.  Installing ndiswrapper alongsode that may not always give you good results.  It is quite simple to bloacklist the linux driver in favor of the windows (ndiswrapper) driver.  But We would need top know the type of card.

---

### Post by willhig on 2005-04-03
It's a Linksys WMP54G version 4, the Ralink chipset. Sorry, I thought since I had already installed the proper driver, I wouldn't need to post that info...

---

### Post by Mr Black on 2005-04-05
willhig,

I have that same wireless card in my Ubuntu system and it works just fine using ndiswrapper.  I would start off by asking if you are sure that you setup the card correctly.  Just double check everything to make sure its working.  The following [link](http://www.ubuntuforums.org/showthread.php?t=19978) may help, I know it did for me. 

Does your machine stop booting after running the network configuration or does it continue to boot, but the network card isn't working when you start gnome?

You might want to check to see if the modprobe command was sucessful.  If you are unsure try removing ndiswrapper and then readding it.  If you get any errors please try to post the output from the terminal.  It helps a lot when trying to describe your problem to others on the forum.

[SIZE=2][I]#to remove
modprobe -r ndiswrapper

#to re-add
modprobe ndiswrapper[/I][/SIZE]

If you could post what is returned from the *ifconfig* command that might help as well.

If you think the system stuff is all fine make sure the settings for the card are correct.  Are you using any encryption? If so make sure its setup.  Did you remember to setup the SSID? Are you getting a strong enough singal from the router?

---

### Post by willhig on 2005-04-06
Thank you for your advice! I'll work on it some more and see if anything works...

if not, I'll have more input than earlier... thanks so much!

??????

---

