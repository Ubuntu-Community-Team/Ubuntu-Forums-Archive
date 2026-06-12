---
title: "Guest Additions not working on XP host"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Mr. R on 2010-03-29
I'm using VirtualBox and I need to set up guest additions for a Windows XP guest on Ubuntu, but I'm not sure why it isn't working.

First of all I have guest additions v 1.5.6 downloaded (with a terminal) and in the correct directory. I have it mounted, but it will not display on XP. It still says "CD Drive (D:)" instead of a title.

Also my thumb drives won't work with it. This is fine if I can get shared folders working, but I cannot get shared folders working until I get the guest additions installed.

Sorry if this is asked hundreds of times. I'm better with Windows than Ubuntu, so I just think there is some configuration issues with VirtualBox or Ubuntu.

---

### Post by Mr. R on 2010-03-29
OK, partly solved. It turns out I was supposed to use v2.0.6. It was outdated.
I want this open until I can get help getting the USB devices to work.
Also, I have already tried enabling it through editing a BASH shell with the terminal. . . didn't help.

---

### Post by mkvnmtr on 2010-03-29
If you are using the latest virtual box from the Sun site the USB will work. If you are using the one out of the repository I unserstand USB is not supported.

---

### Post by bpalone on 2010-03-29
If you are using the OSE version USB is not supported.  For USB support you need to go to [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads") and download the PUEL version.

I also notice that you are using 8.04.  Unless some of the updates have fixed it, you will need to some tweaking of some files.  I can't remember where the details are.  So, you will have to do some searches on the forum.  That is where I found the answers.

Good luck.

---

### Post by Mr. R on 2010-03-29
Yeah. I probably installed VirtualBox with [FONT=Lucida Console]apt-get[/FONT] before I used [FONT=Lucida Console]apt-get update[/FONT]. I can now get version 3.1.6 w/ updated guest additions working well.

---

