---
title: "Won't boot into GUI on G3 IMAC"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by GoldenHippo on 2009-01-26
Okay, I recently aquired an old G3 IMAC from a friend and decided it woud make a good platform for Ubuntu.
So one download of Xubuntu and a Looooong install later and the computer was ready.. Or so I thought.
Now when booting I get the Xubuntu splash screen but then it drops into a black screen and command line with the prompt " initramfs ".
Any ideas on what to do? I'm pretty okay with computers generally, but this is my first attempt with Linux, so idiot proof answers would be nice!  Thanks for your help.

---

### Post by cardinals_fan on 2009-01-26
That machine might be too old.  Xubuntu is not very lightweight.  You have three choices:

1) Download the Xubuntu alternate CD.  This launches a very simple ncurses installer which you can use to install Xubuntu without booting to the GUI.  It should load okay after installation, but may be slow.  This choice is "easiest" and should be attempted first.

If Xubuntu installs okay but proves too slow for that machine, then move on too the backup options.

2) Install a lighter distro such as SliTaz, PUD, or U-Lite (this last option is an Ubuntu remaster and is basically Ubuntu with LXDE and lighter defaults).

3) Install an Ubuntu CLI system and grab Xfce manually.  This may be too advanced if you're new, so try the other two first.
[B]
EDIT: Hold up!  You need a system compatible with the PowerPC architecture.  There is a Xubuntu alternate CD [here]("http://cdimage.ubuntu.com/xubuntu/ports/releases/8.10/release/xubuntu-8.10-alternate-powerpc.iso") that you should absolutely try.

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)[/B]

---

### Post by snowpine on 2009-01-27
Great advice from Cardinalsfan. Make sure you have at least 256mb of ram if you want to run Xubuntu, or 512mb for Ubuntu (in my opinion).

---

