---
title: "Currently using windows xp"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by kmjlvsmdj on 2010-01-26
I am currently using windows xp and was going to reformat the hard drive and completely reinstall windows when I came upon ubuntu. I would like to try it. Can I format the hard drive and wipe everything out then install ubuntu? I have downloaded and made the cd to install ubuntu from the website. Can I just reformat the hard drive then put in the cd and reboot the computer and install ubuntu?

---

### Post by J V on 2010-01-26
Yes, but you could also just boot from the CD and let ubuntu do the formatting :P

Just stick the disc in, boot, and follow the "Next" brick road...

---

### Post by terrapin893 on 2010-01-26
The ubuntu install CD will be able to do all of that for you.  Just pop the CD in the drive, boot from it and enjoy the ride!

---

### Post by Rex Bouwense on 2010-01-26
> **kmjlvsmdj said:**
> I am currently using windows xp and was going to reformat the hard drive and completely reinstall windows when I came upon ubuntu. I would like to try it. Can I format the hard drive and wipe everything out then install ubuntu? I have downloaded and made the cd to install ubuntu from the website. Can I just reformat the hard drive then put in the cd and reboot the computer and install ubuntu?

You can do that or you can boot from the Live CD and try Ubuntu on your machine to see if it recognizes everything and if you like it without changing anything on your computer.  I would check it out first, but it's your call.

---

### Post by lisati on 2010-01-26
Be sure to make sure you've made a set of recovery disks from your recovery partition first (if you have one), "just in case"

---

### Post by jd65pl on 2010-01-26
Note that running a live CD performance will be slower than an actual install

---

### Post by kmjlvsmdj on 2010-01-26
thanks for all the help. I kind of figured that the disk might do it for me if I wanted it to, but was unsure. Thanks so very much.

---

### Post by A&#11375;A on 2010-01-26
You might want to look into Wubi ([http://wubi-installer.org/](http://wubi-installer.org/)) no reformatting required, and you get to experience full-on ubuntu, not live ubuntu (and there is a major difference).

I'd start there, then perhaps you might want to partition your hard drive and boot both Ubuntu and XP.

---

### Post by abcuser on 2010-01-26
> **kmjlvsmdj said:**
> Can I format the hard drive and wipe everything out then install ubuntu?
Hi,
I think you have little bit of misunderstanding what formating is. Formating means changing raw disk to file system. So if you will use Windows to format, then it will create NTFS file system. But Ubuntu uses ext4 file system, so if you format in Windows, then at Ubuntu install you will need to remove NTFS file system and format it with ext4. I suggest to put in Ubuntu CD and boot computer from CD. Then just install Ubuntu and when it will come to partitioning it will ask you if you would like to wipe out whole disk and format it with Ubuntu file system.

By the way, you can also have Windows XP and Ubuntu on the same computer if you like. There are multiple ways of doing it.

INSTALL UBUNTU INSIDE WINDOWS
1. Install Windows XP.
2. Start Windows and insert Ubuntu CD.
3. Wubi installer will pop-up and you are ready to install Ubuntu inside Windows file system. This option is for users that are capable of installing any other Windows application, but are not geeks of knowing disk partitioning etc.
4. If you decide to uninstall Ubuntu, just go to Add-Remove programs in Windows and uninstall Ubuntu just like any other Windows applicaiton.

INSTALL UBUNTU BESIDE WINDOWS
1. Install Windows XP
2. Shut down Windows
3. Insert Ubuntu CD and install Ubuntu.
4. Ubuntu installer will try to partition your system automatically in such a way that Windows partition will be sized down and Ubuntu partition created.

INSTALL UBUNTU AS VIRTUAL COMPUTER
1. Install Windows XP
2. Download VirtualBox and install it
3. Create virtual machine using VirtualBox
4. Install Ubuntu inside VirtualBox as virtual guest.

INSTALL ONLY UBUNTU
If you decided to give up on Windows XP you can just:
1. Insert Ubuntu CD
2. Restart you computer and let it boot it from CD.

Hope this helps

---

### Post by warfacegod on 2010-01-26
> **A&#11375 said:**
> You might want to look into Wubi ([http://wubi-installer.org/](http://wubi-installer.org/)) no reformatting required, and you get to experience full-on ubuntu, not live ubuntu (and there is a major difference).

I'd start there, then perhaps you might want to partition your hard drive and boot both Ubuntu and XP.

You won't get the "full" Ubuntu. For example, you won't be able to run any of the extra visual effects that so may find so pleasing and useful. You will, however, have all of the basic functionality of an actual install. Wubi installs have also been known to become unusable after a round of updates, on occasion.

---

### Post by J V on 2010-01-26
> **warfacegod said:**
> You won't get the "full" Ubuntu. For example, you won't be able to run any of the extra visual effects that so may find so pleasing and useful. You will, however, have all of the basic functionality of an actual install. Wubi installs have also been known to become unusable after a round of updates, on occasion.I got lots of "pleasing" effects out of my wubi when I was in jaunty ;)

Only real issue with wubi is hibernation (which doesn't work)

---

### Post by warfacegod on 2010-01-26
> **J V said:**
> I got lots of "pleasing" effects out of my wubi when I was in jaunty ;)

Only real issue with wubi is hibernation (which doesn't work)

Your the first person I've heard of getting Extra Effects from a Wubi install. Hibernation hardly works for normal installs so it's not surprising that it wouldn't work in a Wubi either.

---

### Post by funkychild on 2010-01-26
> **j v said:**
> follow the "next" brick road...


lol

---

