---
title: "How do I mount an SD card that isn't automatically?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by master5o1 on 2008-12-12
I have an SDHC card that did mount a few days ago but now isn't mounting automatically and I do not know how to mount it more manually.

Here's the stuff from the syslog when I pop it in the laptop.
(image)

---

### Post by theozzlives on 2008-12-12
I have a Dell Inspiron 1525 and sometimes I gotta insert my SD a couple times before it'll mount

---

### Post by -kg- on 2008-12-12
Can you see it as a drive in Nautilus ("Computer" under "Places" on the top launch bar under Gnome)?  If so, double click on the icon and that will mount the card.

---

### Post by master5o1 on 2008-12-12
kg -- no I can't.

---

### Post by master5o1 on 2008-12-12
It does automatically mount an regular SD card but not this SDHC one anymore.

---

### Post by -kg- on 2008-12-12
That's really weird.  According to your syslog, the system is recognizing it's presence, so I can't imagine why you can't "see" the card somehow.

I'm pretty sure there's a command that you can use in terminal to mount a device or drive (mnt), but I'm not sure how to use it and how to set it up so that it auto-mounts.

Yep, open a terminal window and type "man mount", which will give you the manual entry for the "mount" command.  You may be able to find out something there.

---

### Post by master5o1 on 2008-12-12
I so I insert and remove the SDHC card and then I insert and remove a normal SD card and here is the syslog.

---

### Post by -kg- on 2008-12-12
Just wondering...could the SDHC card have lost it's format?  I notice that the regular SD card shows 128 MB at one point in the mounting line, but the SDHC shows nothing at all.  Do you have another computer that you could check that on?

I'm trying my best.  I'm a relative newby myself, though not to computers.  Been into computers since the early '80s, before there was Windows!  Linux is new to me, though.

---

### Post by master5o1 on 2008-12-13
I do not have another machine with an SD slot so no.  Both of them show their sizes in KiB so I doubt it has anything to do with the missing 4GB vs the 128MB label in the log.

---

### Post by master5o1 on 2008-12-26
does 'bump' work here?

---

### Post by shecky on 2008-12-26
You could try:
```
sudo mount -t vfat /dev/mmcblk0p1 /mnt/
```
Where "vfat" is what I am guessing the card is formatted as. If it mounts, your stuff's in the */mnt/* folder. If it comes back as the wrong filesystem type, try some others.

---

### Post by kansasnoob on 2008-12-26
Not sure with that card but I've had good luck with "pmount".

```
sudo apt-get install pmount
```

I've found it helps auto mount many drives and cards - even cameras!

[http://en.wikipedia.org/wiki/Mount_(Unix)#pmount](http://en.wikipedia.org/wiki/Mount_(Unix)#pmount)

---

### Post by kuckunniwi on 2011-01-17
-kg-:

I'm having the same problem with an 8Gb SDHC card on a brand new HP mini 110 3050ss running Kubuntu Lucid 64-bit.I've been using the same card ever since I got it on my 2 year-old Clevo laptop, and I've never had any problems, neither in Ubuntu Lucid 64-bit, nor in Kubuntu Maverick 64-bit, which is what I'm running now. I thought it may be a defective filesystem, but I tried it on the ol' clevo and it worked fine. It seems odd that the card would work on a 2-year-old laptop but not on a brand new netbook.

I suspect the issue may be related to the card-reader drivers under Kubuntu 10.04, as I've had problems with both WLAN and audio drivers on this netbook, which I had to install manually (which was quite an adventure for a newbie such as myself!).

For now, I guess I'll have to stick to the SDHC > laptop > pendrive > netbook procedure while I continue looking for the solution, hoping an upcoming system update will come along and fix the problem...

---

