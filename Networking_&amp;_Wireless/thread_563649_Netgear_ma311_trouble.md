---
title: "Netgear ma311 trouble"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by goffy59 on 2007-09-30
I went to a forum talking about how to install this card under slackware but it did not work. I was aware they are 2 different things, but I thought some of it could help me. I also tried ndiswrapper looking about about 3 different tutorials but my results were not what they described. Anyhow, the computer is in my room currently, but if the wireless wont work; its pointless. Because it goes outside in my living room. I wanted to show my parents the power of ubuntu. Anyhow my luck has ran out and I am stuck. I'm going to undo what the slackwhere tutorial told me to do and heres the link to it [http://justlinux.com/forum/showthread.php?t=132847](http://justlinux.com/forum/showthread.php?t=132847)

Before I did any of this I did try to get it to work by just using what Ubuntu set up. It would attempt to connect and then soon switch back to wire connection. I did it by left clicking the tray icon and chose connect to other wireless network/etc. On windows I had to change the channel so it would connect to one of my routers but I dont see how to do this on ubuntu. I have 2 of these cards, and they both use the same channel by default. The one on windows connects, the one on Ubuntu doesn't. Anyhow, I undid everything I explained about about the slackware tutorial and ndiswrapper. I'm pretty much confused now on which to use. It would be nice if there was something like Envy but for wireless networking.
I also looked at gtkwifi but wasnt able to open it because it says I dont have a wifi card installed, when even the hardware information on Ubuntu says I do. And it gives me the option to use either, its just the WIFI does not connect to my WGT624 router(netgear)

-jack

Thanks in advance.

---

### Post by goffy59 on 2007-09-30
I had a question, how do I change  (wlan0 to eth0), I'm not sure what they mean. I'm happy its already supported but it wasn't working... and still isn't. I'm reinstalling Ubuntu right now. I have an on board network card, and its name is either eth0 or 1. Anyhow what do I do if I have a wireless and wired connection? Forget what I said before I alway make the mistake of giving up when theres more light to be shed.
I reinstalled because when I opened module.conf it was blank. People told me this is where I would change this setting. I booted up just now and module.conf is still blank.

Heres what Ubuntu wiki had to say about my card:
Netgear
	

MA311 (PCI)
	

Prism 2.5
	

Detected as eth0 and started working after modules.conf was edited (wlan0 to eth0)

---

### Post by goffy59 on 2007-09-30
Ahhh the irony. I feel like such an idiot. When I first installed Ubuntu my wireless card would not work WHAT SO EVER! Now that I reinstalled it seems to work like a charm. ARGG This is the 3rd time I've done this on this forum. Make a post and the problem fixes it self. I'm such a Linux newbie! I cant think of anything I did wrong to make it not work on the first install. I literally did NOTHING to any networking config/option. I left it all the same and now it decides to work! I'm sorry for my ignorance. Ignore my post!

Thanks!

---

