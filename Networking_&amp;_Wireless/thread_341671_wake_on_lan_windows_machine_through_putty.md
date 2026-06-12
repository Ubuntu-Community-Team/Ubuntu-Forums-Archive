---
title: "wake on lan windows machine through putty"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by tumandro on 2007-01-19
Hi guys/gals,

I'm relatively new to linux, but being at CNSA major I decided to start taking steps on my own to make sure that I was prepared for my classes later in life so I decided to make a Linux router. My friend had his own so he helped me set it up, and taught me how to do a few things like accessing your files remotely from say my school network using ssh in putty.

I don't want to leave my computer on however during the day and wasting power if I'm not going to use it so I've been trying to figure out how to WoL my computer through the linux router using putty. Does anyone know how I can go about doing this? My desktop is running windows xp.

---

### Post by tumandro on 2007-01-19
anyone?

---

### Post by dannyboy79 on 2007-01-19
all you had to do was look it up in gogle. Gogle is your friend. I spent less than 5 minutes and found your answer immediately. Hope this works for ya:
[http://ahh.sourceforge.net/wol/wol.html#SEC2](http://ahh.sourceforge.net/wol/wol.html#SEC2)

also, here is some info on getting Wake on Lan to work in WIndows XP Pro: 
[http://www.anycpu.com/projects/diypc/GraniteBay/OS.htm#WakeOnLAN](http://www.anycpu.com/projects/diypc/GraniteBay/OS.htm#WakeOnLAN)

---

### Post by Iowan on 2007-01-19
> **tumandro said:**
>  I decided to make a Linux router. [http://www.freesco.org/]("http://www.freesco.org/") 
Here's one you should investigate - just to see how much can be done with minimal hardware.

---

### Post by tumandro on 2007-01-21
i actually already have one set up with ubuntu server running. I just need to find out how to get the wake on lan working through the router.

---

### Post by dannyboy79 on 2007-01-23
Again, I found this within a gogle search. Gogle is your friend.



Note that WOL operates over UDP, not TCP.

So make sure you have port 9 UDP being forwarded, not port 9 TCP. 
Reply to This &#8226; # 
Wake a PC from a Mac - By: TimBonnici on Fri, Jan 21 '05 at 5:11PM PST 
Online tools
By: pheed on Fri, Jan 21 '05 at 6:38PM PST 
If you have internet access there are online tools available for this as well. It will even work through a router too. Make sure you have port forwarding configured appropriately. The beauty of this is that you can wake up a sleeping machine even if you're not on the sam LAN.

---

### Post by glennric on 2008-02-13
> **dannyboy79 said:**
> Again, I found this within a gogle search. Gogle is your friend.


What is gogle?  I understand typos, but when you repeat it this many times it is probably not a typo.

---

