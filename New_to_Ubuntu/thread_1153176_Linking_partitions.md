---
title: "Linking partitions?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Lowelife101 on 2009-05-08
Currently my pc only has the one hard drive and it's very small (120gb), i still think duel booting will be the best option for me but i was wondering if it's possible for me to partition my 1tb external hard drive that i have (without completely reformatting it), and link (i'm not sure if that's the right word) my windows partition on my internal hard drive with a partition on my external hard drive with all the windows programmes on (mostly video games but a few converter programmes so i can get downloads etc into a format kubuntu can handle) and do the same with kubuntu so i'd have a kubuntu internal partition with a kubuntu external partition with all it's programmes on.
 
According to the ITC teacher at my college it's entirely possible to do that with window's however the kubuntu partition on the external harddrive will still be accesible through windows when i boot windows up, in his words "providing you don't put any windows stuff in there and just leave it alone you'll be fine, maybe name it kubuntu partition or something, the same goes for kubuntu you'll see the windows partition when kubuntu is booted up" 
 
Now i know most windows programmes allow me to install them pretty much anywhere so getting them onto the external hard drive partition is easy, my question is will programmes for kubuntu automatically be put on my internal hard drive and will go nowhere else or is it possible to get them to install onto the external hard drives partition?

---

### Post by cariboo on 2009-05-09
It depends on how you install Ubuntu/Kubuntu. If you do a wubi install, you can pretty well install it anywhere, either on your internal drive or your external drive. If you install on a seperate partition you will have to set grub up to boot from your external drive, that way if you start your computer with the external unplugged you can still access windows.

Windows cannot access ext3 partitons without help, you will need one of the programs on [this]("http://www.howtoforge.com/access-linux-partitions-from-windows") page.

---

