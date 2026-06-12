---
title: "[SOLVED] Permissions for /dev/ttySHSF0"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by nunnst on 2007-12-20
I am trying to get gnome-ppp to work from a user account to dial out on a softmodem (port /dev/ttySHSF0).  Gnome-ppp dials and connects just fine with the ISP [COLOR="Red"]**[SIZE="4"]IF[/SIZE]**[/COLOR] you do ```
sudo gnome-ppp
``` or ```
gksudo gnome-ppp
```....but that just won't work for grandmama!  

I found this thread [HTML]http://ubuntuforums.org/showthread.php?t=38106[/HTML], which looked promising, until i discovered there is not a "/etc/dev/permissions.d" file on this Gutsy installation for me to edit (at least not according to the find command I issued).

Frankly, I'm clueless on this and I'm just assuming that I have a permission problem. Gnome-ppp is a frontend for wvdial, which is the code talking to the modem port (the driver actually). Permissions for gnome-ppp, wvdial, and /dev/ttySHSF0 are:

```
[INDENT]-rwxr-xr-x 1 root root 55632 2006-09-28 08:13 /usr/bin/gnome-ppp
-rwxr-xr-x 1 root root 100796 2007-06-14 09:51 /usr/bin/wvdial
crw-rw---- 1 root dialout 240, 64 2007-12-20 18:47 /dev/ttySHSF0
[/INDENT]
```

Thanks in advance for the help!    

I'm going to take a 30 min smoke break and maybe one of Linux gurus will have the magic answer (god knows I don't)!!    

:guitar:

---

### Post by nunnst on 2007-12-21
Found solution! Moved gnome-ppp executable and config file into home folder - worked like a charm.  Now have softmodem working with GUI dialer.  Grandmama is gonna be happy!

Thanks for reading my post.  

:lolflag:

---

