---
title: "can i up grade to 9.10 with out the a cd"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by blake7 on 2009-10-28
yea can i up grade through my 9.04???

and if so what about all the programs, documents and setting on my 9.04 will they sill be thier
???
ps will it be simple

---

### Post by philinux on 2009-10-28
Backup anything important. The update should be offered to you by the update manager tomorrow. Documents and Settings are unaffected by an upgrade. Things can go wrong though.

---

### Post by SunnyRabbiera on 2009-10-28
Yeh you will be able to update to 9.10 without a CD, no problem.
But yeh back up just in case.

---

### Post by undecim on 2009-10-28
Hit alt+f2 and type "update-manager -d" and you will get an update window with the option to upgrade to 9.10

I would recommend having at least a LiveCD of any type handy, in case something happens during the upgrade (power outage, etc.)

Though since Karmic brings with it the much faster ext4 filesystem, it is recommended that you backup your data and do a fresh install, so that you get a new filesystem with a performance boost. 

Or, if you were clever enough to use a sepaarate home partition, you can reinstall without evacuating your files, as long as when installing, you make sure to set the mount point for your home partition, but DO NOT FORMAT IT.

---

### Post by undecim on 2009-10-28
> **philinux said:**
> Backup anything important. The update should be offered to you by the update manager tomorrow. Documents and Settings are unaffected by an upgrade. Things can go wrong though.

Wow, I didn't even realize until just now how close the official release is! I need to start LightScribing some CDs!

---

### Post by blake7 on 2009-10-28
thank you all for your reports

i like the suggestion to down load the live cd just in case, i will be doing just that, thanks to you



cheers you all and may the force be with you

---

### Post by ts13209 on 2009-10-28
First off, please forgive my lack of knowledge with Ubuntu, I purchased a Dell mini 9 back in March with it installed and am learning new things about this OS everyday :) I have a question concerning this upgrade to 9.10 . My netbook does not have a CD drive  internally. I would have to use an external device, something I have not purchased yet. I was wondering if it is possible however to download the upgrade to another computer (desktop) that I own, and then transfer that file to a thumb drive to then install onto my netbook through one of the USBs?  I got the idea recently while looking at thumbdrives on eBay and noticed someone was selling 4 GB thumbdrives with the current version of Ubuntu. I guess you load it onto your computer and then when finished you have a thumbdrive you can use thereafter. I believe my current version of Ubuntu is 8.0.4 . Any thoughts if this would work inmy situation? Thank you.

---

### Post by MrWES on 2009-10-28
> **ts13209 said:**
> First off, please forgive my lack of knowledge with Ubuntu, I purchased a Dell mini 9 back in March with it installed and am learning new things about this OS everyday :) I have a question concerning this upgrade to 9.10 . My netbook does not have a CD drive  internally. I would have to use an external device, something I have not purchased yet. I was wondering if it is possible however to download the upgrade to another computer (desktop) that I own, and then transfer that file to a thumb drive to then install onto my netbook through one of the USBs?  I got the idea recently while looking at thumbdrives on eBay and noticed someone was selling 4 GB thumbdrives with the current version of Ubuntu. I guess you load it onto your computer and then when finished you have a thumbdrive you can use thereafter. I believe my current version of Ubuntu is 8.0.4 . Any thoughts if this would work inmy situation? Thank you.

This will work for your situation:
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

I know several people that ONLY install using this method using a USB flash drive with unetbootin.

~Bill

---

### Post by annie227 on 2009-10-28
so is the release candidate,rc, different from what will be available tomorrow or in however many hours it will be?

---

### Post by H2SO_four on 2009-10-28
> **annie227 said:**
> so is the release candidate,rc, different from what will be available tomorrow or in however many hours it will be?

Not in any major way.  If you are running the RC you will get the update manager tomorrow letting you know there are some things to do.  Thats about it.

---

### Post by philinux on 2009-10-28
final release.No if you update you have the same thing. they are all milestone releases.

Anybody who install alpha1 and kept updating will have the final release.

---

