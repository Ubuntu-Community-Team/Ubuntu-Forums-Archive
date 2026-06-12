---
title: "Quick Installation help please"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-10-10
Currently i have ubuntu 10.04 installed under inside windows. I want to upgrade to 10.10 with a 10.10 disk i burned. So now i am in ubuntu under windows with the 10.10 iso and a disk 10.10 iso. How do i upgrade with the disk or image? 

I know you can upgrade through the update manager but i would rather upgrade through the disk.  Can someone help upgrading from the disk.

I am pretty new at this so if you could explain in detail that would be great. Thanks

---

### Post by andrewthomas on 2010-10-10
Do you want the install to remain inside windows?

---

### Post by hunter99507 on 2010-10-10
Yes i do.

---

### Post by andrewthomas on 2010-10-10
Check this out.
 
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by arpanaut on 2010-10-10
You might want to check the release notes,
I do remember reading about some issues with upgradeing from a wubi install.
See:[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

Scroll down to Known Issues

---

### Post by hunter99507 on 2010-10-10
Ive read that but i dont see where it says how to upgrade from 10.04 to 10.10 with a disk. I would like to upgrade, not install a fresh copy. Any ideas?

---

### Post by jtarin on 2010-10-10
Not to certain about WUBI, but _it might be possible_ to install by going to your software sources and list the cdrom as a source. Make sure the cd is inserted and make sure the software source is listed correctly. Then I would maybe go offline and then choose to upgrade using the cd or uncheck the other sources and use only the cd. Not for certain it will work easily.

---

### Post by andrewthomas on 2010-10-10
You could try to change the entry about the CD in your 
 
/etc/apt/sources.list from lucid to maverick, 10.04 to 10.10 and enable it.
 
EDIT: jtarin beat me to it.

---

### Post by jtarin on 2010-10-10
> **andrewthomas said:**
> You could try to change the entry about the CD in your 
 
/etc/apt/sources.list from lucid to maverick, 10.04 to 10.10 and enable it.
 
EDIT: jtarin beat me to it.A more direct non-GUI aproach. :)

---

### Post by bcbc on 2010-10-11
It's not a good idea to change your software sources to upgrade. Not sure why people would advise that.

Also, you shouldn't upgrade a wubi install of 10.04 to 10.10 yet. The release notes explain why. 

But when that problem is fixed, you can download the alternate CD and run "cdromupgrade" from there. There are instructions somewhere, but I just boot into the wubi install, loop mount the cdrom and run it:
```
sudo mount -o loop ubuntu-alternate-xxx.iso /mnt
sudo /mnt/cdromupgrade
```

The official guide tells you to mount to /media/cdrom and then it will automatically prompt you if you want to upgrade, but this didn't work for me so I used the method I showed.

You will still need to click on YES when it prompts you to check for the latest updates online. Most of the packages will come from the CD, but you'll need to get the latest changes - since these will have the fixes for the wubi upgrade, if and when they are released.

---

### Post by jtarin on 2010-10-11
[I would agree with this method.]("https://help.ubuntu.com/community/MaverickUpgrades")

---

