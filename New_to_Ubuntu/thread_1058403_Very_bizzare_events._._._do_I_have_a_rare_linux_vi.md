---
title: "Very bizzare events. . . do I have a rare linux virus?!?!"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-02-02
I know it is unlikely, but I am having some weird things going on.

Firstly, the hotkeys on my key board only function for 32 seconds exactly after boot, than there is no response if they are pressed.

Next, if my computer has been running for exactly 36 hours, it freezes and a small yellow box with the text "Genghis Khan Murderer"  replaces my mouse pointer.  If I reboot, I get another 36 hours operating time until it happens again.

I'm not sure what to make of this.  None of my data has been damaged so far.

What should I do?

I am running a fully updated Ubuntu 8.10 on a Dell laptop.

EDIT: I have no unusual processes running.  This hasn't happened to any of my other Linux boxes.

---

### Post by pi.boy.travis on 2009-02-02
This can not be a virus.  I have done some searching, and there is no such thing as a genghis khan virus.  I seriously doubt that I would be the first one to ever get a brand new Linux virus.

However, I am at a loss as to why these things happen, especially at such an exact time each and every time.

---

### Post by cdtech on 2009-02-02
> I seriously doubt that I would be the first one to ever get a brand new Linux virus.

Someone has to be first........

---

### Post by mhh91 on 2009-02-02
i've never heard of what you're experiencing :|


congratulations,you've discovered a new virus :D

---

### Post by pi.boy.travis on 2009-02-02
> **cdtech said:**
> Someone has to be first........


This is true, but I have a pretty secure system.  I have a hardware firewall, in addition to UFW on each machine.  I use gmail (which automatically sorts spam) and the junk feature in Evolution.  I keep root disabled, and I haven't had to use sudo in about a week.

---

### Post by W2IBC on 2009-02-02
umm, strange

i just find this very odd

> 
if my computer has been running for exactly 36 hours, it freezes and a small yellow box with the text "Genghis Khan Murderer" replaces my mouse pointer


---

### Post by Crafty Kisses on 2009-02-02
I'd suggest you posting your kernel logs, maybe that will help a bit:
```
/var/log/kern.log
```

---

### Post by pi.boy.travis on 2009-02-02
> **mhh91 said:**
> i've never heard of what you're experiencing :|


congratulations,you've discovered a new virus :D

I would certainly hope not, but better me than someone who doesn't do routine backups. . . ;)

---

### Post by MarblePanther on 2009-02-02
Have you made enemies with any of your friends lately, or do you have someone who's been at your computer physically?

Could be someone playing a prank.  I'm curious as to how you came to figuring out this whole 36 hours thing.  This all sounds like an april fool's post.  :)

---

### Post by p_quarles on 2009-02-02
Did you install anything from outside the official repositories? Something from a Launchpad PPA, even? 

Something that does this would be very easy to sneak inside other code. I'm not sure I would even call it a virus, but a simple trojan like this is trivial to create. The difficult part is getting people to install it, and that is where I would look first in a case like this. Is there anything you installed that could account for the timing of this problem?

---

### Post by cdtech on 2009-02-02
I would start by checking for rootkits:
sudo apt-get install chkrootkit

---

### Post by Crafty Kisses on 2009-02-02
> **MarblePanther said:**
> Have you made enemies with any of your friends lately, or do you have someone who's been at your computer physically?

Could be someone playing a prank.  I'm curious as to how you came to figuring out this whole 36 hours thing.  This all sounds like an april fool's post.  :)
That's what I was exactly thinking at first, I mean it sounds like if someone had physical access to the box, which is obviously a way someone can do this.

---

### Post by MarblePanther on 2009-02-02
> **cdtech said:**
> I would start by checking for rootkits:
sudo apt-get install chkrootkit

Yes good idea, you can try 

sudo apt-get install rkhunter           

for double checking chkrootkit

---

### Post by izizzle on 2009-02-02
Hey. Sounds to me like a virus. Download this here:[http://www.clamav.net/download/](http://www.clamav.net/download/)

Run a scan and see if it catches anything.

---

### Post by MarblePanther on 2009-02-02
Does clam even have sigs for the few linux viruses?  I don't know that it does.

This sounds more like a trojan embedded in software he may have installed, a rootkit, or some kind of prank.  I would be suspicious if it is a virus.

It would be top of the technology headlines if it is a virus.

Doesn't hurt to check though...

---

### Post by pi.boy.travis on 2009-02-02
No, this is not a joke, and I always lock my screen when I am away.  I change my password frequently, and to the best of my knowledge no one knows it.  I can not post my kernel logs, as the forums recognize too many of the characters as smiley faces, and I am limited to eight of them.  I'm stumped. . . 

I have no additional repositories enabled, and about a week ago I installed a deb for Virtualbox.  I get the 36 hour info from the power history page I usually keep open in one worksapce, which I managed to switch to using the keyboard.

---

### Post by Simian Man on 2009-02-02
I agree that this is just a prank.  See if anyone put any kind of scripts in your /etc/init.d or your gnome session settings.  If I was going to prank someone, that's how I would do it.

---

### Post by MarblePanther on 2009-02-02
Put your log into a .txt file and attach it.

and i mean it might be a prank someone is pulling on you, not that you are pranking us.

---

### Post by pi.boy.travis on 2009-02-02
I already scanned for rootkits and with clamAV.  I'll have to check for weird scripts. . . 

Thanks for the quick response.  Ubuntu community excellent as normal!

---

### Post by pi.boy.travis on 2009-02-02
I am getting this error when I try to post my kernel log:

kern.txt:
Your file of 675.7 KB bytes exceeds the forum's limit of 19.5 KB for this filetype. 

I just can't win today. . . . :P

---

### Post by MarblePanther on 2009-02-02
try compressing it into a tar.gz and minimizing the fonts first, might not be enough to get it down to that limit though.  perhaps you could upload it to megaupload or rapidshare or something?

---

### Post by p_quarles on 2009-02-02
> **pi.boy.travis said:**
> I already scanned for rootkits and with clamAV.  I'll have to check for weird scripts. . . 

Thanks for the quick response.  Ubuntu community excellent as normal!
While I know that those were well-meaning suggestions, rootkit and virus detection software is a completely ineffective way of approaching this kind of issue. It's likely that looking for anything "suspicious" is also going to be a bit of a wild goose chase with no real results, but a lot of time spent looking. The reason is simple: if a trojan was able to embed itself in your system with root access, it's going to be better at hiding itself than you are at looking for it. 

Again, I would say the place to start is by listing any software you may have installed from outside the official repositories, as well as any software from anywhere that you installed right around the time this began happening.

---

### Post by pi.boy.travis on 2009-02-02
> **p_quarles said:**
> While I know that those were well-meaning suggestions, rootkit and virus detection software is a completely ineffective way of approaching this kind of issue. It's likely that looking for anything "suspicious" is also going to be a bit of a wild goose chase with no real results, but a lot of time spent looking. The reason is simple: if a trojan was able to embed itself in your system with root access, it's going to be better at hiding itself than you are at looking for it. 

Again, I would say the place to start is by listing any software you may have installed from outside the official repositories, as well as any software from anywhere that you installed right around the time this began happening.

OK, here is all the software I have outside the repos:

truecrypt
VirtualBox
Miro
guvcview
Windows version of Opera, running in wine

Most of these have been installed for quite some time now.

I think my hotkey issue is due to an overcrowded USB hub, as they work again if I directly connect my keyboard to the laptop.

I'll be approaching the 36 hour mark again soon. . .

---

### Post by albinootje on 2009-02-02
> **pi.boy.travis said:**
> 
I am running a fully updated Ubuntu 8.10 on a Dell laptop.

Can you make a clone of your hard disk first, with CloneZilla or partimage ?

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.clonezilla.org](http://www.clonezilla.org)

Then use the live session of your Ubuntu installation cdrom, and then run rkhunter and chkrootkit from that (install them first into RAM).

---

### Post by pi.boy.travis on 2009-02-02
[ATTACH]101967[/ATTACH]

there is my kernel log, finally!

---

### Post by pi.boy.travis on 2009-02-02
> **albinootje said:**
> Can you make a clone of your hard disk first, with CloneZilla or partimage ?

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.clonezilla.org](http://www.clonezilla.org)

Then use the live session of your Ubuntu installation cdrom, and then run rkhunter and chkrootkit from that (install them first into RAM).

This partition is huge, but I can put some folders in a .tar.bz2
which ones would you need?

I do keep backups, would a clean install be easier?

---

### Post by albinootje on 2009-02-02
> **pi.boy.travis said:**
> This partition is huge, but I can put some folders in a .tar.bz2
which ones would you need?

I do keep backups, would a clean install be easier?

It would make sense to make a "clone" of everything except your data in /home, but try to include all dot files in /home
So... if you've backed up all your movies, music, VirtualBox guest vm vdi files etc. then make a clone of the resulting files.

Beware that to run rkhunter and chkrootkit you probably need to tell the software where your / partition is, which would be your mounted / partition from your laptop, and not the live cd files itself.

You can do a clean install after you've made the exact clone if you like, otherwise we can close this thread right away ;-)

---

### Post by pi.boy.travis on 2009-02-02
I think I have figured it out!

I left my computer running with Evolution open.  As it turns out, I get the HowStuffWorks newsletter, and Genghis Khan Murderer was the title of one of the articles.  I found it with gmail search.  I had some VMs running, and truecrypt was formating a virtual disk.  I must have run out of memory or something like that.  The 36 hour mark was where the power history graph must have stopped. . .  I have had this happen before, so the 36 hour stopping point must be some kind of coincidence, or maybe a bug in the power history app. . . ?

Lesson learned: don't run Windows XP, Windows 7 beta, truecrypt, and power history all at the same time, and don't overload your USB hub!

---

### Post by albinootje on 2009-02-02
The resulting mouse pointer you've got could have an asian background.
[http://www.asiafinest.com/forum/index.php?showtopic=65042&st=120&p=1582091&#entry1582091](http://www.asiafinest.com/forum/index.php?showtopic=65042&st=120&p=1582091&#entry1582091)

And after a quick look at your kernel logfile I didn't see anything interesting, except this :
> 
Feb  1 14:32:03 travis-laptop kernel: [ 2713.819216] compiz.real[6533]: segfault at d6000f ip 08055c8c sp bf997460 error 4 in compiz.real[8048000+34000]
Feb  1 17:01:26 travis-laptop kernel: Inspecting /boot/System.map-2.6.27-11-generic

Is that after 36 hours ?

---

### Post by pi.boy.travis on 2009-02-02
> **albinootje said:**
> The resulting mouse pointer you've got could have an asian background.
[http://www.asiafinest.com/forum/index.php?showtopic=65042&st=120&p=1582091&#entry1582091](http://www.asiafinest.com/forum/index.php?showtopic=65042&st=120&p=1582091&#entry1582091)

And after a quick look at your kernel logfile I didn't see anything interesting, except this :

Is that after 36 hours ?



I don't think so. . . but compiz could have played a part.

I can't seem to mark the thread as solved. . . is that feature gone?

---

