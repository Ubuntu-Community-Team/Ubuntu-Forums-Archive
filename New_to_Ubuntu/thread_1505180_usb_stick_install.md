---
title: "usb stick install"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by skyjacker on 2010-06-08
Just wondering... I have put remix onto a usb stick, and made some changes, as well as saved some documents etc (I have 1 Mg of persistence on the stick). Now the question - if I install from this stick, will all of my changes, etc still be there, or will I have to start over?:confused:

---

### Post by nhasian on 2010-06-08
I dont think it will automatically transfer your changes, but it should be easy enough to copy over your settings from the /home folder.  The great thing is Ubuntu will run a LOT faster when its installed to your hard disk instead of running from a usb stick.

---

### Post by C.S.Cameron on 2010-06-09
With a persistent install all additions and changes are saved to a file, (or partition), named casper-rw.
Casper-rw is not copied when you do an install from the flash drive.
You might be able to copy data from the booted flash drive to the hard drive where Ubuntu has been installed but I have had no luck duplicating a home folder from a booted drive and I don't know of a method of accessing a casper-rw file except when booted from it's drive.
If you are using a casper-rw partition then you should be able to at least copy the home folder when booted to Ubuntu from a third medium.

---

