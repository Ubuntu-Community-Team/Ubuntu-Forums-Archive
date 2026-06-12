---
title: "Why is the File system read-only"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by donescamillo on 2009-11-16
Hi,

I just installed Ubuntu 9.10. I wanted to edit grub.cfg so that WinXP is first by default. I wrote in terminal 

gksu gedit /boot/grub/grub.cgf

I moved the WinXP entry up, but could not save the file, it said teh hard drive was read-only!!!

I did not have this problem with 9.04. In 9.04 I could edit grub.cfg, fstab, /X11/xorg.conf without any problems. What has changed in 9.10?
How can I make the file system not to be read-only?

regards
donescamillo

---

### Post by nitstorm on 2009-11-16
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)   

Read the Grub vs. Grub2 section. Hope this helps...

---

### Post by Paqman on 2009-11-16
It's just that one file that's read-only, and it's done to prevent you breaking Grub by editing it. You should instead edit /etc/default/grub.

---

### Post by ukripper on 2009-11-16
post deleted. Not relevant...

---

