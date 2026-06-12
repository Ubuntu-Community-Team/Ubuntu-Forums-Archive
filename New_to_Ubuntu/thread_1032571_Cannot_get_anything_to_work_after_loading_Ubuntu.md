---
title: "Cannot get anything to work after loading Ubuntu"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by dandodge1 on 2009-01-06
OK. I have an older Dell Inspiron laptop.  Its about 5 years old, a hand-me down.  It has a Celeron abou 1.5Ghtz processor, 20gb hd, and 512mb of ram.  That is about all the tech specs I know about it.  It didn't come with an OS.  A friends kid was messing around deleted Windows and there solution was buy a new one.

So I installed Ubuntu 8.10 from an ordered CD.  Everything looked like it installed fine.  Went through the whole process time zones, log in, partitioning.  CD drive ejected took out cd.  Restarted got to login screen and put in login and password.  Then the screen turned black with a pointer in the middle and that was it.  I posted a previous thread about this and was told to hit Ctrl+Alt+F1 and it would start in Black and White mode because it sounded like a video driver problem to that person.  It dropped me out to a terminal type screen and asked for login and password.  When I type nothing shows on the screen.  When I hit enter It is extremely choppy and asks for a login again.

I need HELP!! I know nothing about this OS and I am lost at this point.

---

### Post by matthewcadieux on 2009-01-06
im kinda in the same boat, my hard drive was wiped on an old hp media center computer, a real slow one at that, and so since it was wiped i decided to throw ubuntu on there. whenever i try to run it from the cd it asks me for user info and i know it shouldnt, but then after a few seconds it brings me to a blank screen with the ubuntu 8.10 back ground. also, if i try to install it, it flips between that same screen and a blank orange screen and a black screen. anyone please help

---

### Post by dandodge1 on 2009-01-06
After a little more looking I found this thread

[http://ubuntuforums.org/showthread.php?p=6123466#post6123466](http://ubuntuforums.org/showthread.php?p=6123466#post6123466)

worked like a charm.  Thank you jerrylamos!

---

### Post by mapes12 on 2009-01-06
This is what I would do:

1. Firstly,your machines spec is fine for running Ubuntu
2. My preference would be to install 8.04LTS. It has better support.
3. I would start again with the installation but this time run a low level formatting utility across the HDD to get rid of anything windoze may have left there, especially compressed partitions. Here's a link: [http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/](http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/)

---

### Post by theozzlives on 2009-01-06
dandodge1, when you logon and go to the prompt try typing ```
startx
```

---

### Post by matthewcadieux on 2009-01-06
when i get home ill try this...its sounds like what i have going on, except also i cant even get tot the install via live cd, and the install just freezes for me regularily

---

### Post by mapes12 on 2009-01-06
> **matthewcadieux said:**
> when i get home ill try this...its sounds like what i have going on, except also i cant even get tot the install via live cd, and the install just freezes for me regularilyTry the alternate install CD: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

One of my machines hates the Live CD's.

---

### Post by matthewcadieux on 2009-01-06
thanks ill try this, but i was wondering if you might be able to recognize this problem. my comp got wiped via a gparted accident. now ubuntu's live cd will get to the main install interface where it gives you the 4 choices of try it without change, install, and the other two which are spec inspections. if i try it without install, it doesnt ever get to the desktop it just goes to a login screen, but after a while it goes away. then it goes to a series of image, skin colored, and black screens. then and i lefti t for 4 hours and nothing. next i tried to just install it and the program went to the image screen, then after a while there was a white window that read install on the title bar, then that closed and it went through the same series of screens. any ideas?

---

