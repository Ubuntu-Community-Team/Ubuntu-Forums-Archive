---
title: "Can't get past initial boot menu in installation"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by weatherhelm on 2010-01-20
I am new to Ubuntu and am trying to get it to work on an old PC that I have. I have a working 9.10 Desktop CD (I know because I tried it on another machine and it worked just fine.) I have gotten my machine to boot up off the CD and I have the normal menu screen with options - Try Ubuntu, Install, etc. Yet when I select any of these, a window pops up titled "Boot Loader" displaying some short text like LIVE or INSTALL depending on what I've chosen and an "OK" button. If I hit enter I just go back to the main menu. ?????? 

Here are my system details:
Abit KT7A motherboard
AMD 1000mhz processor
~512mb RAM
I have 2 hard drives connected to the system but neither has a working OS on it.
Just updated the BIOS to the latest version
Not sure what else to include...

I've also tried the Alternative CD and 9.04, but the exact same thing happens. I've also tried all the Boot Paramateters that are suggested in the guide. Same thing.
Any suggestions would be greatly apreciated!

---

### Post by cariboo on 2010-01-21
HAve you tried starting in Safe Graphics mode? At the menu screen press F4 select Safe Graphics, press enter, then go back to the Main Menu and make your choice of how you want to start. I would suggest using try before installing to make sure all your hardware works properly.

---

### Post by gnometorule on 2010-01-21
Try this:

[http://sourceforge.net/projects/wubi/files/](http://sourceforge.net/projects/wubi/files/)

Only way I got Ubuntu onto my 5 year old laptop. Works like a charm (upgrade to 9.10 easy after installing 9.04 first) - for me at least.

---

### Post by candtalan on 2010-01-21
The CD checked ok in another machne - can it check itself in the target machine? Perhaps not, if you cannot leave the boot menu? Just thiking that the CD drive in the target machine might be old and sticky. Any chance of using another CD drive temporarily in the target machine?

I do not know what would happen if a 64 bit CD was used in a 32 bit computer, but, just a thought?

---

### Post by plucky on 2010-01-21
> I do not know what would happen if a 64 bit CD was used in a 32 bit computer, but, just a thought? 


It boots to the Install/TRY menu,but when you ask it to do something it comes back with a message:-

> This kernel requires an x86-64 CPU,but only detected an i686 CPU.
Unable to boot.Please use a kernel appropriate for your CPU.

---

### Post by weatherhelm on 2010-01-21
Thanks for your suggestions, but I think I've tried every single option available from that screen with the same result. Just that little window with the ok button. Hit it and it closes then I'm right where I started. I'm wondering if there's something set up wrong in my bios. I tried to follow some instructions I found about that (disable shadow ram etc.), but had no effect. I can get to the text prompt by hitting escape. Is there a way to manually start the installer from there? Or maybe I should try a much older version of Ubuntu (tried 9.1 and 9.04 but maybe go back further...)?

Another thing I was wondering; does it matter what state the hard drive is in before running the installer? Will the Live version run without a hard drive?
Thanks!

---

### Post by aljoriz on 2010-01-21
You can try xubuntu. it ran on my Girlfriends' antique pentium2 pc with 256mb ram. Xubuntu has a lower requirement when compared to ubuntu

---

### Post by weatherhelm on 2010-01-22
Success!!!! I finally figured out that the memory in my system was not installed correctly. After switching around the dimms so that they were in ascending order, everything works just fine. Yay!

---

