---
title: "Monitor Problem"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by kc0iv on 2009-12-11
First let me say I'm as green as you can get with Ubuntu.

I install 9.10.  This is a stand alone system (no other operation system).  All went well with the exception of one problem which I will try to explain.

The computer is a homebrew creation. The Video Controller is a "Silion Integrated System" VGA compatible.  Product: 86C326 5598/6326.

The monitor, Compaq q-1859, doesn't seem to work correctly.  BTW on this same system when it was running Win XP the screen worked correctly. It also worked on my old CRT monitor. Only reason I got the Compaq was the screen was to small. 

When the system powers up the monitor says " Input signal out of range -- 1366 x 768  60hz"  

Looking at Display Preferences the Resolution shows 1366 x 768 (16:9) with a refresh rate of 60 hz. 

What is happening is when I try to scroll any of the screens the display on moves a couple of lines and then appears to disappear.  If I click outside the program and the click back in the scrolled lines appear correctly.

A second part of this problem is white lines appear on the screen, outside the program, when a program starts and doesn't go away.

---

### Post by adaucourt on 2009-12-11
> **kc0iv said:**
> First let me say I'm as green as you can get with Ubuntu.

I install 9.10.  This is a stand alone system (no other operation system).  All went well with the exception of one problem which I will try to explain.

The computer is a homebrew creation. The Video Controller is a "Silion Integrated System" VGA compatible.  Product: 86C326 5598/6326.

The monitor, Compaq q-1859, doesn't seem to work correctly.  BTW on this same system when it was running Win XP the screen worked correctly. It also worked on my old CRT monitor. Only reason I got the Compaq was the screen was to small. 

When the system powers up the monitor says " Input signal out of range -- 1366 x 768  60hz"  

Looking at Display Preferences the Resolution shows 1366 x 768 (16:9) with a refresh rate of 60 hz. 

What is happening is when I try to scroll any of the screens the display on moves a couple of lines and then appears to disappear.  If I click outside the program and the click back in the scrolled lines appear correctly.

A second part of this problem is white lines appear on the screen, outside the program, when a program starts and doesn't go away.

have to drop your resolution try 800x600 or 1024x768

---

### Post by kc0iv on 2009-12-11
> **adaucourt said:**
> have to drop your resolution try 800x600 or 1024x768


I tried every setting and none worked.

Any other idea?

Leon
(kc0iv)

---

### Post by joes7 on 2009-12-11
> **kc0iv said:**
> I tried every setting and none worked.

Any other idea?

Leon
(kc0iv)

Does your monitor has a "SET/AUTO" button? If it does, simply press it. It will create a resolution and apply it so that it fits your screen.

---

### Post by kc0iv on 2009-12-11
> **joes7 said:**
> Does your monitor has a "SET/AUTO" button? If it does, simply press it. It will create a resolution and apply it so that it fits your screen.

That didn't work either.

It has to be some thing in the operating system that isn't set right since it worked fine in Win XP.

---

### Post by Sensiva on 2009-12-11
Read this carefully it may help. [http://ubuntuforums.org/showpost.php?p=8482381&postcount=17](http://ubuntuforums.org/showpost.php?p=8482381&postcount=17)

---

### Post by kc0iv on 2009-12-12
> **Sensiva said:**
> Read this carefully it may help. [http://ubuntuforums.org/showpost.php?p=8482381&postcount=17](http://ubuntuforums.org/showpost.php?p=8482381&postcount=17)


Thanks for the information.

What I found was there wasn't a xorg.conf file.

Followed the instructions. Moved the file to the /etc/X11 folder.

The system detected the correct monitor and video card per the xorg.conf file.

Problem is the problem is still there. Any other suggestions?

---

### Post by halitech on 2009-12-12
personally from what I've seen of SiS cards, get a new card, either ATI (above the HD2400 series) or an Nvidia card. SiS isn't very Linux friendly so it's a pain to get things working. An ATI or Nvidia card should work properly for you with little headache.

---

### Post by Sensiva on 2009-12-12
If this is your monitor " [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01732348&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3911875](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01732348&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3911875) "

Horizontal scan range 24-83  KHz
Vertical scan range 50-76  Hz

Then the following settings should be added  in xorg.conf
 Horizsync 24.0-83.0
 Vertrefresh  50.0-76.0

---

### Post by Sensiva on 2009-12-12
> **halitech said:**
> personally from what I've seen of SiS cards, get a new card, either ATI (above the HD2400 series) or an Nvidia card. SiS isn't very Linux friendly so it's a pain to get things working. An ATI or Nvidia card should work properly for you with little headache.

I had the same headache with Intel GFX chipsets , but it can be solved after all, only Microsoft products that costs new hardware, Not Linux... Not Ubuntu ;)

---

### Post by halitech on 2009-12-12
> **Sensiva said:**
> I had the same headache with Intel GFX chipsets , but it can be solved after all, only Microsoft products that costs new hardware, Not Linux... Not Ubuntu ;)

I know it can be solved but next update/upgrade could break it all again leaving the OP very frustrated where a cheap card could cause a lot less headache :)

---

### Post by kc0iv on 2009-12-12
> **Sensiva said:**
> If this is your monitor " [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01732348&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3911875](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01732348&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3911875) "

Horizontal scan range 24-83  KHz
Vertical scan range 50-76  Hz

Then the following settings should be added  in xorg.conf
 Horizsync 24.0-83.0
 Vertrefresh  50.0-76.0

That is the monitor I have.

Now would some one tell me how to add this to my xorg.conf file.  Please remember I brand new to ubuntu. I have only work with Win.

As to getting a new card I'll look into it once I get a feel for what I am doing.

Hope I'm getting  close to an answer.

---

### Post by hobo14 on 2009-12-12
Follow steps 3 and (relevant parts of)4 here: [http://ubuntuforums.org/showthread.php?t=1346125]("http://ubuntuforums.org/showthread.php?t=1346125") (don't skip step 3)

---

### Post by Sensiva on 2009-12-13
> **kc0iv said:**
> That is the monitor I have.

Now would some one tell me how to add this to my xorg.conf file.  Please remember I brand new to ubuntu. I have only work with Win.

As to getting a new card I'll look into it once I get a feel for what I am doing.

Hope I'm getting  close to an answer.

Great! now you are few steps away, editing xorg.conf instructions are explained here [http://ubuntuforums.org/showpost.php?p=8482381&postcount=17](http://ubuntuforums.org/showpost.php?p=8482381&postcount=17)

You said you read it already :D

---

### Post by kc0iv on 2009-12-13
> **Sensiva said:**
> Great! now you are few steps away, editing xorg.conf instructions are explained here [http://ubuntuforums.org/showpost.php?p=8482381&postcount=17](http://ubuntuforums.org/showpost.php?p=8482381&postcount=17)

You said you read it already :D

my xorg.conf shows the following:

Section "Monitor"
   #DisplaySize      410   230    # mm
   Identifier   "Monitor0"
   VendorName   "CPQ"
   ModelName    "Compaq Q1859"
   HorizSync    24.0 - 83.0
   VertRefresh  48.0 - 76.0
   Option        "DPMS"
EndSection

which I understand is the same thing.

---

### Post by Sensiva on 2009-12-13
to edit xorg.conf 
gksudo gedit /etc/X11/xorg.conf

then reboot

---

