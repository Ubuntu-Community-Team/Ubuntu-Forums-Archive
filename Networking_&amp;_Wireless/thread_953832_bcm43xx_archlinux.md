---
title: "bcm43xx archlinux"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by z.s.tar.gz on 2008-10-20
OK, so I know that this is ubuntu forums and I should post this on the archlinux forums, but there are a lot more people here and deep down all linux systems are (basically) the same, right?

So, I have a microsoft mn720 wireless card, and in ubuntu I could make it work with ndiswrapper and bcm43xx. I would like to be able to use it in archlinux, but none of their tutorials work for me. btw, I always used a script to install bcm43xx, not fwcutter directly, and I don't know how to do that.

Apparently this script does not work in archlinux, and their wiki doesn't work.

Please help me out! :D

---

### Post by Ayuthia on 2008-10-20
> **z.s.tar.gz said:**
> OK, so I know that this is ubuntu forums and I should post this on the archlinux forums, but there are a lot more people here and deep down all linux systems are (basically) the same, right?

So, I have a microsoft mn720 wireless card, and in ubuntu I could make it work with ndiswrapper and bcm43xx. I would like to be able to use it in archlinux, but none of their tutorials work for me. btw, I always used a script to install bcm43xx, not fwcutter directly, and I don't know how to do that.

Apparently this script does not work in archlinux, and their wiki doesn't work.

Please help me out! :D

Can you post the results of lspci -nn and uname -r?  I just want to see which chipset you have along with which kernel you are using.

Did you try the following guide:
[http://wiki.archlinux.org/index.php/B43#b43](http://wiki.archlinux.org/index.php/B43#b43)

---

### Post by sethvath on 2008-10-20
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

For step 2 you need to find the windows driver for your wireless card instead of using the one listed.

---

### Post by z.s.tar.gz on 2008-10-20
OK ill try it out asap
got to get my laptop up and running w/ arch first
(I've been going on a distro hunt)

---

### Post by z.s.tar.gz on 2008-10-21
oops. I'm a retard. I forgot to add ndiswrapper as a module to rc.conf.
lol sorry for your time, marking as solved.

---

