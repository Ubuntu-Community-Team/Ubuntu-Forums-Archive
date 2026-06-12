---
title: "wireless is super-slow compared to macOS partition | Broadcom BCM4331 | MBP 10,1"
date: 2018-10-01
forum: Networking &amp; Wireless
---

### Post by bennywas on 2018-10-01
Hiya! :KS

**Issue**
My  wireless connection on my new Ubuntu partition is so slow compared to  my macOS partition. Speedtest.com results from two different wifi  locations confirms this:
*(Location. Test: [COLOR=#a52a2a]Ubuntu result[/COLOR] [COLOR=#6699ff]macOS result[/COLOR])*
Public library. Ping: [COLOR=#a52a2a]52ms[/COLOR] [COLOR=#6699ff]9ms[/COLOR] | Download: [COLOR=#a52a2a]4.80Mbps[/COLOR] [COLOR=#6699ff]7.33Mbps[/COLOR] | Upload: [COLOR=#a52a2a]4.26Mpbs[/COLOR] [COLOR=#6699ff]7.36Mbps[/COLOR]
A local cafe. Ping: [COLOR=#a52a2a]24ms[/COLOR] [COLOR=#6699ff]30ms[/COLOR] | Download: [COLOR=#a52a2a]2.80Mbps[/COLOR] [COLOR=#6699ff]48.90Mbps[/COLOR] | Upload: [COLOR=#a52a2a]0.96Mbps[/COLOR] [COLOR=#6699ff]11.64Mbps[/COLOR]

I'm at the cafe now, and wifi *does* work albeit rather slowly, but trying to run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info") from terminal returns:
```
Resolving github.com (github.com)... failed: Connection timed out.
wget: unable to resolve host address ‘github.com’
```
So  I ran the script again while tethered to my iPhone (I mention this  because I'm not sure if it makes a difference for the data collected).  The results are here:
[http://paste.ubuntu.com/p/b9nCvHNgjN/](http://paste.ubuntu.com/p/b9nCvHNgjN/)

**Background**
This  is a MacBook Pro 10,1, with a macOS partition and an Ubuntu 18.04  partition. When I first installed Ubuntu last week, I had major trouble  just figuring out how to get the wifi functional, but I eventually  solved it by following [this advice]("https://ubuntuforums.org/showthread.php?t=2391053&page=2")  to install the "firmware-b43-installer". Now that I can connect, the  next step is figuring out how to speed up my connection to comparable  levels to my macOS partition.

I'm new to Ubuntu and relatively  new to command line, FYI. I'd appreciate any help on starting to diagnose or  possibly fix this problem! Thaaaaaaanks

---

### Post by bennywas on 2018-10-05
Should I have posted this somewhere else? Did I include too much info or not enough? Did I use the wrong tags/descriptors? jw why this post is getting no love... :(

---

### Post by praseodym on 2018-10-06
Try the fixed channel "11" in your router. Channel 1 is crowded, higher than channel 6 will cause interferences with 6. Set the bandwidth in your router to 20MHz instead of 20/40 MHz.

---

### Post by bennywas on 2018-10-06
Hi praseodym!! Thanks for responding. I actually *don't own* a router. My question is about the wifi I connect to on a daily basis, which is public / cafe wifi.

Besides, even if I could approach the manager of every cafe or public library I enter to ask if I could please mess around with their router, that doesn't seem like the real solution. As I said, **the wifi connection works fantastically on my macOS partition _at the same location_, whereas the Ubuntu connection is crappy. **In my original post, I cited two identical locations where I sat down to compare the wireless speeds of each partition at the same time of day. I've since been to several more public wifi locations, and comparing the signal strength across the two partitions/OS's, the results are the same: wherever I go, my Ubuntu partition's wireless connection is significantly slower than my macOS partition's wireless connection.

What do you think could be causing this? How can I diagnose/remedy it?

---

