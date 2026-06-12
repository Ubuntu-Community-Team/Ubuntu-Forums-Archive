---
title: "how to install latest intel driver"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by asif_1088119 on 2010-04-11
intel came up with their latest release for intel drivers in ubuntu.Intel 2010Q1 graphics package includes  xf86-video-intel 2.11.0 release.i want to know where to find .deb of this.

---

### Post by asif_1088119 on 2010-04-13
bump

---

### Post by 3rdalbum on 2010-04-13
> **asif_1088119 said:**
> intel came up with their latest release for intel drivers in ubuntu.Intel 2010Q1 graphics package includes  xf86-video-intel 2.11.0 release.i want to know where to find .deb of this.

I don't think you'll find a Debian package of it; I believe it needs to be compiled against your version of Xorg.

I wouldn't mess with it, if I were you. Last time I messed with compiling new graphics drivers, I broke my system.

---

### Post by f1r3flie on 2010-04-13
There's an easier way to update your drivers than downloading and installing the files from the website: use the drivers tool in Ubuntu. In my 9.10 install it's under System>Administration>Hardware Drivers. If it isn't available in that tool, perhaps you should look for it in Synaptic Package Manager. I personally have never had driver issues so I don't know how this will work. You can also have a look at the Intel website for it.

---

### Post by clhsharky on 2010-04-13
Hi asif_1088119


The graphics package including xf86-video-intel 2.11.0 for Ubuntu is available with a PPA but not for Jaunty. To run that package you need KMS 'kernel mode seting', that means Karmic with KMS enabled or Lucid and KMS is already enabled. If your on Jaunty I'm guessing you didn't want the problem some people had with intel and Karmic with new KMS growing pains. I would try a live session with Lucid with cd/usb and see if everything works. Hopefully better, then you can add this PPA.

[https://launchpad.net/~xorg-edgers/+archive](https://launchpad.net/~xorg-edgers/+archive)

Sharky

---

### Post by asif_1088119 on 2010-04-13
hi clhsharky

i am having compiz problem with my intel driver and thats why i am looking for a solution.what is the latest and stable intel driver release for jaunty then??

---

### Post by sandyd on 2010-04-13
if you look in the link that the poster gave for xorg-edgers, there is a link on the page for xorg-stable.

---

