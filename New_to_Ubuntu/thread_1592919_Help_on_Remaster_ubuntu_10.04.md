---
title: "Help on Remaster ubuntu 10.04"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by tsinelas30 on 2010-10-11
Guys I need your help.

Im finished creating an .iso file.

But when i tried to install the iso file

there is an error:

could not find ramdisk image: /casper/initrd/gz



please help.

---

### Post by diablo75 on 2010-10-11
I've never made my own ISO, but if it's looking for casper then it means your ISO was built to be "stay-resident" or something like that.  In other words, intended to store anything you save while running in the live environment, which is ideal for booting from a USB stick but not from a CD (because it can't be written to).

So you might have to rebuild your ISO and see if there are options that you need to disable... again, I've not done this but that's what it looks like your problem might be...

---

### Post by tsinelas30 on 2010-10-11
> **diablo75 said:**
> I've never made my own ISO, but if it's looking for casper then it means your ISO was built to be "stay-resident" or something like that.  In other words, intended to store anything you save while running in the live environment, which is ideal for booting from a USB stick but not from a CD (because it can't be written to).

So you might have to rebuild your ISO and see if there are options that you need to disable... again, I've not done this but that's what it looks like your problem might be...


Thanks Sir. i will try to create an ISO again.

---

