---
title: "Overcomplicated installation instructions"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by welwitschia on 2011-01-06
Just some food for thought...

As a new user I have noticed that some Linux users clearly prefer coding by default (which I completely understand despite my own skills being inadequate) and others prefer using user friendly ways of doing things. Especially in installing software.

Yesterday something really absurd happened to me, because of this thread (and due to my own ignorence):

[http://ubuntuforums.org/showthread.php?t=1658404](http://ubuntuforums.org/showthread.php?t=1658404)

and these instructions:

[http://www.fewt.com/2008/06/how-to-g...g-in-wine.html]("http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html")

I had the Microsoft Office 2007 setup.exe-file and wine and had already successfully installed all the programs, but because I was so dumb that I didn't know they would go into Applications>Wine>Programs (instead of Applications>Office) I kept on going with the instructions given in [www.fewt.com]("http://www.fewt.com"), which included copy pasting code into GNOME etc. stuff I don't REALLY understand. 

Many hours later I noticed the programs had been there all along.

So for all the other newbies out there, if you want to install Microsoft programs:

1. Install "Wine" from Applications>Ubuntu Software Centre (optionally PlayOnLinux works too).
2. Modify setup.exe-file by right-clicking icon Properties>Persmissions and ticking "Execute: Allow executing file as program".
3. Open setup.exe-file with Wine and let installation take its course. Then you will find the programs "within" Wine in Applications>Wine.

---

### Post by mastablasta on 2011-01-06
sound kind of logical that if you install something inside WINE (which is sort of an emulator) that any possible shortcuts would be in the WINE folder, no?
 
maybe they should make it a bit clearer on what WINE is exactly.

---

### Post by welwitschia on 2011-01-06
> **mastablasta said:**
> sound kind of logical that if you install something inside WINE (which is sort of an emulator) that any possible shortcuts would be in the WINE folder, no?
 
maybe they should make it a bit clearer on what WINE is exactly.
Indeed.
:P

---

### Post by Wtower on 2011-01-06
On the other hand, it is about the common issue that windows users expect windows behaviour in Ubuntu. I believe that installing software in any Debian-based distro as Ubuntu is, is far easier and far more cost-effective procedure than anything else. I wouldn't like to get into more comparison details. Installing a windows application in Linux is by definition still very hard to be easy. Not to mention, why would anyone like to use msoffice before critically evaluating Ubuntu alternatives. In my experience, 9 out of 10 users that want to still use msoffice is mostly a matter of habit rather than some feature lacking in Ubuntu.

---

### Post by mastablasta on 2011-01-06
> **Wtower said:**
>  Not to mention, why would anyone like to use msoffice before critically evaluating Ubuntu alternatives. In my experience, 9 out of 10 users that want to still use msoffice is mostly a matter of habit rather than some feature lacking in Ubuntu.
 
2007 has some new and exciting features :-P
 
seriously it does have some good features that OO lacks. they can be a real help if you have more text and need to edit it faster. we had to go through video showing and giving tutorial of some new features. while some are just not worth mentioning others are really great.

---

### Post by welwitschia on 2011-01-06
> **Wtower said:**
> Not to mention, why would anyone like to use msoffice before critically evaluating Ubuntu alternatives. In my experience, 9 out of 10 users that want to still use msoffice is mostly a matter of habit rather than some feature lacking in Ubuntu.

I agree that in many ways OpenOffice can be better than Microsoft Office (I had to Download OpenOffice when still using a Windows OS, because of a dataset that was too large for Excel!). But EVERYONE else uses Microsoft and if you want to be able to work with their files (e.g. comments in a word-file) Microsoft Office is necessary, because Open Office is not compatible with that feature (comments get all messed up). If the compatibility with the Microsoft files was better...

---

### Post by fuduntu on 2011-01-06
> **welwitschia said:**
> Just some food for thought...

As a new user I have noticed that some Linux users clearly prefer coding by default (which I completely understand despite my own skills being inadequate) and others prefer using user friendly ways of doing things. Especially in installing software.

Yesterday something really absurd happened to me, because of this thread (and due to my own ignorence):

[http://ubuntuforums.org/showthread.php?t=1658404](http://ubuntuforums.org/showthread.php?t=1658404)

and these instructions:

[http://www.fewt.com/2008/06/how-to-g...g-in-wine.html]("http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html")

I had the Microsoft Office 2007 setup.exe-file and wine and had already successfully installed all the programs, but because I was so dumb that I didn't know they would go into Applications>Wine>Programs (instead of Applications>Office) I kept on going with the instructions given in [www.fewt.com]("http://www.fewt.com"), which included copy pasting code into GNOME etc. stuff I don't REALLY understand. 

Many hours later I noticed the programs had been there all along.

So for all the other newbies out there, if you want to install Microsoft programs:

1. Install "Wine" from Applications>Ubuntu Software Centre (optionally PlayOnLinux works too).
2. Modify setup.exe-file by right-clicking icon Properties>Persmissions and ticking "Execute: Allow executing file as program".
3. Open setup.exe-file with Wine and let installation take its course. Then you will find the programs "within" Wine in Applications>Wine.

The difference between the shortcut in your applications menu, and my instructions (which are possibly even out of date since they are 2 years old) is that with my instructions you associate word documents with the executable so you can double click a document in nautilus and it opens with MS Office.

If you don't need that, by all means just use the menu icons.

---

### Post by welwitschia on 2011-01-06
> **fuduntu said:**
> The difference between the shortcut in your applications menu, and my instructions (which are possibly even out of date since they are 2 years old) is that with my instructions you associate word documents with the executable so you can double click a document in nautilus and it opens with MS Office.

If you don't need that, by all means just use the menu icons.

I understand that now (finally). I've realised that it was my own stupidity that I didn't think to look in Wine>Programs. 

Just for curiosity's sake, does anyone know of a newer set of instructions for doing that?

---

