---
title: "EasyBCD"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by TimEnid on 2010-08-01
so i am dual booting w7 and ubuntu. i installed grub 2 to my w7 hd using EasyBCD. now i am ready to remove windows 7 completely. If i installed Grub 2 to the ubuntu hd, will my pc boot right into ubuntu with no issues. If this is not the best method, how should i go about deleting windows 7, where the grub is installed. I also plan to format the w7 hd and use as extra space. any suggestions?

---

### Post by Zimmer on 2010-08-01
I'm not sure you 'installed GRUB2 ' using EsyBCD. EasyBCD is a bootloader for Windows systems that will enable you to boot other OS's.

I have EasyBCD installed on my Vista partition. It has an entry that points to GRUB which is NOT installed on the MBR of my drive, but on the Ubuntu partition itself.

I reckon if you use a LiveCD to install GRUB2 to the MBR of your drive it will probably recognise the Win7 install too.

If you then remove the Win7 install (by repartitioning/formatting whatever..) then you will need to update GRUB again to remove the Win7 entries from the GRUB menu...

Check out the GRUB pages on the official and community documentation pages for the commands etc.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
and
[http://members.iinet.net.au/~herman546/p20.html](http://members.iinet.net.au/~herman546/p20.html)

---

### Post by TimEnid on 2010-08-01
so say im logged on to my ubuntu os, and i can see my w7 hd. if i format the drive, everything is erased. can i then install grub/boot loader on my ubuntu hd.

---

### Post by louieb on 2010-08-01
Get and run the [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/") it will show your drives and what boot loader is installed where. and other good stuff.

If you have questions put the output in your next post - it removes the guesswork. 

If I had to guess - Grub is already installed on the Ubuntu drive - you'll just need to change the boot order to boot straight to Ubuntu.

---

