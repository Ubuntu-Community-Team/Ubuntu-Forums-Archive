---
title: "RT860 Newest Ralink Drivers won't compile under 2.6.26 kernel"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by krutoileshii on 2008-08-28
Here is a problem. at some point Ubuntu will move to a 2.6.26 kernel. at this point everyone with a ralink drivers for  rt2860 chipset will not be able to compile them. 
I managed to compile it after modifying the source based on what i was able to dig around online. but at the same time lost all support for any type of encryption.

This will be coming. at this point still trying to figure it out. Since 2.6.26 kernel is not used by most people yet it's hard to pin point the problem.

---

### Post by Crafty Kisses on 2008-08-28
You don't get any errors?

---

### Post by krutoileshii on 2008-08-28
No none what so ever.
Keep in mind this is on Arch Linux not Ubuntu.
First of it was a pain to find any info and getting it to compile as the 2.6.26 kernel is not as common yet.
on top of that it work fine without any encryption.
Also the same driver works on 2.6.24 2.6.25 kernels just fine.
if you are willing to help with figuring it out let me now. I'm not that proficient at linux yet and especially debugging it.

---

### Post by krutoileshii on 2008-08-28
There is nothing in messages except it's normal output. no errors.
partly because before compiling it i removed some logging otherwise it would print 20 stupid messages every 5 second and load the system.

---

