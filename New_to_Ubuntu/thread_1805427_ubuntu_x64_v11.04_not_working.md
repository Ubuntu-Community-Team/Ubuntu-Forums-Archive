---
title: "ubuntu x64 v11.04 not working"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by nadsjinx on 2011-07-16
hi, this is my first post and my first time with ubuntu so pls bear with me...

i just bought an laptop, the HP Pav G4 1115TX, core i5 2410, 4gb mem, ATI™ Radeon 6470HD vcard...

i want to try ubuntu so i downloaded the x64 11.04 version but its not working...it just show a black screen and does nothing after the laptop boots up...i downloaded and burned it 3 times just to be sure and same thing happens...i dont know if its the installer(i downloaded from torrent) or the laptop is at fault.

i downloaded the version 10.04.2 just to be sure and it works fine. i want to install ubuntu but if possible i want the latest version so i wont have to upgrade/update later. so please help with the 11.04 installer.


also ive been reading about partitions and i've read about the need of creating 3 partitions(root, swap and home). is this really necessary or will i get away with a single partition(i read that swap can just be a file)?

thanks in advance!

---

### Post by wildmanne39 on 2011-07-16
Hi, you can use a single partition, but it is better to have a root, home and swap.

1. Separate home makes it is to keep your files when you reinstall or upgrade to a new version.

2. Swap is needed if you do not have enough memory, also you have to have swap ti hibernate or put your system to sleep.

3. To get past the boot issue so you can install your video driver look at this link.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by nadsjinx on 2011-07-16
Thanks for replying. 

After reading the article, I decided to stick with the v10.04.2 since it seems that the newer versions will need more research and testing for me to use. Im just gonna get acquainted with the one that works first before going for the later versions...


 not on topic: so the root partition will contain the system? how big will i make it? will 1 or 2 gb root partition do? and the rest make it home partition?

---

### Post by 3rdalbum on 2011-07-16
Root should be 10 gigs if separate. I'd suggest just having one partition with root and home (Ubuntu's installer preserves the home when you do a reinstall even if home and root are the same partition) and then another partition for swap that is slightly bigger than your RAM. The Ubuntu installer does this by default anyway so don't bother messing around with manual partition sizes.

---

