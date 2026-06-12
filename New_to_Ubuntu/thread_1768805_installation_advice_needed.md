---
title: "installation advice needed"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by spillage2 on 2011-05-27
Hi,

I give up with my last attempt at installing a separate home so its time to start again.

I would like some advise if possible about which drives to use and how..

I have 

sata

2 x 640gb
1 x 40gb

what would be the best way to utilize these drives so I have room for anything I download and room for a separate home partition without running out of room to quickly..

Cheers,

Spill

---

### Post by 3xp10r3r|X13 on 2011-05-27
I would recommend to partition your 640 gb drive manually during the installation process. So  the thing you should be doing is creating several partitions, such as /, /home, /boot and swap. Assign about 240 gb to your system "/" (primary partition, for the rest select logical partition), about 390 gb to "/home", 500 mb to "/boot" and depending on your ram something to "swap". (4 gb ram so 4 gb to 8 gb should be more than enough)

--> you can use the other drives to simply store things on as well, but as you've got 390 gb available in your home directory, that's not really necessary. (use the second 640 gb drive - it will act as an external hard drive - to store really big files on - so much space)

Any questions?

---

### Post by trozamon on 2011-05-27
Umm... /home on one of the 640s, everything else on the other 640?
 
That way your home directory has over 600GB of space.

---

### Post by spillage2 on 2011-05-27
ok thanks for the input..

I take it the 40gb drive would be too small to put / /boot and swap on with /home on another drive?

---

### Post by trozamon on 2011-05-27
Actually, you could probably put everything except /home on the 40, assuming you don't install a ton of software.

---

### Post by 3xp10r3r|X13 on 2011-05-27
true...but lots of people, including me, just love to install tons :D

---

### Post by fballem on 2011-05-27
Another option to consider would be to use LVM. Do do this, you will need to use the Alternate installation CD

Some links that might prove useful:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

I use LVM on my desktop, which has a 500 GB harddrive and a 1 TB harddrive. I have configured a single LVM that includes both - less a small piece (500 MB) as the /boot.

Hope this helps,

---

