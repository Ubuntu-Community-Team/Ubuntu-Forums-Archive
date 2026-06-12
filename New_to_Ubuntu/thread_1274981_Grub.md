---
title: "Grub"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-09-25
I have to keep windows on my desktop along with ubuntu.
When i reinstall windows,i cant c the menu to select the os and it goes to windows directly.

How do i bring the grub menu

---

### Post by philinux on 2009-09-25
If it's vista you could use easybcd [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1). The download button for easybcd is at the bottom of the page. 

Or reinstall grub from the live cd as windows will have nuked the mbr with it's own bootloader.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tpjk on 2009-09-25
if you want to create a dual boot system it's good practice to make your windows partition the boot partition i.e. on a formatted hard drive, install windows first, then pop in your live cd and boot from it, and install ubuntu on a seperate partition.

---

