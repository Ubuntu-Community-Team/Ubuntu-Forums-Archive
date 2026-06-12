---
title: "Installing a Netgear WG511v2 (China)"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by czarjosh on 2007-02-25
I am running xubuntu 6.02 and I am trying to figure out how to use my Netgear WG511v2 (China).   I am a novice and do not understand what I need to be doing.  I have read some confusing posts about ndiswrapper, which i installed using automatix, but that is all the farther I am.

Is it possible to use this card?

---

### Post by gradedcheese on 2007-02-25
This card has a Marvell chipset, which has no Linux support.  It will only work with ndiswrapper.   Personally, I would dump this card and get a different one, but if you do want it to work, ndiswrapper will take care of it.

---

### Post by jacksonz123z on 2007-03-05
I have the same card.  It worked very well with edgy until the latest kernel update (11).  After this, for me it was completely broken.  I tried the latest ndiswrapper (recompile etc) to no avail.
Finally I upgraded to feisty to fix the problem.  I used synaptic ndiswrapper 1.8, the card now is once again working very well.  I used the win2k driver using the "standard" Ndiswrapper install scripts.
Feisty even at this early stage is working very well for my basic needs.

---

### Post by the.eagle on 2007-03-06
Yes I had some confusing posts about this card too. I changed cards, but now I can't even get a post to work. 
basically the netgear china model has a lot of issues. Good luck

---

### Post by jacksonz123z on 2007-03-07
> **the.eagle said:**
> Yes I had some confusing posts about this card too. I changed cards, but now I can't even get a post to work. 
basically the netgear china model has a lot of issues. Good luck

Well the Netgear wg511v2 often works very well with Ubuntu, but nevertheless it has wasted a lot of my time!  I think a card with the Atheros driver is the way to go?

---

### Post by gradedcheese on 2007-03-07
> 
I think a card with the Atheros driver is the way to go?


Yes!  Marvell, Broadcom, and Realtek are on my "don't buy" list:
[http://andrey.thedotcommune.com/wireless.html](http://andrey.thedotcommune.com/wireless.html)

Atheros and Ralink will give you much better results.

---

### Post by koolkris on 2007-03-13
I kind of got mine to work. First thing I did was go to Source Forge and download the newest version of ndiswrapper. I followed the instructions contained in the tar.gz file to a t. I removed the driver I installed for my card, *sudo ndiswrapper -r <driver>*. Then, I reinstalled the driver, *sudo ndiswrapper -i <driver>.inf*, and rebooted my laptop. When it came back, the lights on the wireless card lit up for the first time! The only problem I have now is that it pulls a loop-back IP address of 128.0.1.1 and I cannot connect to any networks when I use WiFi Radar.

K

---

### Post by june.itech on 2007-08-20
I think every problem has been fixed with the Feisty release: just use the synaptic package manager to download ndiswrapper, then type ndiswrapper -i [filename.inf] and reboot (if it says the driver is already installed, uninstall it with ndiswrapper -r [drivername]). If it worked on my 5-year-old laptop, I guess it will work on yours, too ;)

---

