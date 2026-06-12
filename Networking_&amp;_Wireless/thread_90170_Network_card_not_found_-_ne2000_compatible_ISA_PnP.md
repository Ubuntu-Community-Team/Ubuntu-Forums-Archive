---
title: "Network card not found - ne2000 compatible ISA PnP"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by olavi on 2005-11-14
I have a ne2000 compatible ISA PnP network card and Ubuntu does not find it. It works perfectly with Windows and Gentoo Linux (modprobe ne).

How can I make it work with Ubuntu Linux?

I have two similiar cards, so I'm not buying new ones. :smile:

---

### Post by olavi on 2005-11-14
Actually I found something. Whoops.

[http://www.petersblog.org/node/657](http://www.petersblog.org/node/657)

Missed the console in the installer. I wonder why he had to use io and irq flags, and I didn't with Gentoo. :confused: 

I'll try that and post the results.

---

### Post by olavi on 2005-11-14
This is what I did:

Install stage:

1.1: Open console

1.2: modprobe ne

After logged on to Ubuntu:

2.1: Open console

2.2: sudo modprobe ne

2.3: System management -> Network settings -> eth0 properties -> (choose the right settings)

And now I'm writing this. :D 

I wonder do I have to repeat the stages 2.x after reboot...

---

### Post by Lambert on 2005-11-14
You can add ne to /etc/modules.conf (I believe that's correct) so it loads at boot.

---

### Post by olavi on 2005-11-14
Thanks! It's actually just /etc/modules.

Now I have a legacy ISA device working perfectly. :)

---

