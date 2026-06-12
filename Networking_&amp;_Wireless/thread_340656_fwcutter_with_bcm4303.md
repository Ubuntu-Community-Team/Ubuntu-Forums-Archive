---
title: "fwcutter with bcm4303"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by fugative on 2007-01-17
I have a HP Pavilion zv5ooo series running edgy. The built-in broadcom 4303 is recognised but won't run, this I understand is down to the lack of firmware in the kernel for it. (although the drivers are pre-installed in edgy). I had it running with ndiswrapper but for some reason it made the laptop run like a commodore 64 with XP so i decided to go back to the native drivers. I tried the fwcutter route but no luck, no light, no connection. I found the firmware files  from [this site]("http://us.ubuntu.cafuego.net/dists/edgy-cafuego/") but there are no instructions and the laptop has no internet so i can't use that method. 
If anyone can help me i'd be most appreciative.

---

### Post by Richard Kut on 2007-01-18
Hello fugative! I would encorage you to use ndiswrapper instead of fwcutter, since fwcutter can only handle 11 Mbps whereas ndiswrapper can handle 54 Mbps.

If you are still determined to go with fwcutter, then have a look here:

[http://doc.gwos.org/index.php/BroadcomWireless](http://doc.gwos.org/index.php/BroadcomWireless)

I hope that this helps. Good luck!

---

### Post by fugative on 2007-01-19
My card is a 802.11b so it only does 11mbps anyway and as i pointed out ndis made my machine run sloooow. get these things sorted out and i don't really mind if i use a ham sandwich.

---

### Post by Richard Kut on 2007-01-21
OK, so have a look at this link which deals with fwcutter:

 [http://doc.gwos.org/index.php/BroadcomWireless](http://doc.gwos.org/index.php/BroadcomWireless)
 
 I hope that this helps. Good luck!

---

