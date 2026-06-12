---
title: "Live CD problem on Dell Dim. 2400"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by NoJobyDesert on 2009-03-28
Got an old Dell Dimension 2400 with 512 RAM.

In an attempt to run the live cd, I just get a black screen with a working mouse pointer.

I am able to get all the way through the boot screen and it stops at a black screen with mouse.

Any ideas?

---

### Post by NoJobyDesert on 2009-03-28
Oh, and the version is 8.10

---

### Post by greatpaul on 2009-03-28
I have a dell 2400 as well. It could be the video card. I had that problem at first. Is it internal or an PCI one?

---

### Post by MyR on 2009-03-28
you have to log in using resuce or whatever the option is (to the command line)

then uninstall compiz

```
sudo aptitude remove compiz compiz-core
```

then 
```
exit
```
and you'll be able to log in normally

---

### Post by prematurebaby on 2009-03-28
Have you tried safe graphics mode?

---

### Post by PenguinsFan on 2009-03-28
Check for a bad disc. At the boot menu, choose "Check CD For Defects"

---

### Post by MyR on 2009-03-28
safe graphics mode accomplishes the same thing as removing compiz.

while it is a good practice to check to make sure the disc is good, it is unlikely that it is bad in this case.

---

### Post by NoJobyDesert on 2009-03-28
Sorry, I should probably mention that it is a Windows machine.

I checked the CD for defects, it was OK.

It should not be a graphics problem as I did get a white screen for a few seconds before black, as well as a mouse pointer and the "busy" circle pointer for a few seconds.

I can try safe graphics mode, but how do I start it?
There is not such option on the 8.10 disc.

---

### Post by presence1960 on 2009-03-28
> **NoJobyDesert said:**
> Got an old Dell Dimension 2400 with 512 RAM.

In an attempt to run the live cd, I just get a black screen with a working mouse pointer.

I am able to get all the way through the boot screen and it stops at a black screen with mouse.

Any ideas?

A friend with a Dimension 2400 had the same problem. He wound up using the alternate text based installer. You can get that as separate download from the Get Ubuntu link on the Ubuntu web page.

---

### Post by Shibblet on 2009-03-31
I also have the Dell Dimension 2400.  There are a few different flavors of this unit...

The one I have has 512M Ram, and a Celeron 2.0Ghz processor.

The solution for me was not to use the onboard video.  The Intel Graphics 82845 was made specifically for this Dell Dimension, and only has functioning Windows XP drivers.  (Load Vista on it, I dare ya... ;))

The onboard graphics adapter shares usable memory with the rest of the computer.  And for some reason, this confuses Ubuntu.

The best solution is to go down to your local computer store and get a $20.00 PCI (not PCI-E) video card, and then fire that sucker up.  Problem solved.

It worked for me!  (Huked on fonix werkt fer mee!)

---

