---
title: "repairing broken system from live cd"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by bacardiandwatermelon on 2009-05-21
Hey all,

I just spent the last couple of hours in hell as I "accidently" installed the fglrx-kernel-source and had a black screen on boot with no login window and no tty1 login either. And because I didn't change my root password I couldn't log into root from that recovery menu. In the end I had to use my Alternate cd and use the rescue a broken system so I could boot into my shell and run "sudo apt-get remove fglrx-kernel-source". My question is, is it possible to do this from the live cd and remove packages from the local drive? sorry if this doesn't make any sense, i'm a bit amped.

---

### Post by taurus on 2009-05-21
Boot into recovery mode from GRUB menu (not Ubuntu LiveCD) and use the xfix option to fix your X server.

---

### Post by bacardiandwatermelon on 2009-05-21
xfix didn't work for me. First thing I tried :-( The only solution was to remove that package. I was just looking for a way to remove local hdd packages from the live cd.

---

### Post by taurus on 2009-05-21
Can you get into root shell from the recovery mode?

---

### Post by Apollo87 on 2009-05-21
> **bacardiandwatermelon said:**
>  And because I didn't change my root password I couldn't log into root from that recovery menu. 

sudo su

That should log you in as root using your user password

---

