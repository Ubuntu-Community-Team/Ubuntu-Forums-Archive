---
title: "In Wine, how do I run a CD based program?"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by bwallum on 2010-04-21
Hi

I have a windows cd based program that normally runs on XP/Vista simply by inserting the cd into an optical drive.

I have tried to copy files into Wine 'c:' drive through the configuration process but it does not run. I have tried inserting the cd and see what happens. A lot of huffing and puffing noises are made, an icon appears on the Desktop, then nothing. Theicon does nothing when clicked.

Any ideas how to get a windows cd based program working in Ubuntu?

---

### Post by MadCookie on 2010-04-21
> **bwallum said:**
> Hi

I have a windows cd based program that normally runs on XP/Vista simply by inserting the cd into an optical drive.

I have tried to copy files into Wine 'c:' drive through the configuration process but it does not run. I have tried inserting the cd and see what happens. A lot of huffing and puffing noises are made, an icon appears on the Desktop, then nothing. Theicon does nothing when clicked.

Any ideas how to get a windows cd based program working in Ubuntu?

Do you mind telling what program you want to run?

---

### Post by bwallum on 2010-04-21
> **MadCookie said:**
> Do you mind telling what program you want to run?
It's called "Art Deco II" a simple programme for putting backgrounds and patterns together then printing out instructions I gather.

---

### Post by Homicide on 2010-04-21
Have you tried opening the CD and running the EXE?

---

### Post by P4man on 2010-04-21
> **Homicide said:**
> Have you tried opening the CD and running the EXE?

I noticed recently that this no longer works; because the file is not marked as executable, wine refuses to execute it. And you cant mark it as executable because its on a read only filesystem. At least its like that when I mount ISO images, I assume its the same from a CD. 

Whoever thought of that wasnt thinking very hard :S Now i got to extract the ISO's to my harddisk, so i can change the execute permission of the file before I can even test the app in wine. Progress I suppose...

---

### Post by Kellemora on 2010-04-21
I'm following this thread also, because, I have a few old programs I run in wine myself, BUT have never got a single program that requires the CD to be in the drive to run it to work.

I've even went to the extremes of creating a fake drive within wine that contained the CD as is a drive, following some instructions I found somewhere.  It appeared to work for about 5 minutes, until the next scene, then poof, it never worked again after that.

TTUL
Gary

---

### Post by P4man on 2010-04-21
> **Kellemora said:**
> I'm following this thread also, because, I have a few old programs I run in wine myself, BUT have never got a single program that requires the CD to be in the drive to run it to work.

Most of those apps would require the cd to be in there because of copy protection (stuff like SecuROM and other nasty stuff). That usually doesnt work on wine. You need to track down a cracked .EXE  or nocd crack. For games you might find those, for other apps that might get very tricky.

---

### Post by bwallum on 2010-04-21
> Originally posted by P4man
I noticed recently that this no longer works; because the file is not marked as executable, wine refuses to execute it. And you cant mark it as executable because its on a read only filesystem. At least its like that when I mount ISO images, I assume its the same from a CD. 

It is, that's exactly what I'm up against.

---

### Post by user333 on 2010-04-22
I run programs daily from a CD, by browsing the folder and right-clicking the exe file, and clicking "open with wine windows program loader". It works great for me, but it does take some time to load. Maybe the program you want to run needs to be set up for what windows version it is designed for? Just go to Applications> Wine> Configure Wine, and click "add application". Find your program, set it to xp, or whatever you need (experiment for a while, but I find xp works for most things) and then try running it.

Hope this helps you :)

---

### Post by 3rdalbum on 2010-04-23
In the terminal:

```
wine <drag the file you want to run into the terminal>
```

Hit Enter.

---

