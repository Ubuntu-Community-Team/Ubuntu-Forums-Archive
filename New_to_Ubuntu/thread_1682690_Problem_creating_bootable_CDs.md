---
title: "Problem creating bootable CDs"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by airscrew on 2011-02-06
Hi, and thanks for reading this.

Newbie to Unix/Ubuntu. Moderate PC skills in general, enough to be dangerous anyway...coding skills are poor, and many years ago (remember VMS, MVS, VM, PL/1???).

I have an old DELL D600 laptop, used by my young teenager.
XP has died. Tried all the usual recovery and boot utilities. No joy.
Pentium3 @850Mg with 500Mb. I could reload XP, but I'd have to buy another licence.
So time to move to Ubuntu.

After a number of failed attempts, starting with 10.10, I've down loaded the ISOs for:
Ubuntu 10.10 and 10.4
XUbuntu 10.4
LUbuntu 10.4
MD5 chksms are all good.

Burned a number of CD's without success. Tried CDBurnerXP (I'm working off a full XP desktop), ActiveISO, and INFRA.
YES, always burnt at the lowest speed.

ONLY ONE combination will load-up.
XUbuntu 10.4 via CDXP. 
Boots, installs, works just fine.

 The others just hang (ie wont boot after setting BIOS to boot from the CD/DVD drive). Thats on 2 laptops (old and new) and this desktop.


Q1. 

Any ideas why a burnt ISO image wont boot?? 
Especially Ubuntu 10.4 with OK MD5s and a 4x burn...???


Q2. 

Which is the most stable version, and the best place to download it from??


Q3.
Which is the best variant for an old laptop? 
Will Ubuntu run just fine, or should I try to get lightweight with X or L??
My preference would be a variant in which most default features work out of the box, and where I can have 'utility apps' rather than revert to hard coding the setup.


Any thoughts???
Thanks.
JAI.

---

### Post by Rubi1200 on 2011-02-06
Hi and welcome to the forums :-)

The hanging could be a graphics card issue, but also RAM.

In general, the older the machine, the better it is to use a lighter version like Xubuntu or Lubuntu.

---

### Post by fabricator4 on 2011-02-06
> **airscrew said:**
> 
I have an old DELL D600 laptop, used by my young teenager.
XP has died. Tried all the usual recovery and boot utilities. No joy.
Pentium3 @850Mg with 500Mb. I could reload XP, but I'd have to buy another licence.

Why?  The license label stuck on the machine is still good - for that machine.  At the worst you'll have to ring microsoft and get a new key.  It's not big deal - done it heaps of times - it gives you instructions on the screen.

> 
So time to move to Ubuntu.

Regardless, it's _always_ a good time to move to Ubuntu.

[quote]
Q1. 
Any ideas why a burnt ISO image wont boot?? 


Sometimes when drives age they go out of spec.  Sometimes it can be dust on the lens or even a scratch.  You could try a "head cleaner" type device in both the burner and the reader and see if that improves things.  Be careful about manually cleaning the lens as they are made of a very soft plastic and easily damaged.  If it still doesn't work you just have to replace the drives. :(

> 
Q2. 
Which is the most stable version, and the best place to download it from??


Arguably, Lucid 10.04 LTS.  Its the most mature, has had the most bug fixes, and is supported until 13.04. (Three years from realease date)

Get it from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") but it sounds like you've already got the ISO - you just need to burn a decent copy of it.

> 
Q3.
Which is the best variant for an old laptop? Will Ubuntu run just fine, or should I try to get lightweight with X or L??
My preference would be a variant in which most default features work out of the box, and where I can have 'utility apps' rather than revert to hard coding.


Well, Xubuntu isn't really that "light" anymore.  Gnome integration seems to have done it no favours. [Wikipedia]("http://en.wikipedia.org/wiki/Xubuntu")

Lubuntu appears to be a truly light version, however Lubuntu is not officially recognised as an Ubuntu derivative.  If Ubuntu isn't suitable for your machine then Lubuntu might work well. [Wikipedia]("http://en.wikipedia.org/wiki/Lubuntu")

My preference would still be for Ubuntu 10.04

Chris.

---

### Post by airscrew on 2011-02-08
> **airscrew said:**
> Hi, and thanks for reading this.

Newbie to Unix/Ubuntu. Moderate PC skills in general, enough to be dangerous anyway...coding skills are poor, and many years ago (remember VMS, MVS, VM, PL/1???).

I have an old DELL D600 laptop, used by my young teenager.
XP has died. Tried all the usual recovery and boot utilities. No joy.
Pentium3 @850Mg with 500Mb. I could reload XP, but I'd have to buy another licence.
So time to move to Ubuntu.

After a number of failed attempts, starting with 10.10, I've down loaded the ISOs for:
Ubuntu 10.10 and 10.4
XUbuntu 10.4
LUbuntu 10.4
MD5 chksms are all good.

Burned a number of CD's without success. Tried CDBurnerXP (I'm working off a full XP desktop), ActiveISO, and INFRA.
YES, always burnt at the lowest speed.

ONLY ONE combination will load-up.
XUbuntu 10.4 via CDXP. 
Boots, installs, works just fine.

 The others just hang (ie wont boot after setting BIOS to boot from the CD/DVD drive). Thats on 2 laptops (old and new) and this desktop.


Q1. 

Any ideas why a burnt ISO image wont boot?? 
Especially Ubuntu 10.4 with OK MD5s and a 4x burn...???


Q2. 

Which is the most stable version, and the best place to download it from??


Q3.
Which is the best variant for an old laptop? 
Will Ubuntu run just fine, or should I try to get lightweight with X or L??
My preference would be a variant in which most default features work out of the box, and where I can have 'utility apps' rather than revert to hard coding the setup.


Any thoughts???
Thanks.
JAI.

Thanks for the help so far.

I'm still not up and running.
It appears I keep burning images that either
a) appear empty (to both windows and Ubuntu)
b) wont boot from the CD
I must be doing something dumb.

Could someone please take the time to walk me through each of the steps I need to create a fresh install on a laptop, but downloading and burning on an XP machine.

Thanks.

---

### Post by Bucky Ball on 2011-02-08
Xubuntu 10.04 LTS is a good fit for your specs. You have the best and most stable version. LTS = long term support (til 2013). ;)

Hang in there, enjoy the learning curve, the OS, and welcome to the forums. Post back with any issues.

---

### Post by migs73 on 2011-02-08
When burning the ISO, are you telling the burning software to 'burn an image' to the disc? Or just burning the ISO file, 'cos that won't work.

That caught me out the first time!!

Mike

---

### Post by airscrew on 2011-02-09
> **migs73 said:**
> When burning the ISO, are you telling the burning software to 'burn an image' to the disc? Or just burning the ISO file, 'cos that won't work.

That caught me out the first time!!

Mike

Thanks to all. 
Up and working now.

As above,
It seems that not all ISO burners burn a bootable image by default.
Most seem like music/DVD burners that also do ISO (badly!).
After trying a few, ISOBurner seems the best with default settings for me.

---

### Post by Bucky Ball on 2011-02-09
Once you're in Ubuntu, Applications>Sound and Video>Brasero. Just for future reference. Burn image. Easy. ;)

---

### Post by fabricator4 on 2011-02-10
Also easy, (or even easier?):

```
->System
    ->Administration
        ->Startup Disk Creator
```

---

