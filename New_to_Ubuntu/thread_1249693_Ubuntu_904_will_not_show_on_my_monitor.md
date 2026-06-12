---
title: "Ubuntu 9:04 will not show on my monitor"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by minouper on 2009-08-25
I have upgraded from Ubuntu 8:10 to Ubuntu 9:04.
When I boot or reboot the logo screen comes up and Ubuntu seems
to load OK.
After the line on the logo screen fills up, the screen than flickers to the next starting screen showing the hash lines across the screen, than the screen shows the little white dot several times-like it is loading and than I get a black blank screen.
I can reboot and get into the menu and get to a command line interface which is: root@ken-desktop:~#.  I can run commands from here.  I don't know enough to be able to do much from here though.
I seem to be missing a package and when I go to get it I cannot reach ca.archive.ubuntu.com.
Does anyone have an answer for my problem.
Help is much appreciated.

---

### Post by nick_nik on 2009-08-25
Is you graphics card an ATI Radeon? I had a similar issue with an xorg-driver-fglrx and an ATI Mobilibity Radeon X500
 
If you have the and ATI card and fglrx driver installed try removing it from the command line using
 
```
sudo apt-get remove xorg-driver-fglrx
```
 
then try and restart as normal. 
 
 
Apparently some older ATI cards dont work that well under 9.04

---

### Post by mapes12 on 2009-08-26
Did you upgrade via Update Manager over the internet? If so, I have experienced problems similar to what you are describing. The best way I found to upgrade is with a fresh install from CD-R. Obviously, back up anything you want to keep in /home. If you haven't got /home on its own partition perhaps now would be a good point to do so. It makes everything much easier when carrying out a fresh upgrade. If you need any help with /home on its own partition then please post back.

Mark

---

### Post by Luca_turicci on 2009-08-26
That's why I prefer fresh installations.

Backup your info, and do the /home partition thing, then install from a liveCD

---

### Post by minouper on 2009-08-26
Thsnks for replying.  No, I have a #dbfx video card in a AGP slot and it worked just fine before I upgraded.

---

### Post by NoaHall on 2009-08-26
Try reverting to your onboard driver - it might help.

Removing your AGP card.

---

### Post by minouper on 2009-08-26
Hi, Thanks for replying.  Yes I did upgrade over the internet.  I don't know how to get into my home directory using the command line in order to back it up.

I can't dee anything in the GUI on my screen.

---

### Post by minouper on 2009-08-26
How do I do this?

---

### Post by NoaHall on 2009-08-26
cp /home/ $
Where $ = to where you want to copy the files.

---

### Post by minouper on 2009-08-26
Also, when I try to get something to load, I am getting it from "ca.archive.ubuntu.com" which no longer works.  Apparently, 
"ca2.archive. ubuntu.com" does work, but I don't know how to change to this ?respository?

---

### Post by minouper on 2009-08-26
Sorry, but was does the $ sign stand for?  I am assuming it is a directory? How do I make a directory to copy tyhem to?

---

### Post by LewRockwell on 2009-08-26
we must have missed the previous post regarding the specific makes, models, and build/part numbers of the hardware causing these difficulties

.

---

### Post by minouper on 2009-08-26
How do I revert to my onboard driver?

---

### Post by minouper on 2009-08-26
I did try removing my AGP card.  I installed an old PCI card in its place.  This didn't help either.

---

### Post by LewRockwell on 2009-08-26
> **minouper said:**
> Sorry, but was does the $ sign stand for?  I am assuming it is a directory? How do I make a directory to copy tyhem to?


> **NoaHall said:**
> cp /home/ $
Where $ = to where you want to copy the files.


**_*Where $ = to where you want to copy the files.*_**

.

---

### Post by NoaHall on 2009-08-26
> **minouper said:**
> I did try removing my AGP card.  I installed an old PCI card in its place.  This didn't help either.

You don't have a card built in to the mother board?

---

### Post by minouper on 2009-08-26
No I don't.  I have an older MB, an ASUS P3V133-which worked fine b/4.

---

### Post by LewRockwell on 2009-08-26
> **NoaHall said:**
> You don't have a card built in to the mother board?

why should this/that on-board stuff...always be ASSUMED?

.

---

### Post by NoaHall on 2009-08-26
Ah, okay. A complete reinstall is probably best then.

---

### Post by minouper on 2009-08-26
I read the help Vampire bit and just so everyone knows I have tried to look elsewher at FAQs, Google, Ubuntu help, blogs etc..  My problem is as a newbie I don't know where to look or how to describe things very well yet for Linux/Ubuntu.  I have 3 books on Hacking Ubuntu which I am reading and using.  It is still a steep learning curve for me. I am making progress though, albeit slowly.

---

### Post by LewRockwell on 2009-08-26
> **minouper said:**
> I have upgraded from Ubuntu 8:10 to Ubuntu 9:04.
When I boot or reboot the logo screen comes up and Ubuntu seems
to load OK.
After the line on the logo screen fills up, the screen than flickers to the next starting screen showing the hash lines across the screen, than the screen shows the little white dot several times-like it is loading and than I get a black blank screen.
I can reboot and get into the menu and get to a command line interface which is: root@ken-desktop:~#.  I can run commands from here.  I don't know enough to be able to do much from here though.
I seem to be missing a package and when I go to get it I cannot reach ca.archive.ubuntu.com.
Does anyone have an answer for my problem.
Help is much appreciated.

did you try the 9.04 LiveCD BEFORE you switched?

or did you just do a blind upgrade?

download, md5sum check, slow-burn, and run the 9.04 LiveCD and see how it goes

.

---

### Post by minouper on 2009-08-26
Yes, I did both an upgrade and tied the CD download, used checksum etc to download.  I will try loading the CD again tomorrow.
I tried this and it will not work.
I am at this point: root@ken-desktop:~#

When I try to install my missing files I get a message that says ca.archive.ubuntu.com cannot be reached and I should try ca2.archive.ubuntu.com or another archive that will work.  How do I change to this from this command line: root@ken-deasktop:~#  
I have been reading most of the day and still cannot find out how to do this.

---

### Post by minouper on 2009-08-31
I tried this and it will not work.
I am at this point: root@ken-desktop:~#

When I try to install my missing files I get a message that says ca.archive.ubuntu.com cannot be reached and I should try ca2.archive.ubuntu.com or another archive that will work. How do I change to this from this command line: root@ken-deasktop:~# 
I have been reading most of the day and still cannot find out how to do this.

---

### Post by minouper on 2009-09-01
I have solved the problem about how to change the archives thanks to some very good  help.  You need to use: vi /etc/apt/sources.list 
and go to make the changes in the file
Take a look at
[http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)
for some basics at vi
________________

---

