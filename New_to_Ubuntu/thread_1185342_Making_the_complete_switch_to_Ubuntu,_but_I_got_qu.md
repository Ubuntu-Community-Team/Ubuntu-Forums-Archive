---
title: "Making the complete switch to Ubuntu, but I got questions..."
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-12
I love Ubuntu in the sense it's lightweight and has a simplistic but awesome look. Put that together with compiz fusion and it's great.

I know it's not Windows, but I don't want it to be windows.
I'll be running 9.04 with virtualbox and XP or vista inside that for the software that's only windows based.
I was wondering, will I be able to use my Logitech Quickcam software and webcam within the virtualbox without problems? (So long as, yes, Ive installed guest additions)

and same goes with most of my Windows stuff. Will it communicate with my hardware through a virtualbox properly, and work with the software?

Also is virtualbox recommended, or is there something that will perform better? Even if it's paid. I just need a solution to run windows and linux together.
I don't really wanna dual boot anymore, which is why I need a good virtual solution.

Also, I have a core 2 duo and 4gb ram...
I guess I should choose 9.04 x64 yes?
I'm just not sure if it's really that compatible, or if it should be fine.

---

### Post by kpkeerthi on 2009-06-12
I would recommend VirtualBox for two reasons:
1. I find the guest OSes quite snappy on VirtualBox
2. Its very easily to install. Download the latest deb file from VirtualBox's website and double-click to install. 

Yeah, go for x64.

Not sure about your Logitech thing.

---

### Post by kendoori on 2009-06-12
I also endorse VirtualBox. I've built a relatively light weight XP image and it starts up fast and runs well when I need it.

---

### Post by HavocXphere on 2009-06-12
> **Gp. said:**
> Will it communicate with my hardware through a virtualbox properly, and work with the software?
As a general rule, anything involving 3D acceleration will not work 100% through virtualbox. Games & Compiz will be hit & miss.

Should be fine otherwise. The x64 vs x86 thing is less of a hassle on linux than windows x64 vs x86.

> Logitech Quickcam software and webcam
Probably. Not sure. Make sure you get the right Virtualbox version...there is one with usb support and one without.

Would be helpful to know what falls under "Windows stuff" for you.

---

### Post by Gp. on 2009-06-12
> **HavocXphere said:**
> 
Would be helpful to know what falls under "Windows stuff" for you.

Things like WLM, the logitech software for my keyboard, mouse and webcam, Adobe CS4 Suite, nothing gaming related. I understand what kind of a switch I'm making.
I don't game much anymore anyway lol

---

### Post by 3rdalbum on 2009-06-12
I don't know what WLM is. Not all of us have used Windows lately so you might have to clarify what it is and what it does, to get an answer of whether it'll work. Of course, you could just try it :-P

The Logitech software for your keyboard and mouse will most likely not work. Virtualbox will emulate a generic PS/2 keyboard and mouse to the guest OS. You can pass your webcam through to the guest OS if you have the non-open-source version of Virtualbox, so Windows and its software will be able to see the webcam for what it is, and control it directly. While Virtualbox is passing your webcam through to the guest OS, it will not be available in the host OS.

Guest operating systems don't see the underlying hardware, so don't try to install graphics card drivers or anything. Virtualbox emulates "generic" hardware (Soundblaster audio, some old sort of Ethernet card, VESA graphics etc) except for what you pass through. Windows should work alright with this emulated hardware.

+1 for 64-bit Ubuntu - your processor and RAM will love it, and it's indistinguishable from 32-bit when you're using it. Unless Virtualbox has changed recently, you'd still need 32-bit Windows as the guest.

---

### Post by Gp. on 2009-06-12
Ok, I'm trying to install Filezilla...
Need some help!
When I try from the Add/Remove Applications manager it says it's not supported for my system type (amd64)
How can I get filezilla working on x64 Ubuntu?

---

### Post by Elfy on 2009-06-13
Hi - instead of using Add/Remove, try it from the command line - it works here

```
sudo apt-get install filezilla
```

---

### Post by Gp. on 2009-06-13
Cheers!
Got another question.

With drive mounting...
When I go to Places and choose the drive I want to access, it then automatically mounts it and the drive icon appears on the desktop and I can access it.

But how can I have my drives permanantly mounted so after restart it will always be mounted even before I click onto it from places. If you get what I mean?
Also is there an application or tool to make these settings easier.

And what other essential ubuntu tools would you recommend. I have ubuntu tweak which is a good little one, what others do you recommend for a variety of tasks? Put it this way. What tools could you not do without whilst running ubuntu!

Really wanna get into this :)

---

### Post by Elfy on 2009-06-13
Hi - I've got another answer ;)

You can do that with graphical tools - pysdm is in the repos - it works with linux partitions at least, not sure about windows ones - long time without now.

```
sudo apt-get install pysdm
```

It appears in the System Admin menu - Storage Device Manager, if it doesn't work with ntfs, use ntfs-config

```
sudo apt-get install ntfs-config
```

That gets put in System Tools - that does work with ntfs

While it is nice and easy to use these if you get stuck and need to edit the files in recovery then you'll need to get your hands dirty :D 

IF you feel like it - copy your fstab file before you mount the drives then have a look afterwards to see what gets changed 

```
cat /etc/fstab
```

Fstab information here - have a look sometime [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


I tend to not use graphic tools so can;t answer that really ;) Ubuntu tweak for instance changes things in gconf-editor - I go there ... 

As far as tools I could not do without - the terminal :lol:

---

### Post by Gp. on 2009-06-13
Ok sweet I'll do that too.
Also I was wondering, is ext 4 worth it over ext 3?
It's installed with ext3 because I used default installation settings, but I'm wondering if I should reinstall with ext4?

---

### Post by Cresho on 2009-06-13
ext4 is still being tweaked so stick with ext3.  Nothing wrong with ext4.

---

### Post by Gp. on 2009-06-13
Well say I hadn't installed Ubuntu yet, would you recommend 3 or 4? lol

---

### Post by Elfy on 2009-06-13
I'd say ext4 - I've not had any issues with it - others who have might not though :)

---

### Post by Gp. on 2009-06-13
What kind of problems are people having with it?

---

### Post by Elfy on 2009-06-13
I'm not too sure to be honest and I won't get into FUD ;) it's also possible thatthose I saw were during the jaunty development.

As I said I'm using it and have had no issues - what I wouldn't bother doing is reinstalling just to get ext4.

---

### Post by Gp. on 2009-06-13
What are the actual advantages with ext4 over ext3?

---

### Post by Elfy on 2009-06-13
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1133719](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1133719)

whoops - meant to add that I hope that will answer your question ;)

---

### Post by Gp. on 2009-06-13
Ah cheers.
Think I'll stick with ext3 just because it's more stable right now.

Another question....

How do I go about changing the drive label?



More questions coming! I've made posts asking a a lot but I need a refresh and some went unanswered :P

---

### Post by SunnyRabbiera on 2009-06-13
Pysdm can do it, just be careful.

As for the EXT3 vs 4 debate personally I would use EXT3 until EXT4 gets its bugs worked out, its the data loss issue that makes me reluctant to use it so I think EXT3 is the best way to go for a little while.
We will see how BTRFS fares out if its ever finishes.

---

### Post by Gp. on 2009-06-13
I remember using Pysdm to try and label and it didn't work too well.
It was showing different labels in different spots or something.
I just remember having some weird issue.
Any other ideas?

---

### Post by SunnyRabbiera on 2009-06-13
> **Gp. said:**
> I remember using Pysdm to try and label and it didn't work too well.
It was showing different labels in different spots or something.
I just remember having some weird issue.
Any other ideas?

pysdm is the only GUI way I know of, I never fully manually edited fstab so I dont know much about manually editing it.
The only thing I used Fsab for was my external hard drive but that was ages ago.

---

### Post by Gp. on 2009-06-13
Ok well XP and virtualbox now up and running.
I have no idea how to get my USB devices to work inside virtualbox.
All the USB devices like my printer for example are blanked out and unelectable from the devices menu on the virtual machine window.

Anybody? Help? lol
:D

---

### Post by nandemonai on 2009-06-13
> **Gp. said:**
> Ok well XP and virtualbox now up and running.
I have no idea how to get my USB devices to work inside virtualbox.
All the USB devices like my printer for example are blanked out and unelectable from the devices menu on the virtual machine window.

Anybody? Help? lol
:D

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by SunnyRabbiera on 2009-06-13
You know depending on the make of the printer you might not need the virtual box as much.
If the printer is a HP you might be in good fortune in getting it working.

---

### Post by theozzlives on 2009-06-13
> **Gp. said:**
> I love Ubuntu in the sense it's lightweight and has a simplistic but awesome look. Put that together with compiz fusion and it's great.

I know it's not Windows, but I don't want it to be windows.
I'll be running 9.04 with virtualbox and XP or vista inside that for the software that's only windows based.
I was wondering, will I be able to use my Logitech Quickcam software and webcam within the virtualbox without problems? (So long as, yes, Ive installed guest additions)

and same goes with most of my Windows stuff. Will it communicate with my hardware through a virtualbox properly, and work with the software?

Also is virtualbox recommended, or is there something that will perform better? Even if it's paid. I just need a solution to run windows and linux together.
I don't really wanna dual boot anymore, which is why I need a good virtual solution.

Also, I have a core 2 duo and 4gb ram...
I guess I should choose 9.04 x64 yes?
I'm just not sure if it's really that compatible, or if it should be fine.

If your cam is USB, then it should work. I'd say setup your VirtualBox while you're still Dual Booting, if it don't work for your liking... delete it. I run VirtualBox with WinXP and 7 and it works fine for my purposes.

---

### Post by Gp. on 2009-06-13
Oh I'm on Ubuntu Primarily now.
:D

Any suggestions for a messenger with webcam support?
and a program like the quickcam software to record video with audio and take pictures? Cheese doesn't seem to cut it...

and does anyone know how to turn off Right Light technology for my quickcam pro 9000 in ubuntu...I hate that. It makes everything slow and low shutter speed looking.

And also cheese receives my cams video slow....maybe thats another issue in itself not with cheese but with ubuntu?

---

### Post by SunnyRabbiera on 2009-06-13
There isnt much for cameras right now, Cheese is possibly the best you can get in that area though you might get more suggestions.
As for IM clients that support video you could try kopete, though it will look a little alien.

---

### Post by abhiroopb on 2009-06-13
My logitech cam works perfectly through skype. Did not have to install drivers or anything. Just plugged it in and it worked.

---

