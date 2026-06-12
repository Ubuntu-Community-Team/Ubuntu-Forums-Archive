---
title: "Connection problems"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by Tanuvein on 2006-10-08
I just installed Ubuntu Linux on my compaq laptop, a system I ordered about 2 months ago and am now replacing Windows XP. It seems to work fine, except networking.

It does not even allow by wireless internet to pick anything up. It shows an eth1 for a wireless card, but, at least on windows, it always showed up as WLan.

Also, for the actual ethernet physical connection, its shakey at best. I tried wiring it to both the router and directly to the modem, but I get the same results on both. Minimal connectivity with speeds that dial up would laugh at (about 600 b/ps), with frequent connection drops. I tried automatix, but I can't get the updates to download as it drops for all of the large ones, and it won't install what I have managed to download.

I'm not sure what to do, any help would be appreciated. This is my first time using linux and I've picked up on it fast, but this is frustrating and I can't find an answer. I was thinking of making my desktop linux too, but not if I can't get this working ](*,)

---

### Post by dolphinsonar on 2006-10-08
Try Wifi-radar.  If you can get it to download its pretty handy at automatically hopping on whatever wireless network is available with minimal configuration.

---

### Post by Tanuvein on 2006-10-09
I tried that, but it tries to use my eth2 card (which doesn't exist and isn't even on my network list) to scan with. Is there a way to fix that?

Also, someone said that, at least on a different type of linux with the same set up as me, they went into /etc/modprobe.d/blacklist in an editor, and put

#Broadcom Native Driver
blacklist bcm43xx

Would that help me? How do I do it? I'm kinda new to linux and I'm having a hard time learning since I can't get online with that computer.

---

### Post by Tanuvein on 2006-10-09
Ok, I figured that part out but it also didn't help. After doing some more searching on my particular card coupled with Ubuntu, it seems to be a problem within the latest Ubuntu versions. I stlil haven't found a fix. My card is the Broadcom 4318 "AirForce One 54g". If anyone knows a fix, I'd appreciate your help. I'm continuing to search as well.

At least I'm learning how to use Ubuntu, spending eight hours trying to fix this :P

---

### Post by wirelessmonkey on 2006-10-09
Sometimes learning is the most painful part... but you'll be proficient sooner than you think.

I have the same broadcom card as you on my laptop, I'll start up an ubuntu install and see if I can't help out a bit.


Good luck.

---

### Post by Tanuvein on 2006-10-09
Thanks :)

After some more working, thanks to a guide in this forum, I've managed to get the card tied to eth1, so it is now recognized and shows up fine. But its not getting a signal off of my router. I have no idea where to go from here. Tomorrow at school I can try the campus-wide wireless.

EDIT: The blue light showing the WLan is working is flashing, and if I type 'sudo iwlist scan', it shows my router. But the connection itself is still not there.

---

### Post by Tanuvein on 2006-10-09
Fixed it! I used a walkthrough I found on this site, blacklisting default driver, then ndiswrapping a custom driver plus fiddling around with some network settings. I then could turn it on, but it wouldn't pick up my router so I used the program the first person suggested and now it works! I've updated linux and used automatix :)

Thanks for all of your help guys. I feel like I've actually learned a lot from this.

---

