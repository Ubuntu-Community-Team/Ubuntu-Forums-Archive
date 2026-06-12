---
title: "Focus Problems in Fresh Wubi Installation"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by offthecane on 2010-12-14
I installed the 64-bit version of Ubuntu 10.10 using Wubi, and completed the installation. As soon as I saw the desktop, strange things started happening on the desktop.

I opened a Firefox window and I found that I couldn't move the window around, nor could I use my mouse in the window at all. My keyboard works fine, but I can't press any buttons or select anything with the mouse. Nor can I select something on the desktop, rubber band around anything in the desktop, open any other applications, or otherwise interact with the mouse.

Closing the program with Alt-F4 gives me mouse control again.

A similar thing happens with all other open programs: when I try to give focus to another window, I'm not able to select anything on the desktop or in any window with my mouse, and am forced to close whatever program originally had focus.

Ubuntu 10.10 is what I have running now, but I had the same problem with 10.04, installed using Wubi, again on a fresh installation.

I really don't know what's causing this, and it's frustrating me to no end because it's a fresh installation and the effects are difficult to put into words.

Hopefully this rings a bell with someone somewhere who can help me; seems like it would just be a settings issue or possibly something wrong with Wubi itself, but I don't know where to look.

---

### Post by Rubi1200 on 2010-12-14
Hi and welcome to the forums :)

Where to start troubleshooting?

1. try turning off Compiz (desktop effects)

2. what graphics card do you have?

3. try another mouse or try changing settings in BIOS for mouse and keyboard

4. what version of Flash are you using?
Look here for more information: [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

5. check this out: [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Basically you need to try a few things in order to narrow down what may be causing this.

Hope this helps.

---

### Post by nhasian on 2010-12-16
I'm having the same issue as offthecane.  On a fresh install of Ubuntu 10.10 (64bit) and booting from a thumbdrive all is fine.  However, after doing the updates, my left click on my laptop's touchpad stops working.  Well it mostly stops working.  Its hard to describe.  I can move the mouse around but the mouse focus doesnt seem to work.  I can't click on most things but i can click on some things.  See its hard to describe.  For example I can launch firefox but then i cant click on anything anymore until i close firefox by pressing Alt-F4.  I cannot even click on the X to close it on the widget on the toolbar.  I noticed that during the updates it made some changes to the dbus.  I'm guessing maybe thats where the problem lays?  I just have a basic intel video adaptor in this laptop, and the problem persists whether or not compiz is enabled.

---

