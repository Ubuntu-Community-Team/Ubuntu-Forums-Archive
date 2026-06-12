---
title: "How do I mount a CD-ROM drive?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by lukeinvancouver on 2009-04-23
I don't know much about Linux and  hope somebody can help me with this problem. 

I'm building a system for somebody who hasn't used a computer in all is life and who also doesn't have much money. It's an old clunker (Celeron 300A) but for learning basic mouse skills, find out how to use windows (minimising/maximising etc etc), learn how to use OpenOffice etc etc it's OK.

When I put an audio disk into the CD-ROM drive on my new machine (Intel Atom) the drive is mounted automatically. An icon appears on the desktop and Rhytmbox Music Player is launched automatically. The music plays just fine.

When I put an audio disk into the CD-ROM drive of the old clunker (Celeron 300 A) the disk spins in the drive for “an eternity” then stops and there is no way I can play the music. ( I played some music yesterday from an internet radio station so the sound is working.) The drive is a 48X Max. ( I doubt this stands for Maxtor.)

I should say that this CD-ROM comes from a machine I found in the lane and took apart to recycle everything useful. It seems to be working because when I put the Ubuntu Live CD in it, it launches it. (Both when the machine is already running or when booting up from the CD-ROM.) So it seems to me that the drive is working.

It's connected to the MB as a Master.

I have not yet mounted a drive (filesystem?) manually. I have a book about Fedora but assume that these commands are the same for all distros.

Is the following correct:

I assume I open Terminal.

According to the book I enter:
mount -t iso9660 

Problem no1: What is the name of the data source, i.e. CD-ROM drive? (I can't find it in the book)
Problem no2: What is the mountpoint?
Problem no3: Do I need to do something first, e.g. create a folder for the mountpoint? (If that makes any sense.)
Problem no4: What is the command to enter in Terminal (if that is the app to use)?

In the help files I only get a reference for tape drives and "installing from mount".

Searching here yields 'sorry no matches found'.

Just to let you know that I tried.

Any help would be much appreciated and it would also benefit somebody on welfare (the guy I want to  give the machine to).

Thank you in advance.

---

### Post by Peter09 on 2009-04-23
Your CD should mount automatically. It may be that your CDrom drive is one of a limited few that Ubuntu has trouble with.

CDROMS are normally mounted on /media/cdrom. Have a look there and see if the CDROM is mounted.

---

### Post by Kobalt on 2009-04-23
I assume your drive is working and configured correctly, if you say you used it with an Ubuntu Live CD and you can access this CD from Ubuntu.
The problem may reside in your CD itself : is it an original or burned CD? If it's an orignial, is it copy-protected (OpenDisc or something like this)? Have you tried with other original/burned CDs?

---

### Post by James_Lochhead on 2009-04-23
The easiest way to mount a CD is to use the GNOME panel mount applet. It will then be mounted under /media/<something>.

---

### Post by lukeinvancouver on 2009-04-23
> **Peter09 said:**
> Your CD should mount automatically. It may be that your CDrom drive is one of a limited few that Ubuntu has trouble with.

CDROMS are normally mounted on /media/cdrom. Have a look there and see if the CDROM is mounted.

Thank you.

There are two folders there one called cdrom and the other cdrom0. The first one has an arrow at the right top corner pointing upwards towards the right.

I have no idea what this means.

Nothing happens when I open either one, I mean no files are listed.

The CD is one with mp3 files I burned on a Windows machine. It works on the Atom machine, mounting automatically and launching the player.

A commercial Deutsche Grammophon disk plays on the Celeron. Both machines are running the same version of Ubuntu

Thanks for helping

:guitar:

---

### Post by lukeinvancouver on 2009-04-23
> **Kobalt said:**
>  Have you tried with other original/burned CDs?

Cool!

It works with a commercial Deutsche Grammophon disk but not with one, or another one, I burned on my Windows machine.

However the mp3 disk I burned myself launches automatically and plays on my Atom machine. That one has a LG DVD drive

Thank you so much for your help.
:)

---

### Post by lukeinvancouver on 2009-04-23
This forum is the best I have ever been to.

Thank you all so much!!!!!

---

### Post by steve101101 on 2009-04-23
just so you know the arrow indicated that its a link to another location.

---

### Post by lukeinvancouver on 2009-04-23
> **James_Lochhead said:**
> The easiest way to mount a CD is to use the GNOME panel mount applet. It will then be mounted under /media/<something>.

Would you please tell me where I can find it and how to install it?

Clicking on "add to panel" it does not appear in the list.

Thank you in advance.

---

### Post by lukeinvancouver on 2009-04-23
> **steve101101 said:**
> just so you know the arrow indicated that its a link to another location.

Dumb question Steve: What is it pointing to?

---

### Post by Peter09 on 2009-04-23
Try right clicking on the panel and selecting 'add applet' - select the one you want.

---

### Post by Peter09 on 2009-04-23
Its called 'Disk Mounter'

---

### Post by lukeinvancouver on 2009-04-23
Since the homemade disk plays in one machine and not the other, is it reasonable to assume that if I changed the drive where it doesn't play that it would work then?

---

### Post by Peter09 on 2009-04-23
May be - some very old CDROMS had difficulty reading the CD-RW disks, or perhaps the CDROM drive that does not work needs its lens cleaning - its always worth a try.

---

### Post by Dileeshvar on 2009-04-23
what I do is 

```
cd /media

mount cdrom
```

This works when my DVD is not auto mounted :)

---

### Post by lukeinvancouver on 2009-04-23
> **Peter09 said:**
> May be - some very old CDROMS had difficulty reading the CD-RW disks, or perhaps the CDROM drive that does not work needs its lens cleaning - its always worth a try.

Thanks.

I'll have ot get a lens cleaner first and then I'll try.

---

### Post by lukeinvancouver on 2009-04-23
> **Dileeshvar said:**
> what I do is 

```
cd /media

mount cdrom
```

This works when my DVD is not auto mounted :)

Thank you.

Do I do this in Terminal? (Sorry about the dumb question, but I'm a real beginner)

---

### Post by lukeinvancouver on 2009-04-23
> **Peter09 said:**
> Its called 'Disk Mounter'

Thanks again
:)

---

### Post by lukeinvancouver on 2009-04-23
> **Peter09 said:**
> Its called 'Disk Mounter'

It's there allrught and coming to think about it I ahd tried before adding it to the panel but it doesn't do anything.

:confused:

---

### Post by Dileeshvar on 2009-04-23
> **lukeinvancouver said:**
> Thank you.

Do I do this in Terminal? (Sorry about the dumb question, but I'm a real beginner)

yes of course :)

applications-->accesories-->terminal

---

### Post by lukeinvancouver on 2009-04-23
> **Dileeshvar said:**
> yes of course :)

applications-->accesories-->terminal

Thank you. Now I know.

:)

---

