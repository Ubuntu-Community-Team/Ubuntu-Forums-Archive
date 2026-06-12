---
title: "Ubuntu Unistall"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by eugeneisobel on 2009-05-30
I need to uninstall ubuntu.  I used hp recovery disc to reformat the hard disk and reinstall windows 98.  When I reboot grub appears and to load ubuntu and fails.  What needs to be done to get rid of grub?


eugeneisobel

---

### Post by TeoBigusGeekus on 2009-05-30
Get yourself a windows cd, boot with it and type r to get into recovery mode.
Then type 
```
fixmbr
```
to fix the master boot record and you are done.

---

### Post by bacardiandwatermelon on 2009-05-30
win98? That's a blast from the past.

---

### Post by eugeneisobel on 2009-05-30
:p> **TeoBigusGeekus said:**
> Get yourself a windows cd, boot with it and type r to get into recovery mode.
Then type 
```
fixmbr
```
to fix the master boot record and you are done.

Thank you.

eugeneisobel

---

### Post by SunnyRabbiera on 2009-05-30
Well why unintall ubuntu that will be supported for a long time for win98 that is long since dead in terms of support.

---

### Post by ymra on 2009-05-30
Actually I think he needs fdisk /mbr.  He is running windows 98 not xp.

---

### Post by blueridgedog on 2009-05-30
> **ymra said:**
> Actually I think he needs fdisk /mbr.  He is running windows 98 not xp.

+1...it is the old dos version

---

### Post by lisati on 2009-05-30
[http://ubuntuforums.org/showthread.php?t=1174193](http://ubuntuforums.org/showthread.php?t=1174193)

---

### Post by blueridgedog on 2009-05-30
> **SunnyRabbiera said:**
> Well why unintall ubuntu that will be supported for a long time for win98 that is long since dead in terms of support.

I was curious as well.  What could lure a Ubuntu user to win98...w/o any updates it is virus and sypware magnate.

---

### Post by eugeneisobel on 2009-05-30
> **blueridgedog said:**
> I was curious as well.  What could lure a Ubuntu user to win98...w/o any updates it is virus and sypware magnate.

Ubuntu doesn't run that well on this old computer at 533Mhrtz and 256 memory with 10 gig hard drive.

---

### Post by halitech on 2009-05-30
If you are finding ubuntu on the slow side, try Xubuntu or another distro like Puppy or DSL. I have Xubuntu running on a Celeron 638 with 384 meg of ram and it runs decently. Or even try the LXDE desktop on top of your current ubuntu install and change the DE you log into.

---

### Post by Hendronicus on 2009-05-30
> **blueridgedog said:**
> I was curious as well.  What could lure a Ubuntu user to win98...w/o any updates it is virus and sypware magnate.

I've run it on the internet and I know people who still do it. Most of the viruses and malware around nowadays just go right by, mainly because they're looking for an NT kernel and a whole host of server extensions that Win98 just doesn't have. You can also get the Unofficial Service Pack from Google and fix quite a few things with that. I'm not recommending any of these things, BTW. I'm just saying it's not as crazy as it sounds. I would stongly recommend using at least Firefox 2.x ( 3.x doesn't work well on Win98 ) and ABP+NoScript for browsing, though.

---

### Post by blueridgedog on 2009-05-30
Before giving it the heave ho, consider trying xubuntu...designed with your system in mind.

---

### Post by blueridgedog on 2009-05-30
> **Hendronicus said:**
>  You can also get the Unofficial Service Pack from Google

Now that I have to learn more about.

---

### Post by Hendronicus on 2009-05-30
> **blueridgedog said:**
> Now that I have to learn more about.

[http://www.google.com/search?hl=en&q=Unofficial+Service+Pack&btnG=Google+Search](http://www.google.com/search?hl=en&q=Unofficial+Service+Pack&btnG=Google+Search)

It's the first entry. I've used it. I never had any problems except it won't install if you've used 98lite with the "Win95 shell" option.

---

### Post by which ones pink on 2009-05-31
Dang dude, there are dozens of lightweight Linux distros that will annihilate Win98 (Crunchbang, Fluxbuntu, Puppy, Damn Small, etc.), with Xubuntu being probably the heaviest and most beginner-friendly.  You can also start with a [minimal install disc](https://help.ubuntu.com/community/Installation/MinimalCD) and [build your system from scratch](http://www.psychocats.net/ubuntu/minimal#barebones).

---

### Post by Toshubu on 2009-05-31
> **eugeneisobel said:**
> Ubuntu doesn't run that well on this old computer at 533Mhrtz and 256 memory with 10 gig hard drive.

Hi Eugene,
Sounds like mine...533 celeron; loaded with 255MB of RAM (as much as it can have); 20GB HD...Still using '98SE on it...but mostly for IM and an old email program. HP Pavillion, by any chance? I tried an Ubuntu 8.10 live disk on it..and it was slow....

---

