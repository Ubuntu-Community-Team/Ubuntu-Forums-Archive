---
title: "Ubuntu not working after system update"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by mac98aop on 2009-01-16
PLEASE HELP BEFORE I CHUCK THING IN THE BIN!

I have a Dell Mini 9 and Update Manager just did 177 updates and installed all fine. Rebooted and then disaster! The window borders are pink and not blue and the windows key no longer does full screen.

If I play around in Themes it WON'T change the colour no matter what it thinks it's doing.

As for the Full Screen toggle?

Is it possible to revert the system to pre-update state?

PLEASE HELP

---

### Post by timcredible on 2009-01-16
was a new kernel included in the upgrade?  if so, reboot, and when grub shows up to give you choices of what to boot, choose the old kernel.  if everything works again, then you need to either use the old kernel, or maybe re-install the video drivers on the new kernel.

---

### Post by mac98aop on 2009-01-16
Thanks but please help!

How do I ascertain if a kernel was included?
What is grub?
How do I choose the old kernel?

---

### Post by mapes12 on 2009-01-16
I've had a look at your machines [spec]("http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-9?c=us&cs=19&l=en&s=dhs") and from what I can see you do not have an optical drive (CD or DVD) which means that your BIOS must be able to boot from another media such as a USB flash memory stick. You will need to check your documentation to confirm this as I'm not familiar with your hardware. On the basis that you can boot from a flash drive then you should be able to do a fresh install by following [this tutorial]("http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html"). It's based on the Asus EEE PC (eeeUbubtu) but you can use the iso file for whatever Ubuntu version you want to install. The main bit is using [unetbuntin]("http://unetbootin.sourceforge.net/").

---

### Post by ugm6hr on 2009-01-17
Some relevant Mini 9 threads:

1. Restore FF bookmarks and Windows key fullscreen toggle:
[http://ubuntuforums.org/showthread.php?p=6529628#post6529628](http://ubuntuforums.org/showthread.php?p=6529628#post6529628)

2. Pink theme issue (no complete solution yet)
[http://ubuntuforums.org/showthread.php?p=6543324#post6543324](http://ubuntuforums.org/showthread.php?p=6543324#post6543324)

---

### Post by muteXe on 2009-01-17
> **mapes12 said:**
> On the basis that you can boot from a flash drive then you should be able to do a fresh install by following [this tutorial]("http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html"). 

Why oh why do people suggest fresh installs all of the time?!  You don't see mechanics suggesting to people to buy new cars if the windows are dirty....

---

