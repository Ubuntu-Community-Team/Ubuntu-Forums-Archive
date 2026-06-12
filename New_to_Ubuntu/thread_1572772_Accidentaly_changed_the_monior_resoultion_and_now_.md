---
title: "Accidentaly changed the monior resoultion and now dont get an image"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by mos2111 on 2010-09-11
I was looking at the monitor settings for my current monitor and had a cat - tastorphy with some help from my cat.  My resolution was changed and now I am unable to view the desktop from one of my user profiles.  The resolution I need to set it back to is 1280x1024.  I have tried several things from the terminal, but am afraid of changing important settings.
Is there a simple way to do this?  
thanks

---

### Post by papibe on 2010-09-11
Do you have a xorg.conf file?
```
$ ls /etc/X11/xorg.conf
/etc/X11/xorg.conf
```
If so, you could try to rename it. That way X will try to get the data from the monitor.
```
$sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old 
```
and then restart your PC.

BTW, long time ago my brother's cat, "Chonita", scratched my Splinter Cell CD before I was able to installed it...arrg!!

Good Luck.

---

### Post by mos2111 on 2010-09-11
> **papibe said:**
> Do you have a xorg.conf file?
```
$ ls /etc/X11/xorg.conf
/etc/X11/xorg.conf
```
If so, you could try to rename it. That way X will try to get the data from the monitor.
```
$sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old 
```
and then restart your PC.

BTW, long time ago my brother's cat, "Chonita", scratched my Splinter Cell CD before I was able to installed it...arrg!!

Good Luck.

Program LS is not installed, do you wish to install it.

also tried 
/etc/X11/xorg.conf
and got Permission Denied.

---

### Post by 73ckn797 on 2010-09-11
Will recovery mode not reset to a basic resolution?

---

### Post by mos2111 on 2010-09-11
> **73ckn797 said:**
> Will recovery mode not reset to a basic resolution?

How would I start in recovery mode from terminal?
Also, will this kill everything on my desktop?

Thanks

---

### Post by 73ckn797 on 2010-09-11
Recovery mode is available at the grub menu, that is if you can even get there. What version of Ubuntu are you running? It will not kill anything except what may be the problem.

---

### Post by mos2111 on 2010-09-11
> **73ckn797 said:**
> Recovery mode is available at the grub menu, that is if you can even get there. What version of Ubuntu are you running? It will not kill anything except what may be the problem.

9.04 Jaunty.
Thanks
ETA - I can use the monitor and access a terminal from one of the other user accounts I created for the computer, although it is not the admin profile.

---

### Post by mos2111 on 2010-09-11
I tried to start from recovery and it still wont work. 
what am I doing wrong?

---

### Post by pastalavista on 2010-09-11
At the log in screen, enter your admin name and password but select "Failsafe Gnome" in the "Session" button on the bottom toolbar. You should be then able to boot with low-res graphics and reset the resolution. Then log out & back in to your regular Gnome session.

---

