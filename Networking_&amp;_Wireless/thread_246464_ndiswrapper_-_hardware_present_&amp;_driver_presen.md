---
title: "ndiswrapper - hardware present &amp; driver present still doesn't work"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by hygren on 2006-08-29
Hi

I've been trying to get my 3com 3crusb20075 usb 108mbit/s wlan card to work in ubuntu. Using ndiswrapper with net5523.inf (from 3com website) I get driver present and hardware present, both in program and in terminal:ndiswrapper.

In networking the card finds and identifies wlans in the surrounding but I can't connect to them. I'm using a simple wep-key but it won't connect.

Any ideas?

---

### Post by Richardson183 on 2006-08-29
](*,) 
Tell me about it, I can't seem to get my Linksys 802.11b Wireless card to work on Ubuntu Linux 6.06. It works fine on my other paritition. The other partition contains Windows XP Home Edition SP2. On Windows the wireless card works fine and I stil don't get it. Ndiswrapper says that the driver is present (WMP11). But I can't get on the internet wirelessly.

---

### Post by syzygy07 on 2006-08-29
Did you guy's blacklist your original preloaded drivers?<br>
Find your chipset, in my case it was a broadcom. Then<br>
<B>sudo gedit /etc/modprobe.d/blacklist</B><br>
Depending on your chipset, blacklist the default one:<br>
In my case I added <I>blacklist bcm43xx</I> to the configuration file.

---

