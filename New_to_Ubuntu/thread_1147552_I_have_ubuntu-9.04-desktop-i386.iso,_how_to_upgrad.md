---
title: "I have ubuntu-9.04-desktop-i386.iso, how to upgrade my 8.10 with it?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-03
Hi
thank you for reading my post
I have ubuntu-9.04-desktop-i386.iso file in my ubuntu 8.10 and I want to upgrade it to ubuntu 9.04 using this image.

I looked in [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) but it mentions another image file name.

Any help is welcome.

Thanks.

---

### Post by snowpine on 2009-05-03
You can't; the disc in your possession is for installing, not upgrading. Follow the instructions in your own link for how to upgrade. :)

---

### Post by sneeks on 2009-05-03
it would be better to do a fresh install really,as sometimes upgrading creates some problems.
just backup all your stuff to an external h/d and do it from scratch,it will not take too long compared to a windows install.
iv'e just installed jaunty on a pc in the house here and took me just an hour including putting back all backed up stuff.

---

### Post by aysiu on 2009-05-03
You can't use the Desktop CD to upgrade (only to do a fresh reinstall).

If you want to upgrade by CD, you need the Alternate CD.

---

### Post by logos34 on 2009-05-03
> **aysiu said:**
> You can't use the Desktop CD to upgrade (only to do a fresh reinstall).

If you want to upgrade by CD, you need the Alternate CD.

yes, unfortunately.

I've never understood why they can't arrange things so you can upgrade from the desktop cd as well.  Sure would help a lot of people who have only the shipit live cd and dialup

---

### Post by aysiu on 2009-05-03
> **logos34 said:**
> yes, unfortunately.

I've never understood why they can't arrange things so you can upgrade from the desktop cd as well.  Sure would help a lot of people who have only the shipit live cd and dialup
There's not enough space on the Desktop CD to house all the packages needed for an upgrade. When the Desktop CD installs, it doesn't unpack and install all the individual .deb files. It makes a copy of a squashed live session on to the hard drive.

That's why a Desktop CD installation takes between 10 and 30 minutes, and an Alternate CD installation can take over an hour or sometimes 2 hours.

---

### Post by logos34 on 2009-05-03
> **aysiu said:**
> There's not enough space on the Desktop CD to house all the packages needed for an upgrade. When the Desktop CD installs, it doesn't unpack and install all the individual .deb files. It makes a copy of a squashed live session on to the hard drive.

So there is *absolutely *no way to integrate the two on a cd?

---

### Post by aysiu on 2009-05-03
> **logos34 said:**
> So there is *absolutely *no way to integrate the two on a cd?
Correct. It may be possible to integrate the two on a DVD, however.

---

### Post by scratman on 2009-05-03
could be combined on a disk quite easily, but not on a cd, it would be a DVD.  You'd be talking in excess of 1.2GB of data.  There is a bloat argument there.  It depends on whether shipit are prepared to offer DVDs in addition to CDs.  Surely it would be easier to negotiate that shipit offer the alternate as well as the install though?

---

### Post by Vyder on 2009-05-03
You can just type this into terminal, if you have a working internet connection, to upgrade your distro to the newest one.

```
sudo apt-get distro-upgrade
```

---

### Post by lindsay7 on 2009-05-03
I gpt mine by doing ALT plus F2 and typing "update-manager -d"

---

