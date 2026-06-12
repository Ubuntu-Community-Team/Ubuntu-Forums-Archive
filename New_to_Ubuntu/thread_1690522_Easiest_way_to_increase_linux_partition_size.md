---
title: "Easiest way to increase linux partition size?"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by itsmoonsoo on 2011-02-18
Not so long ago I installed linux on my machine to dual boot Windows 7 and Ubuntu 10.10.  My original partition size I gave it is looking to be a bit too small as I've been primarily been using Linux lately.  

Just wondering what the easiest way is to increase the size of the Linux partition while taking away some space from the Windows partition as it has a lot of unused space.

Thanks in advance :)

---

### Post by fabricator4 on 2011-02-18
Use Gparted.  Gparted is on the live CD, just boot it up and select it from the System/Administration menu.

You'll have to boot from the CD anyway, as you can't resize a mounted and booted partion.

It might be helpful to defrag your windows partion first, and run disk checks on both partitions.  Logical file errors can really cause problems if you're moving partions around.

Of course you should back up any important data first.  When operating on partitions there's always the chance that it will go pear shaped and trash your data.

Chris

---

### Post by metalf8801 on 2011-02-18
The safest way is to use the partition software that is built into Windows 7 (Disk Management) to shrink your Windows 7 partition. Using the Windows 7 built in partition software will decrease the odds having problems booting Windows 7 when your done.


here are more instructions that should help
[http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/](http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/)

---

### Post by Megaptera on 2011-02-18
I used this method of sharing the space between Ubuntu & Vista - a share :
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

just another option to consider perhaps.

---

