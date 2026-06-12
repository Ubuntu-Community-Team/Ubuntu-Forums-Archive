---
title: "Orinoco/Hostap in Feisty - Need assistance with installing"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by EdTheUniqueGeek on 2007-08-16
I have a Dell C400 with a Truemobile 1150 wireless mini-PCI I would like to get working with a secured access point, particularly using WPA.
Could someone please assist me with get rid of the Orinoco drivers and use the Hostap instead?
I'm sort of a amateur to Ubuntu but I can get around a little bit in Linux and command line.
Thanks for you assistance in advance.

---

### Post by EdTheUniqueGeek on 2007-08-17
Bump

---

### Post by EdTheUniqueGeek on 2007-08-17
Here is what I have attempted so far without any assistance.

I've installed all the Hostap packages from Synaptic Package Manager. I've created a blacklist file in the following directory:

/etc/modprobe.d/blacklist-wlan

In that file I blacklist the Orinoco drivers and prism2.
All of this doesn't seem to have worked. I **lshw** and I still see the Orinoco drivers listed in my eth1.
What am I missing or doing incorrectly?

---

### Post by markonhismobile on 2007-08-18
I have also been hunting around for a suggestion on how to get this working as I have recently got hold of an old Tecra 8200 and after much hunting around have established that the Orinoco drivers don't support WPA!

I followed the instructions on here:[http://ubuntuforums.org/archive/index.php/t-192050.html]("http://ubuntuforums.org/archive/index.php/t-192050.html")

I installed hostap-utils and blacklisted all the modules mentioned on that post and after a reboot my WLAN card doesn't even show up now! I'm going to carry on working at this as I'm sure Hostap could be the way to go I just need to find out how to load it to control the card!

---

### Post by Corgan on 2007-08-18
I'm having a very similar problem.

I have an AWN-8030 card from Adaptec which loads using the orinoco driver. In searching a database of linux-supported cards, it is said that, officially, this card is fully supported by hostap. 

In attempting to blacklist the Orinoco, I too wind up with no recognition of the card in the networking tools. If anyone could help in instructing me how to suggest, force, or swap the drivers please do.

Best of luck to those who posted before, as well.

---

### Post by EdTheUniqueGeek on 2007-09-11
I'm revisiting this.
Anyone have any information on this?

---

### Post by EdTheUniqueGeek on 2007-10-05
I guess I should consider this dead.
Does anyone, at least, know if any of the wireless problems so many people encounter with Ubuntu, and Linux in particular, will be fixed in Gutsy when it is released this month?
I would really, really love to get my wireless working on my laptop in Ubuntu. I've been reluctant to use Windows until I can find a wireless solution in Ubunutu.

---

