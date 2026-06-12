---
title: "setting up root"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Ed_K on 2009-09-26
I have just switched from Fedora 11 to 9.04.  I noticed that I was not allowed to set up my root password during install.  Now I have no "root".  I'm sure it is a simple process, but could I get some guidance on this?

---

### Post by SuperSonic4 on 2009-09-26
You can use sudo for root access. We can't tell you how to enable root - it's against forum rules

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Personally, I like being able to be root, it's often easier

---

### Post by Temposs on 2009-09-26
Ubuntu does not encourage use of a root account, and makes it more difficult to set up. I recommend to stick with Ubuntu's sudo privelege model, as everything is designed around that.

---

### Post by Paqman on 2009-09-26
Use sudo at the command line, or gksu (Gnome) or kdesu (KDE) for graphical apps.

---

### Post by skymera on 2009-09-26
It's never been enabled in Ubuntu since i've used it (7.04)

And personally, i discourage the use, i've managed to get everything working with little effort without it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) I hope this helps a bit.

---

### Post by credobyte on 2009-09-26
You don't need one :)

```
sudo -i
<command #1>
<command #2>
exit

```

---

### Post by Ed_K on 2009-09-26
Thanks all.  Great info and references.  I didn't think that there was that big a difference between F11 and Ubuntu, but I'm starting to see that there is.  And a free pocket guide to boot.:)

---

### Post by credobyte on 2009-09-26
> **Ed_K said:**
> Thanks all.  Great info and references.  I didn't think that there was that big a difference between F11 and Ubuntu, but I'm starting to see that there is.  And a free pocket guide to boot.:)

Having root account disabled by default isn't a big difference - you can ( not recommended! ) enable it if you want.

---

