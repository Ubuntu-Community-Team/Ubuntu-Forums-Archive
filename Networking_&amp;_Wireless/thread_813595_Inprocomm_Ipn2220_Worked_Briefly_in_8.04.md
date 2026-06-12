---
title: "Inprocomm Ipn2220 Worked Briefly in 8.04"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by mmlowe on 2008-05-31
First off, I'm a complete noob to any sort of Linux.  I've got an Acer TravelMate 2303WLCi and I just installed 8.04 yesterday (after an incident with Norton PartitionMagic resulting in a fully 'unallocated' hard drive).

Anyway, my friend with the Linux disks was a little help explaining where to start.  I was able to get my wireless working yesterday, specifically with the help of ndiswrapper and these links:
[_Sicksand_]("http://sicksand.net/post/32208741/inprocomm-ipn-2220-wireless-lan-adapter-problem-in")
and
[_Phil Dawson_]("http://phildawson.tumblr.com/post/22267163/how-to-enable-linksys-airconn-inprocomm-ipn-2220")

My computer has a big wireless 'activity light' on the front that is also an on/off switch.  Once I ran the steps, it connected fine, and would fire up before the operating system even finished loading (light blinking).  I did a restart or two, but never a true shutdown.

I was pretty proud of myself, and thought "This linux stuff isn't so bad, maybe I'll keep it."  Today, when I turned it on, no light, no wireless.  I've spent the last few hours googling the problem and found an [_old forum_]("http://ubuntuforums.org/showthread.php?t=586414&page=2") where someone else mentioned a similar problem with 7.10.

By now, I've got 3 or 4 different drivers downloaded (only one will install at a time) and have manually downloaded ndiswrapper 1.53 and used the synaptic for 1.50.  I don't know which one is now in place.

I could try [_this guy's advice_]("http://ubuntuforums.org/archive/index.php/t-179270.html") but his linked download doesn't work for me.

Any advice would be appreciated, and help lead me towards not finding my old system restore disk (XP) when I get home next week.  Thanks!

---

### Post by mplexus on 2008-05-31
just a hit-in-the-dark (or something to that effect):

you could try to disable the acer-acpi module and see if anything
good happens (which i doubt but still.. : )

sudo gedit /etc/modprobe.d/blacklist

and add at the end of the file this:

blacklist acer_acpi

then reboot. I apologize in advance if this just wastes your time
- in which case don't forget to remove the added line.

---

### Post by mmlowe on 2008-05-31
No apologies...  I've wasted plenty of my own time trying to figure this out.  Any advice is appreciated.  I'll see if it helps and let you know (I'm on another computer right now).  Thanks.

---

### Post by lunetter on 2008-06-23
Hi, dont know if you still have problems with installing the driver... my girlfriend's computer has the same wireless and I had no problems with installing the correct driver so this might help you.

1. I followed the advice at Ubuntu documentation for installing windows wireless drivers:

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

2. Then I could see wireless working but whenever I restarted the computer it was gone and had to repeat the steps again. To avoid that I opened /etc/modules as sudo

by typing in Terminal: gksudo gedit /etc/modules

and added "ndiswrapper" as the last line.

After that the wireless showed up also after the restart.

---

### Post by mmlowe on 2008-06-23
Thanks for the advice, I gave up on it after successfully getting it to work for about 3 days straight.  ](*,)  I've gone back to the dark side with XP :evil:.

---

