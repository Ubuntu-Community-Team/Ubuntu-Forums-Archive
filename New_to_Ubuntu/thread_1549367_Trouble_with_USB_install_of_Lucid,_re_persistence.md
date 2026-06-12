---
title: "Trouble with USB install of Lucid, re: persistence"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by revol xnyl on 2010-08-09
Hello all.

I recently installed 10.04 on a 4gb USB drive for my Dell Inspiron 1521 using the Universal USB Installer.  I chose a 1gb partition for the persistent option.

Everything went according to plan, and I was able to get my broadcom wireless up rather painlessly by extracting the firmware to the appropriate folder...

But then, I changed my repository settings, updated, and ran 
sudo apt-get install ubuntu-restricted-extras

[FONT=Verdana]to begin getting everything functional, and BAM.  I ran out of space.  

I have plenty of drive space on the internal hdd of the laptop, but i don't know how to proceed with this.  I want to boot from the USB, and have a persistent install, and i suppose i need a partition on the internal hdd for saving configuration and settings.

How do I do this?
[/FONT]

---

### Post by revol xnyl on 2010-08-09
Do I need to supplement this post with additional information to get a reply? 

I feel like the post is Lucid and coherent, is it not?  

I really just want to be able to configure some things and have them stick...

I'd love to boot from the USB and have y browser just how I want it, and have my wireless drivers remain installed, etc.

Is there something simple I'm overlooking?  Any links that might help?  I know how to search, and I read quite a bit - I just can't seem to find any help with this... 

I am a *newb*, after all.

---

### Post by cloyd on 2010-08-09
There may be other answers, but I'd suggest that you either 1) go get a 16 or 32 gig flashdrive, or better 2)see if you can't free up about 50 gig of free space on your hard drive, install Ubuntu and dual boot your machine. Flashdrives boot terribly slow. You can really appreciate some of Ubuntu's advantages if it is actually installed on your computer.

---

### Post by revol xnyl on 2010-08-09
> There may be other answers, but I'd suggest that you either 1) go get a  16 or 32 gig flashdrive, or better 2)see if you can't free up about 50  gig of free space on your hard drive, install Ubuntu and dual boot your  machine. Flashdrives boot terribly slow. You can really appreciate some  of Ubuntu's advantages if it is actually installed on your computer.     To be honest, I'm not as newb as I could be.  I've been dicking around with linux for some time, have dual booted, have been keeping up with the newest iterations of ubuntu for a while.  I've played with lots of livecds and have installed puppy and dsl and other distros in the past.  

I've only just recently decided what i REALLY want.  And that is to have NO OS on the internal hdd of my laptop.  I want to be able to boot into Lucid from USB and run windows in virtualbox when necessary (if necessary), and run any other winblows apps via wine. 

I'd like to have the hdd of the laptop partitioned such that there is space for config stuff, storage, swap and other necessities, but no active OS.

I really like booting Lynx from USB, and I've found it to be much faster than my xp boots, and faster than any previous install of linux i've ever done, whether Ubuntu or other.  Speed is not really an issue.

Furthermore - I have Zero dollars to spend on this - I haven't paid my rent yet this month, and i have tremendous debt.  So no, I won't be buying anything.  Especially when i know that what i want to do is possible.  Besides, is your response really in keeping with the spirit of Linux in general?  "Go buy something" isn't really the best response....

Thanks.

PS - I'm not looking for solutions to all of those problems i just expounded upon.  All I'm looking for from this thread is a tut or some examples of how to go about having a persistent install from a USB drive, such that I'm not limited to the 4gb available on the flash drive.

Any takers?

---

### Post by cloyd on 2010-08-09
Gosh, I don't know if I can help. I do know that I have a pretty complete installation on 9.5 gig. Perhaps you could use an 8 gig or 16 gig drive . . . but that does cost. However, I wonder . . . what if you put your home partition on the hard drive?  I don't know how much this would help. I do know that about 5 gig of my 9.5 is on another partition because I moved my home folder to another partition. If you are not a real noob, then you know that this involves more than just moving the folder. Any other suggestions?

---

