---
title: "error: Can't locate x11 installation"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by SaffronB77 on 2009-03-30
Hi All, 

I'm trying to install Conky 1.6.1 and have run into an issue. 

I get the error can't locate X11 installation. 

I searched X11 in add/remove applications and downloaded and installed Emacs22(X11) . How do I pinpoint where the problem is? Is Emacs not what I need?

Any help is greatly appreciated

---

### Post by llamakc on 2009-03-30
Conky 1.6.1 is in the Intrepid repositories. Are you using an older version of Ubuntu?

```

sudo aptitude install conky

```FWIW the X11 error refers to the precursor of Xorg, which was X11. When building software, those errors are often due to the lack of having the development files installed. In this case that could be the package xserver-xorg-dev, libx11-dev or something similar.

---

### Post by wolfen69 on 2009-03-30
only do aptitude install if you do
```
sudo aptitude update
```
first.

---

### Post by SaffronB77 on 2009-03-30
Thanks guys, your replies are appreciated.

I ran sudo aptitude update, then sudo aptitude install conky. 

After a reboot, I see I've up(down?)graded to xubuntu. Also, I don't see how to start conky. I noticed that when I ran install conky it was ver 1.5. The packkage I was trying to install is 1.6.  That's not a big deal, either is fine, I'm just wondering why I still can't get either version to work. I still get the X11 error when using ./configure for 1.6

Edit: llamakc, I'm using Hardy. Thanks fro your patience, I'm learning as I go :)

---

