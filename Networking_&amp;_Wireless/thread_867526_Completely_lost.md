---
title: "Completely lost"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by zeke13 on 2008-07-22
Do I need to be a computer programmer to use Linux? I have been a frustrated microsoft user since the late '80s. I tried using Linux a few years ago but it didn't have a GUI & there were very few applications avalible. I have now installed Ubuntu & have a similar problem to the one posted by deshpreetsbedi. Unfortunatly after reading the thread, I am scratching my head in confusion. How do I get to the command line? How do I extract a filename.tar.gz file? After I extract it how do I open the application? Is it going to be this difficult to download & install every application? Please don't flame me, I am just trying to find out how difficult this is going to be. I have been searching the web for info, but y'all appear to have your own language, and I can't find a dictionary to aid in understanding it!  Thanks in advance for any help.

---

### Post by sofasurfer on 2008-07-23
I'm not good enough to tell how to unzip a tar.gz but I can tell you that if I can do it you can to.

Open a terminal by going to the button at the lower left of your screen. Its like the windows "start" button. Follow it to applications>accessories>terminal.

Hint: go to [www.ubuntu.net](www.ubuntu.net), click the "free documentation" button and start exploring. That will keep you busy for weeks.
And keep it simple till you learn the basics.

---

### Post by tamoneya on 2008-07-23
here are the three easiest ways to get command line:
1.  Hit alt-F2 and type ```
gnome-terminal
```
2.  Applications -> accessories -> terminal
3.  Hit ctrl-alt-F1 to go to tty1.  To get back to the desktop hit ctrl-alt-F7.

As for extracting a .tar.gz put the following command into terminal. (assume the file is in /home/username/Desktop/ and is called file.tar.gz)

```
cd /home.username/Desktop
tar -xvzf file.tar.gz
```

---

### Post by sputnikkk on 2008-07-23
System --->  Administration --> Synaptic Package Manager is your friend as well.

Its like "Windows Update" on steroids but not just for security patches - hehehe ....

You can search the global repositories for all different types of softwares and patches and excellent things.  It adds and removes apps, and can GUI'ize the unzipping and compiling of install apps code for you [in many cases]  I guess you dont recall DOS eh? 

Im 2 weeks into this and its pretty good so far.  There are a few things I find frustrating - like SOOOO much command line syntax being required, but ya get the hang of most of it quickly.

The Open Office apps for Word Processing and Spreadsheets[excel] - which read and write the Micro$oft equivelent files and types is pretty sweet as well.  Im huge into using PDF as the final format of Word and Excel proposals.  Wish I would have realized how far along these Open Office apss were some time ago.

Ive got $1,000 of dollars in M$ Office licenses and Adobe Acrobat FULL VERSIONS - like 15 seats worth!!!!

Once I find a robust email client - I think I'll be MONEY.

Video sound and peripherals seem harder to get working - but mostly because the hardware mfg'rs dont put forth the same effort to support the linux OS as they do M$

Im converting the whole home LAN as I can.  Im starting on the kids fun machines - nothing mission critical yet. They think the Compiz-Fusion desktop customizations are outta sight - and their friends thinks its some SUPER COmputer thats the "pimp shizzle".  All 5 yr old hardware - crusty and rusty - but Linux works on it great.

Good luck man ...

---

### Post by tamoneya on 2008-07-23
> **sputnikkk said:**
> 
Once I find a robust email client - I think I'll be MONEY.

Depending on what type of email server you are using you should give thunderbird a try.  Its much better than evolution and its very robust in my opinion.

---

### Post by Gallienus on 2008-07-23
Zeke13, to extract a tar.gz file, all you need to do is double click on it. That should open the archive manager automatically. As far as installing programs goes, if you're a beginner, I recommend that you stick to programs available ready to download in Ubuntu's repositories for now - it will make life a lot easier for you. You can add these through the menu option Applications -> Add/Remove...

---

### Post by zeke13 on 2008-07-23
> **tamoneya said:**
> Depending on what type of email server you are using you should give thunderbird a try.  Its much better than evolution and its very robust in my opinion. I use Thunderbird in Windows, so I downloaded & extracted it in Linux, but I can't figure out how to open it!

---

### Post by Sealbhach on 2008-07-23
> **zeke13 said:**
> Do I need to be a computer programmer to use Linux?  Not these days. Anyone can use Ubuntu. Seriously.

> **zeke13 said:**
> 
 How do I extract a filename.tar.gz file? After I extract it how do I open the application? Is it going to be this difficult to download & install every application?  

You will rarely have to do this - most packages can easily installed by clicking from a list (see Add/Remove Programs in the menu).


> **zeke13 said:**
> Please don't flame me, I am just trying to find out how difficult this is going to be. 

They don't do that on this forum, they're really nice to noobs.


.

---

### Post by forger on 2008-07-23
> **zeke13 said:**
> How do I get to the command line? How do I extract a filename.tar.gz file? After I extract it how do I open the application? Is it going to be this difficult to download & install every application?

Installing applications is easy:
Ubuntu menu Applications > Add/Remove... (the bottom option)
You can browse through the available software from there.

Note: You have to have administrator privileges (or the first user when it was installed) to install anything.

---

### Post by tamoneya on 2008-07-23
> **zeke13 said:**
> I use Thunderbird in Windows, so I downloaded & extracted it in Linux, but I can't figure out how to open it!

like you were saying before it is best to use synaptic package manager.  Install it from there and it will be in applications-> internet.

---

### Post by decoherence on 2008-07-23
> **Gallienus said:**
> Zeke13, to extract a tar.gz file, all you need to do is double click on it. 

You can also right-click the file and select "Extract Here." Very handy.

---

