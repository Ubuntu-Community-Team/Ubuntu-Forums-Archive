---
title: "How to dual boot W7 and 9.10 with two hd's?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-11-06
I have a computer with Windows 7 and would like to add Ubuntu to the machine. I'm getting another hard drive and was wondering how to set up the system:

1st hd (640GB with IDE connection): Windows 7
2nd hd (160GB with SATA connection): Ubuntu 9.10

And want Windows to boot first by default. I tried to look for some info or how-to's online, but I can't find quite what I need, so if you can point me to the right info. It'll be awesome!

Thanks!

---

### Post by H2SO_four on 2009-11-06
These might be helpful to you.  I have one hard drive for my OSes and another that is for storage.  Win7 is the first partition, followed by a couple incarnations of Ubuntu, swap space and blank partitions (big drive).  I left my Win7 alone and did a fresh install of 9.10 and when Grub was installed it recognized my Windows partition and everything went extremely smoothly.  

Hope your install goes well!!


[http://ubuntuforums.org/showthread.php?t=1195275&highlight=change+boot+order](http://ubuntuforums.org/showthread.php?t=1195275&highlight=change+boot+order)

[http://ubuntuforums.org/showthread.php?t=1285897&highlight=change+boot+order](http://ubuntuforums.org/showthread.php?t=1285897&highlight=change+boot+order)

---

### Post by sylvainrb on 2009-11-06
Thanks for the info!

I do have a question prior to setting up GRUB2. Can I just plug in the 2nd hd onto the motherboard, pop in the liveCD and 9.10 will prompt me which hd to install onto? Or is there prior set up I need to make in BIOS or something the like?

---

### Post by oldfred on 2009-11-06
If your BIOS lets you switch drives I would make the Ubuntu drive first. Some BIOS with mixed sata & pata do not make it easy to do that. While windows likes to be first the advantage will be that you keep the MBR of the windows drive intact and if in the future need to directly boot windows you can switch drives back. Ubuntu should find the windows instlal on the second drive and add a mapping command to make it think it is the first drive.
I like to have a operating system on every drive and the boot in the MBR of that drive so I can boot any drive just in case one dies. The system only boots from the first drive so that is the one that will control booting, windows does not make it easily to boot ubuntu but grub will boot just about anything.
Herman has a lot on dual booting in general, I have not seen much yet on your set-up, but the difference between versions is not significant.
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

One of the biggest changes for 9.10 is grub2. To get windows as the default see this site and you will edit /etc/default/grub and set GRUB_DEFAULT=saved
This will boot the last system used. 
You can adjust the saved entry to be only windows several ways:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by sylvainrb on 2009-11-06
Oops sorry, the first hard drive does have a SATA connection instead of an IDE one.

---

