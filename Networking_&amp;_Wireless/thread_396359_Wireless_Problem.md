---
title: "Wireless Problem"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Krymore on 2007-03-29
I just installed Ubuntu 6.10 and apparently I was one of the lucky few with a special wireless card that requires lots of headaches.  I have a BCM4309 on a Latitude D610.  Most of the different HowTo's I've seen are all different 43xx's and I'm not sure if there's a difference but none of them seem to work.  I downloaded the two ndiswrapper things off the Ubuntu cd and got some gui tool for it that I found in a random HowTo.  I downloaded the driver from the Dell website and loaded the bcmwl5.inf thing but it says the hardware isn't present.  I apologize in advance for being a complete noob, but can anyone point out what I should be doing differently?

---

### Post by bkeithly on 2007-03-29
You might have the wrong driver.

Can you see the card when you do:

lspci?

it should be listed.

or do:

lspci | grep bcm

See what that gives you.

If you can see the card then it is time to start trying other drivers.

Also you need to black list the existing bcm43xx.

vi /etc/modprobe.d/blacklist

add

blacklist bcm43xx

---

### Post by Krymore on 2007-03-29
lspci shows:

03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

That's what I'm looking for right?
I already added "blacklist bcm43xx" to the end of that file.

---

