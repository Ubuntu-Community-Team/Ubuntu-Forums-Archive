---
title: "Goodbye M$"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by StillOnTheEdge on 2009-10-26
A little background on me: I have been using computers since the Commodore 64s were first brought out, and I am currently employed working on Windows-based PCs 5 days a week.

10 or so days ago, I took the plunge to switch (as completely as possible) to Linux from Windows. I have to tell you that the first several days have been a shock to my system. I was feeling somewhat overwhelmed. I have gotten VirtualServer up and running with an XP box on it for those programs I need to have available while I am getting up to speed with Ubuntu.

Now, I am at least treading water... but I have a bunch of questions. (I have researched these questions at least a little bit, but haven't found any good answers.)

1.) Has anyone had any success getting analog sound from a Hauppauge 1800 TV Tuner card? I had great success getting video from the tuner via TVTime, but no audio over cable or component.

2.) How can I configure my Logitech MX Revolution mouse to have the side buttons mapped to keystrokes like "ENTER" and "ESC"?

3) How can I get my system to use the latest beta of OpenOffice so I can use my Office 2007 documents better? (Preferably with apt)

4) How can I convert my Thunderbird mail from windows into Thunderbird for Ubuntu? Just copying the files to the .thunderbird folder didn't work.

I'm sure there is more, but that is all I can think of right now...

Thanks in advance for all your input.

A little info about my system: 
Ubuntu 9.10 beta 64-bit, upgraded kernel to latest version
AMD Phenom 9850 w/ 8GB RAM
Diamond Radeon HD  4850 512MB video card
SANS DIGITAL TR8M-B 8 Bay Enclosure (and a boatload of drives)
[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816111051")MS Natural Ergonomic Keyboard 4000 & Logitech MX Revolution Mouse
Hauppauge 1800 TV Tuner Card & Hauppauge HD-PVR

---

### Post by philinux on 2009-10-26
It's always best and you'll get more replies with one topic per thread.

It will get really confusing otherwise.

---

### Post by candtalan on 2009-10-26
Welcome!

> 
How can I convert my Thunderbird mail from windows into Thunderbird for Ubuntu? Just copying the files to the .thunderbird folder didn't work.


It basically should work, or at least it does for me. However check that the file profiles.ini is correct for your new arrangement. For example, the new profile content might be
/home/user1/.mozilla-thunderbird/57ejflmh.default

and so your new  profiles.ini files should look appropriate such as

================
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=57ejflmh.default
Default=1
================

hth

---

### Post by StillOnTheEdge on 2009-10-27
Well, so far so good. I have the MX revolution working the way I like it. 

Now just 3 more things to deal with.

---

### Post by bkratz on 2009-10-27
Look here about the 1800 tuner card

[http://ubuntuforums.org/showpost.php?p=6129026&postcount=132](http://ubuntuforums.org/showpost.php?p=6129026&postcount=132)

---

### Post by StillOnTheEdge on 2009-11-03
Just an update on my progress:

1.) IN PROCESS - Has anyone had any success getting analog sound from a Hauppauge 1800 TV Tuner card? I had great success getting video from the tuner via TVTime, but no audio over cable or component.  

2.) DONE - How can I configure my Logitech MX Revolution mouse to have the side buttons mapped to keystrokes like "ENTER" and "ESC"?

3) DONE - How can I get my system to use the latest beta of OpenOffice so I can use my Office 2007 documents better? (Preferably with apt)

4) DONE - How can I convert my Thunderbird mail from windows into Thunderbird for Ubuntu? Just copying the files to the .thunderbird folder didn't work.

I have Wine set up and working with some of my favorite games (Civ4 family), and have more testing to do with Wine programs.

I have a VirtualBox with Windows XP installed for those programs that I "need" that don't play well with Wine (ComicBase and PaperPort being the main ones, and Quicken to make sure everything converted to gnuCash correctly). 

I want to say thank you to all who have helped me along this journey. I believe I am here to stay. 

Now my last request, which will go pro'ly go unfulfilled... Make my OpticBook 3600 scanner work in Ubuntu, and an open source program like PaperPort... :D

---

### Post by ukripper on 2009-11-03
> **candtalan said:**
> Welcome!



It basically should work, or at least it does for me. However check that the file profiles.ini is correct for your new arrangement. For example, the new profile content might be
/home/user1/.mozilla-thunderbird/57ejflmh.default

and so your new  profiles.ini files should look appropriate such as

================
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=57ejflmh.default
Default=1
================

hth

+1, copy the thunderbird files from windows over to ubuntu.

---

