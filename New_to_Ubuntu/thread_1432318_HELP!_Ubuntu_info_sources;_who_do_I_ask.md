---
title: "HELP! Ubuntu info sources; who do I ask?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by robertlow on 2010-03-17
HELP! Ubuntu info sources; who do I ask?

Using Ubuntu is like having an F-16 parked in the front yard; it's beautiful, but I don't know how to fix it, or even enough experience to ask semi-intelligent questions about HOW.

My experience: (Gained while dinosaurs roamed the Earth) Might help you understand where I'm coming from.  :P

IBM OS & COBOL; taught myself DOS, Basic, Some C (Borland C 1.0 - wrote own Assembler-based I/O routines using DOS & BIOS interrupts.) Did some Win95 tech support (Circa 1997 during the death & destruction of the browser wars when Billy was trying to kill Netscape - uh, that is, COMPETE with Netscape in the market place.) Nothing professional since. 

My goal: The ability to tell the difference between a bug and a broken machine, to fix my machines when they break, & report bugs when detected. In short, I'd much rather pay forward and be a help to others than a pain in the butt like I am now. 

:KS My specific needs:

A. A glossary of Ubuntu & computer terms so I can figure out what the heck you guys are talking about. Is there a glossary source? What's it called? Specifically where & how do I get it? (Them if more than one). Different OS, different terms. It's hard to find the potty when you don't know how to ask.

B. Manual pages: I've heard of them. Where do I get them and how? Can I print them out for reference and study? Are there other resources I should know about and can't name?

C. A Map of Ubuntu: How are the system files arranged? 
1) What files are used for initializing and configuring the system and software? 
2) What tools are available to manipulate these files, and where are they located? Note: I did find the terminal. Now, mostly we sit blinking at each other between my attempts to issue commands and its usual response: 'I don't know what you're talking about.'

D. What are the proper places to ask questions, post comments and form community ties. (I feel confident that Absolute Beginner is the proper place to post this one.)

:popcorn: Final note:
 My SINCERE THANKS to you, the many people who spend your time making our lives easier. Armed with the information you've supplied to others, I've updated the BIOS to make my Dell Dimension machines making them usable under Ubuntu, and have my happy little network up and running. Now it's time to set up a 'break-me' machine and learn how to fly this puppy!

Robert Low

---

### Post by Brandel Valico on 2010-03-17
A) [https://help.ubuntu.com/community/Glossary](https://help.ubuntu.com/community/Glossary)

B) [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/) (You can also type the word "man" before the command in question for example (man apt-get) in the terminal will give you the commands used with Apt-get 

C) [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
1) Sorry no answer off the top of my head
2) Terminal is great (I don't have much else specific. Sure someone will be along soon to give you a great list though

D) General Help is also a great area. As is as you noted Absolute Beginner. The main trick is to make your subject line as specific and clear to the specific issue. Instead of general blanket terms like HELP!!! 

Welcome to Ubuntu sorry I wasn't more help

---

### Post by GSF1200S on 2010-03-17
A. [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

B. Manual pages are accessible by placing 'man' in front of a command. So for instance, im trying to see man pages on the program 'rsync':
```
man rsync
```

C. [http://bookpic.newbooks.com.cn/pic/200610/60497/200610102145035833.jpg]("http://bookpic.newbooks.com.cn/pic/200610/60497/200610102145035833.jpg") This should give you an idea about how the filesystem is layed out.
1/2. APT (Advanced Packaging Tool) helps you install packages. You can access it via the command line (try 'man apt' for a manual entry on APT ;) ). You can also access it via Add/Remove Programs in your Applications menu. Finally, System > Administration > Synaptic Package Manager is an application that manipulates APT and gives you advanced package management.

Mostly, its effort. Youre learning something new and it takes patience. You likely learned windows over time, just as you will Linux. Give it a chance :) Good luck..

---

### Post by robertlow on 2010-03-17
Thanks, Brandel - That is VERY helpful! 
-RL:popcorn:

---

### Post by Brandel Valico on 2010-03-17
Toss out my own thanks to GSF1200S for the cool link to the filesystem layout image. As well as the other info also. Always nice to get more sources of info for my own use.

Your welcome also Robertlow

---

### Post by nerdy_kid on 2010-03-17
for the filesystem, i dont know a lot but this should help you:
_everything_ is accsessable from root (/)  other hard drives end up being mounted in a folder.

/etc/ -- system config, similar to system32 on windows
/etc/init.d/everything that gets run on system startup, includes services
/home/  -- users folder
/usr/share  --similar to Program Files
/usr/lib   -- shared program libraries
/usr/bin  -- program executibles
/sbin/  -- system executibles
/media/  -- place where external devices get mounted (i.e. attached to filesystem) such as cds, ipods, etc.

all your (as a user) config files are in your home folder (/home/{username}, but are hidden by default.  Press ctrl-h to see them (press it again to hide)

hope this helps :)




<edit> dang it didnt see the image GSF1200S posted; after typing that all out!  im an idiot :S  i like that image though, i think im gonna learn some cool stuff from it thanks :)

---

### Post by 2hot6ft2 on 2010-03-17
The Ubuntu help pages provide a lot of information on many things
[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

Here are few others while some are a bit dated they are still helpful.
Helpful things to bookmark for future reference.

Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Everyone asks coming from windows
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Customizing and apps
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)

Learning Linux
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

Troubleshooting, multimedia and misc help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

Welcome and enjoy

---

### Post by GSF1200S on 2010-03-17
> **nerdy_kid said:**
> for the filesystem, i dont know a lot but this should help you:
_everything_ is accsessable from root (/)  other hard drives end up being mounted in a folder.

/etc/ -- system config, similar to system32 on windows
/etc/init.d/everything that gets run on system startup, includes services
/home/  -- users folder
/usr/share  --similar to Program Files
/usr/lib   -- shared program libraries
/usr/bin  -- program executibles
/sbin/  -- system executibles
/media/  -- place where external devices get mounted (i.e. attached to filesystem) such as cds, ipods, etc.

all your (as a user) config files are in your home folder (/home/{username}, but are hidden by default.  Press ctrl-h to see them (press it again to hide)

hope this helps :)




<edit> dang it didnt see the image GSF1200S posted; after typing that all out!  im an idiot :S  i like that image though, i think im gonna learn some cool stuff from it thanks :)

np ;) You cover some information I left out though- 2 minds are better than one :)

---

### Post by GSF1200S on 2010-03-17
> **Brandel Valico said:**
> A) [https://help.ubuntu.com/community/Glossary](https://help.ubuntu.com/community/Glossary)

B) [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/) (You can also type the word "man" before the command in question for example (man apt-get) in the terminal will give you the commands used with Apt-get 

C) [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
1) Sorry no answer off the top of my head
2) Terminal is great (I don't have much else specific. Sure someone will be along soon to give you a great list though

D) General Help is also a great area. As is as you noted Absolute Beginner. The main trick is to make your subject line as specific and clear to the specific issue. Instead of general blanket terms like HELP!!! 

Welcome to Ubuntu sorry I wasn't more help

Been in the community awhile and never even realized the glossary existed. I guess I rely on google to solve my problems/questions too often. 

And WOW on the TOME of a post by 2hot6ft2 :)

---

### Post by 2hot6ft2 on 2010-03-17
> **GSF1200S said:**
> Been in the community awhile and never even realized the glossary existed. I guess I rely on google to solve my problems/questions too often. 

And WOW on the TOME of a post by 2hot6ft2 :)
TOME? I saved a lot of links over time. I had to remove a couple, one for being irrelevant to 9.10 and one where the link no longer worked.

---

### Post by GSF1200S on 2010-03-17
> **2hot6ft2 said:**
> TOME? I saved a lot of links over time. I had to remove a couple, one for being irrelevant to 9.10 and one where the link no longer worked.

Still alot of good information :) Just because you saved the links over time doesnt make you listing them any less valuable ;)

---

### Post by 2hot6ft2 on 2010-03-17
> **GSF1200S said:**
> Still alot of good information :) Just because you saved the links over time doesnt make you listing them any less valuable ;)
I agree, some are great for learning more about Ubuntu and Linux in general.

---

### Post by robertlow on 2010-03-17
My thanks to GSF1200S, nerdy_kid, 2hot6ft2, and again to Brandel Valico. This info is more helpful than any of the books I've seen on the subject, most of which were out of date before I opened the cover, and so non-specific that they were largely useless. Cool map. Great tips - and probably useful to others besides me.

Gonna be BUSY for a while! Happy time! :KS:lolflag:

---

### Post by Brandel Valico on 2010-03-18
As cliche as it sounds.... Thats what Ubuntu is all about.

What does Ubuntu mean?
> 
Ubuntu is an African word meaning 'Humanity to others', or 'I am what I am because of who we all are'. The Ubuntu distribution brings the spirit of Ubuntu to the software world.... Thats what Ubuntu is all about.

We got helped, At least I know I did, when we first switched and had questions. So now we help answer others questions. (Well I'm starting to be able to do so more and more) Someday you will get a chance to do so also. Us helping you and them having helped us. Will make it easier for you to do so. On down the line and growing and spreading outward. 

Yep that does sound cliche. But it works... Got us all this great free OS after all.

---

