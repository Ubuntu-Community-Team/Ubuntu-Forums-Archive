---
title: "To Ubuntu or not to Ubuntu"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by gv29847 on 2009-01-18
Having watched Linux ocasionally from afar for a long time, I just decided to see if I could swap one of my four systems over, and chose Ubuntu 8.1 to try.

The PC I chose is a Dell Optiplex which is just used as a backup organiser under XP Pro. The basic scheme is that the other PCs on my network dump onto the Dell once an hour. The Dell pushes this info into what is effectivelly a complicated queue. To do this it runs a set of overnight scheduled folder to folder clones i.e. just updating where necessary - not full copying. (If you happen to be familiar with FolderClone (Windows only) that's what I am using.) The schedules differ acording to the day of the week and the whole thing runs through daily, weekly and monthly cycles.  So can I do this simply with Ubuntu or an available app? This is my key question - I don't want to spend time resolving what follows only to find it is a pain to get this task performed.

Before you advise me to use Ubuntu to look for stuff, please be aware of the following.
1. I have tried booting from CD, originally this worked fine - except it took around 45 minutes! I was able to look at files both locally and on the network, open .pdf and .doc, run FireFox etc. 
2. However I noticed that I was not getting the BIOS screen during the boot - presumably because there is a mainboard video driver and a pci one and I had the monitor on the later. However when I switched the monitor to the mainboard video, and removed the plug in card, and booted from the CD again I get 
2.1. the BIOs screen, 
22. Ubuntu comes up with an a screen with its name and the circle thingy, and then the "Try Ubuntu ...", "Language", and the horizontal ping pong,
2.3. then a whole series of SQUASMFS errors, and Buffer i/o error on device sr0...., 
2.4. then it does a default log on to unbuntu since it is not responding to keyboard text
2.5. Eventually comes up with "Internal Error. Failed to Initialise HAL!" Return does not close this window, but CtrlC recycles back to 2.4.
2.6. CtrlAltDel does a graceful shutdown and XP starts up.

I guess the sr0 is a drive, which would be strange since XP sees no drive errors. I also suppose I could put the video card back and see if I get back to being able to get back into Ubuntu but just now that seems like more hassle that may go nowhere!

3. I also had a problem with sharing the drives on the network - but I have read some stuff about being a superuser instead of an administrator which is supposed to allow me to fix this. (I could see out on the network from Ubuntu when it ran, but not in from the other pcs.)

Anyway because of these three issues it is not easy / fun to get Ubuntu up and running to play with - hence my seeking advice before spending more time.

Peter

---

### Post by cmnorton on 2009-01-18
To me, if you have an application running -- and it sounds like it is running successfully -- regardless of the OS or hardware, the last thing I would try to do would be port that application over to another platform, and I speak from experience. 

Just porting applications from rpm-based Linux to Debian (Ubuntu) Linux has its own little nuances. For starters, I had to change all my bash shell scripts that had #!/bin/sh to #!/bin/bash on the first line. Debian links /bin/sh to /bin/dash, and dash does not behave just like bash.

As to booting,if it took 45 minutes, something is terribly wrong. The Ubuntu Live CD is nice, but sometimes you have to play with it, and start it up in text mode (cannot remember all the options).

I had a W2K server IIS application running on an old Pentium II. It was slow, but it worked, and I moved it to a new Windows server system, only when I had to, and that was just moving to new hardware, same OS.

---

### Post by jimmy the saint on 2009-01-18
I kind of agree with cmnorton on the "if it ain't broke" mentality.  On the other hand, I like the fact that since I switch to Linux a few years ago (and spent a lot of that time breaking/fixing/learning) my systems simply don't break like they used to under windows.

If you want to install ubuntu on that system and the normal cd is giving you grief, you can try the alternate install cd.  It is a text based (you still get menus and just use arrow keys, spacebar and enter) and often works when the live cd won't because it skips the x-session. You could try dual booting first so that you can mess around with it without losing your working system.  In fact, I would highly recommend it since you seem to have a well configured system doing its job well.  It would be a shame to sacrifice your working tool to experimentation, only to have to set it up all over again!  This way if it doesn't work for you, you can just delete the new partition with no harm done.

Before you do so, make a disk image using something like acronis, norton ghost or (my favorite) clonezilla.  That way you have a complete backup with no risk of having to start over.  An ounce of prevention is better than a week of beating your head agains the wall

---

### Post by gv29847 on 2009-01-18
Thanks for the advice guys - but can you please tell me if there is an app which will do the schedules cloning I refered to? Or can it be done 'native' in Ububtu?

Peter

---

### Post by laffinet on 2009-01-18
I don't know an awful lot about this, but I think you should be able to achieve what you're looking for with a scheduled 'rsync' job.

Rsync lets you copy/transfer/synchronize directories I believe. Combined with 'cron'  (scheduling under Ubuntu) this should work. Or 'anacron' if the machine isn't running all the time.

You might have to google a bit (lots to be found), or start a new thread that solely devoted to your scheduled job (make sure you describe in the title what you want to do and you should get heaps of help).

---

### Post by gv29847 on 2009-01-18
OK thanks, that's enough to encourage me to see if I can get past the boot stuff. And I take your point about focussing the title!
Peter

---

### Post by oldos2er on 2009-01-18
Regarding your difficulties with the LiveCD, the first thing you should do is to run 'Check CD for defects' from the first menu. Also, could you post your machine's hardware specs?

---

### Post by Talon2 on 2009-01-18
Is there a RAID controller in the system?

---

### Post by gv29847 on 2009-01-18
PC is a Dell Optiplex GX110, 800 MHz Pentium III, with 512 Meg RAM, and C = 10G, D = 120 G, E = 120 G (All IDE), F = CD burner 52x read, G = 500 Gig USB hard drive. No RAID.

So I thought - why indeed I should run the CD check. However this time - looking round from my day job every now and then - I must have missed that screen, cos now it's running Ubuntu! Nothing at all was changed - but here it is!. Next time I will make a note to look when that screen is expected and run the check. Another day - its 45 mins a pop here!

---

### Post by gv29847 on 2009-01-19
While Ubuntu was running I thought I would get back to the networking thing. On Ubuntu I can see the other pc's and their shared drives. On the other (XP) PC's I can see Ubuntu and "Printers and Faxes" but none of the drives on the Ubuntu pc. How do I make a Ubuntu drive or folder visible to - amd writable to - the networked pc's?

---

### Post by HavocXphere on 2009-01-19
The LiveCD's speed is not a realistic representation of what the finaql install will be like. If the CD drive sucks a bit (e.g. the CD drives in laptops) then the experience is a bit painful because everything slows down to a crawl.

45min does sound a bit heavy though.:( 10-15mins would be more on target.

You could also try installing ubuntu on top of the XP install (google Wubi) so that its easier to return to XP.

---

