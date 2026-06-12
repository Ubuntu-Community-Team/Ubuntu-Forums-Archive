---
title: "Wireless not connecting"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by hidamari no tami on 2005-10-25
Hi,

I posted this in the Hoary Networking forum, but since I now am running Breezy and am having the same problem, I thought I'd post it here as well.

Basically, my problem is outlined here: [http://ubuntuforums.org/showthread.php?t=78546](http://ubuntuforums.org/showthread.php?t=78546) , but in short, I can connect to my internet with a wired connection using a Xircom RBE-100 that I borrowed, but I can't connect to the internet wirelessly (tired two cards: WG511 and WPC55AG). Neither card will scan either.

If it helps, I'm running WEP 128-bit encryption, but I also tried connecting with the WEP off to no avail.

I hope someone can help, this is driving me crazy! Thanks in advance!

---

### Post by knappen on 2005-10-25
Have you installed the driver with ndiswrapper?

---

### Post by hidamari no tami on 2005-10-25
I didn't use ndiswrapper since back when it was working properly all I had to do was copy the "isl3890" file into the /lib/hotplug/firmware/folder ...this was under Warty though. In Hoary, it just worked off the bat when I installed the first time, so I didn't touch anything, but all of a sudden one day it just stopped. Have yet to get it working under Breezy though.

---

### Post by hidamari no tami on 2005-10-26
I just tried ndiswrapper (there were two inf files in for the windows drivers, so i tried both), and it still doesn't seem to work. 

I did notice something else though when I set my card to auto instead of managed (sudo iwconfig eth0 mode auto); it seems that in auto mode I can scan for networks, but instead of the usual 10+ available networks, there's only one and it's ad-hoc instead of master (I know it shouldn't be ad-hoc since it's my network). Any ideas?

*EDIT* - I should have mentioned earlier that I can ping the loopback interface (both before and after installing ndiswrapper)

---

