---
title: "Can't get online with RTL8139 in Compaq Laptop"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by agentphish on 2008-07-20
Greetings, 

I have just installed Ubuntu 8.04 on my Compaq C762NR laptop. 
Installation was effortless and easy, like OS X. But now I'm so lost. I pioneered getting this laptop working for XP, and wrote a whole guide for doing so. I have had little luck with osX86 on it so I thought I'd give Ubuntu a try.

This is my first experience w/ Ubuntu. I want to love it, but so far, I can't get on the internet via Wired ethernet, which means I can't follow the directions I have found here and elsewhere to get my Atheros wireless card to work.

My wired card doesn't seem to be scoring an IP address from my router. I even tried manually configuring it, but it doesn't seem to make a difference. There's still no internet connection. At this point I set it back to "Roam" after reading that should set it up automatically, but it has done nothing and I am unable to get online.

Can anyone help me out? The internal wired card is listed as a RealTek RTL8139/810x Family Fast Ethernet NIC. My router is a Linksys WRT54GX.


Thanks so much

---

### Post by agentphish on 2008-07-20
Bah...I searched for RTL8139 here and found the main realtek thread about telling winblows to enable WOL and it's working now...

Strangely I had to switch ports on my router before I got it to work. I have no idea why that would be.

Dual booting Ubuntu and Vista. Now to get the Atheros WiFi working.

---

### Post by thegitksan on 2008-09-04
> **agentphish said:**
> Bah...I searched for RTL8139 here and found the main realtek thread about telling winblows to enable WOL and it's working now...

Strangely I had to switch ports on my router before I got it to work. I have no idea why that would be.

Dual booting Ubuntu and Vista. Now to get the Atheros WiFi working.

Can you explain what you just said above in English please? I have no idea what "telling winblows to enable WOL" means, for example. Also, if you changed ports,what was it when you started and what was it when you got it working?

I've got an RTL8139/810x fast ethernet card as well, with similar zero luck figuring out where to look for an answer. Where is the realtek thread, for example? 

Thanks!

---

### Post by lilmale1 on 2008-09-04
I cant get my rtl8180 to work.
I installed manually the driver and wicd doesn't work with this card till I install wpa supplicant because something with the compadibitlity. it would be nice if someone like u can help me 
cuz I don't get it....of how to install all that and beside i don't know how to configure my card after it reads in wincd.

:popcorn:

---

### Post by thegitksan on 2008-09-05
Not sure I'm the right person to be asking for help - I am asking for help myself.

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lshw -C network
```

---

