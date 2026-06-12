---
title: "P5B-E ethernet driver??"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by wparsons on 2007-04-11
I just finished installing Kubuntu 6.10 x64, and can't find an ethernet driver anywhere.

I've searched a few things on this site, but didn't find anything quite the same.  I've found info on a P5B deluxe, but my onboard ethernet on the P5B-E is different than the dual gigabit LAN's on the deluxe board.

Is there a driver anywhere, and if so, where?

I looked in the network connections, and the only interface I have is the loopback(127.0.0.1).

Any help would be greatly appreciated!!

---

### Post by chili555 on 2007-04-11
We'd like more information. What does```
sudo lshw -C network
```tell us about your ethernet card?

---

### Post by wparsons on 2007-04-11
Here's what it says:

* network UNCLAIMED
description: Ethernet controller
physical id: 0
bus info: pci@03:00.0
version: b0
width: 64 bits
clock: 33mhz
capabilities: bus_master cap_list
resources: iomemory: ff8c0000_ff8fffff irq:10

all I gather from that is that its detecting my card, but has no idea what it is or what driver to try.

---

### Post by chili555 on 2007-04-11
Wonderful, it tells us nothing useful.

Check here: [http://www.linux-tested.com/results/asus_p5b-e.html](http://www.linux-tested.com/results/asus_p5b-e.html) especially this: > The On-Board Attansic L1 Gigabit Lan chip were not detected by normal install, must get driver file atl1-x-x-x.tar.gz then setup itThen check here: [http://sourceforge.net/project/showfiles.php?group_id=184921](http://sourceforge.net/project/showfiles.php?group_id=184921) I would try 2.0.6.1, since  the others seem to be built for kernel 2.6.19 and 2.6.20. Edgy (6.10) uses 2.6.17.

Whether this will work in x64 is anyone's guess. You may be a trailblazer. Post back if you need more help.

---

### Post by wparsons on 2007-04-11
Thanks for everything so far! I'm gonna boot back into linux, and hopefully post again from it!

---

### Post by Monteaup on 2007-04-13
I used the drivers from the Asus CD. Works fine for me.

You need to install the kernel-sources. Then there will be a bz2 file in /usr/src

unpack it with "tar xvfj linux....." 
then link this dir to linux in the /usr/src. "ln -s linux-sourc.... linux"
then in the attensic/src dir a make install thats all.

---

### Post by wparsons on 2007-04-13
I didn't even think to try the Asus CD.. Thanks for the heads up!

---

### Post by shoq on 2007-04-14
Gentleman

I a total Linux Newbie.  I have the same Asus Motherboard AND L1 ethernet onboard.  I am completely lost

I downloaded the L1 linux driver from Asus, and its readme tells me i must to a Make Install.  But then i learn (from another thread on this board that i posted) [http://ubuntuforums.org/showthread.php?p=2453378#post2453378](http://ubuntuforums.org/showthread.php?p=2453378#post2453378)

that i need a bazillion downloads to get the "build essentials"  

This step is not mentioned here in this thread, so I am wondering if I am missing something

Could someone give a total novie to linux, a step by step tutorial in how to get this Attansic Ethernet working in Ubuntu?  I know how to do almost nothing, but open a terminal window. Beyond that, I am clueless

I would happily rewrite your instructions for other novices like me, if it needs touch up. 

Thank you

---

### Post by Monteaup on 2007-04-17
Yes you need the build essential packages. Without you wan't be able to compile something. Thats the first thing I do after ubuntu install, I forgot to mention it. 

In the other thread you need to install the linux-headers. But it looks like the driver needs to rebuild some kernel objects. So you need the linux-source.

After make install the module will be always loaded. Then you can configure your network card like in windows. Using System->Administration->network

---

