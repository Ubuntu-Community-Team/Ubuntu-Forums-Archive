---
title: "login"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by creekstar on 2009-03-11
Well, I installed Ubuntu on my old spare computer about 3 mos back, and guess what, I have no idea what I used for my username/password is.  If I can't get pass the login screen, I suppose I will have to wipe the drive and start over.  Luckily I have no files on it as I was just experimenting with it anyway, but it is frustrating to have this happen.  Any suggestions how to bypass this screen or is it too much of a security question to answer?  No big deal either way, just a little more trouble to go to.   Creekstar:oops:

---

### Post by taurus on 2009-03-11
Boot into recovery mode from GRUB menu (if you don't see a menu, offering you a choice which to boot, press Esc key to bring it up) and at the prompt, see what is your login name.

```
ls -la /home
```
Assuming your login name is star, you can reset a password for star with

```
passwd star
```
Once you have changed a password for star, reboot and see if you can login now.

```
shutdown -r now
```

---

