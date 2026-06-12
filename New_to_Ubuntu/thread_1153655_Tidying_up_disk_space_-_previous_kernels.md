---
title: "Tidying up disk space - previous kernels"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by alexcckll on 2009-05-09
Hi folks, 

I run 8.04.2LTS on a preinstalled Lenovo Thinkpad R61i bought from Linux Emporium.

I've been keeping a track of my disk usage, and was shocked to find out how much space was taken up by boot options I do not use.

I have accepted updates, and found another kernel update in there.

Current uname entries - 

"alex@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux"

I noticed I have kernel levels from 2.6.24-16 through to 24 on disc.. how do I *SAFELY* tidy my boot options up?  

Reading around it, I gather that the safest way to work is to keep 3 revisions of kernel around - so that leaves -16, -17 and -19 as no longer needed.

I went into Synaptic and searched for "linux-generic", highlighted the -16 pack that was installed.. but wording as in "You don't want to touch this package" came up in the description field.

I backed out - shut down Synaptic and made no changes.

I do NOT want to risk doing damage.. but likewise, i do want to keep close control of my root filesystem's disk usage - currently running at 10% used.

Just another scared ex-Wintel user.

---

### Post by Didius Falco on 2009-05-09
Here is a guide to removing old kernels:

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

You are correct in keeping a couple of kernels available - just in case.

If you just want to tidy up your Grub menu, and it's not an issue of available space, you may want to just comment out the ones you don't want displayed in your menu.lst file.

If you are interested in doing that instead, and need some instructions on how to do so, just post again.

I hope this helps...

Regards,

Didius

---

### Post by spcwingo on 2009-05-09
Alternately, you can use ubuntu-tweak to cleanup unused kernels, uninstalled program configurations, thumbnails, etc.  It also makes other things easier...give it a shot.  It can be found here:

[direct download]("http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.4.7.1-1%7Ejaunty1_all.deb")

---

