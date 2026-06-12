---
title: "Here's the my gparted and win7 windows management screen shot.."
date: 2010-06-24
forum: New to Ubuntu
---

### Post by lemo1226 on 2010-06-24
he unshrinked partition was also turned to unknown..
here's my partitions of 320 hd
G:    87.88 GB -resides Games and most of the programs installed.
D(2nd windows)(D:smile: 30GB=resides data files.
E: data=also contains data
windows C:- My Win7 OS





Heres what wubi log says..

06-19 19:36 DEBUG  Distro:   checking whether C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp is a valid Ubuntu CD
06-19 19:36 DEBUG  Distro:     does not contain C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp\casper\filesystem.squashfs
06-19 19:36 DEBUG  Distro:   checking whether C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp is a valid Ubuntu CD
06-19 19:36 DEBUG  Distro:     does not contain C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp\casper\filesystem.squashfs



..that was just the part of a log..thanks evryone..

---

### Post by lemo1226 on 2010-06-24
> **lemo1226 said:**
> he unshrinked partition was also turned to unknown..
here's my partitions of 320 hd
G:    87.88 GB -resides Games and most of the programs installed.
D(2nd windows)(D:smile: 30GB=resides data files.
E: data=also contains data
windows C:- My Win7 OS

the unshrinked partition was also turned to unknown..
here's my partitions of 320 hd
G:    87.88 GB -resides Games and most of the programs installed.
D(2nd windows)(D:smile: 30GB=resides  data files.
E: data=also contains data
windows C:- My Win7 OS



Heres what wubi log says..

06-19 19:36 DEBUG  Distro:   checking whether C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp is a valid Ubuntu CD
06-19 19:36 DEBUG  Distro:     does not contain C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp\casper\filesystem.squashfs
06-19 19:36 DEBUG  Distro:   checking whether C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp is a valid Ubuntu CD
06-19 19:36 DEBUG  Distro:     does not contain C:\Users\emachine\AppData\Local\Temp\pylCEB.tmp\casper\filesystem.squashfs



..that was just the part of a log..thanks evryone..

---

### Post by wilee-nilee on 2010-06-24
I gave you the answer already you have 4 primary partitions, that is the maximum allowed. You will have to remove one, and they are all pretty much full, so you will have to either get a larger internal hard drive or a external for the data that is removable or movable to remove a primary and let Ubuntu install to a extended.

---

### Post by lemo1226 on 2010-06-25
thanks sir,so the maximum allowed partitions in ubuntu was 4?or its the limit?what do you mean b ubuntu cant install in NTFS?so theres no other way in installing it in wubi in win7?

---

### Post by wilee-nilee on 2010-06-25
> **lemo1226 said:**
> thanks sir,so the maximum allowed partitions in ubuntu was 4?or its the limit?what do you mean b ubuntu cant install in NTFS?so theres no other way in installing it in wubi in win7?

The maximum of primary partitions on any HD are 4.
If your trying to do a wubi install you do it from the live windows enviroment and a file is made for Ubuntu that is in the NTFS partition. You wouldn't be shrinking or building partitions with a wubi install. 
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

What your actually trying to due is confusing give a better description.

I think if you post the bootscript in my signature in code tags it will be helpful to see whats going on.

---

### Post by Chame_Wizard on 2010-06-25
Remove one of the primary partition and do a clean install of Lucid Lynx or Karmic Koala.

---

