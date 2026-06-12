---
title: "Enraged sister pulls out power cord. (HELP!?)"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Kafubie on 2010-07-31
Let me tell you good story.. (real obviously)

Couple months ago...
I put Ubuntu 10.04 on my family's computer just a couple months ago.  To combat windows vista home basic, slow as heck.  It is couple years old.

Sister...
 She thinks I 'break' the computer dozens of times. /facepalm...
She doesn't know anything about computers, unless its her mp3 usb plugging in to charge her mp3.

Just 30 minutes ago...
I go on the computer, which seems to be the first time in couple months.  I just checked up on it and **LOW and BEHOLD**, 300 something files added up to 280 mbs in the update manager that never were implemented in the system.

Long story short...
She gets mad at me cause i'm 'ruining the computer'.  I started to install the updates just then and i tell her... "You cannot go on yet, too bad"  She comes back to the computer and pulls out the power cord.  (I stayed cool and started the computer up again)

Problem....
Computers starts up and I get the part of the posting when it has the [OK]'s with the cups and pulseaudio.  With the white and orange asterisks. It doesn't go any farther then that.

What do I do now?  I have the ubuntu 10.04 LTS cd with me.  I started the computer 4 or 5 times.  

Hope you feel a little rage, and please post with suggestions.

---

### Post by adalal on 2010-07-31
Can you get to a terminal by any chance? Hit Ctrl + Alt + F1 and insert your username and password if you can, and then rerun the update. If it comes up as an error, run  sudo dpkg --configure -a, and hope that fixes it.

Let me know is that helps. If not, let me know how far it gets, can you get to the grub screen?

---

### Post by Kafubie on 2010-07-31
> **adalal said:**
> Can you get to a terminal by any chance? Hit Ctrl + Alt + F1 and insert your username and password if you can, and then rerun the update. If it comes up as an error, run  sudo dpkg --configure -a, and hope that fixes it.

Let me know is that helps. If not, let me know how far it gets, can you get to the grub screen?

I tried a couple times, first time i didn't even get to status's screen.  Then next time I did.  I tried to get in the first channel terminal.. Nothing.

3rd attempt: I waited about a minute then tried to get into first terminal.. again.  black screen of nothingness.

Every time i power off, it shows the purple ubuntu splashscreen then shuts down..

---

### Post by adalal on 2010-07-31
> **Kafubie said:**
> I tried a couple times, first time i didn't even get to status's screen.  Then next time I did.  I tried to get in the first channel terminal.. Nothing.

3rd attempt: I waited about a minute then tried to get into first terminal.. again.  black screen of nothingness.

Every time i power off, it shows the purple ubuntu splashscreen then shuts down..

Right, so, by that I'm assuming you can get to the grub screen?

---

### Post by amsterdamharu on 2010-07-31
Could it be it is checking the harddisk with fschk? That might take a while to complete, is the harddisk light active? 

I'd give it at least 20 minutes to complete and then re-try the update either by pressing control+alt+F1 through F7 or by logging in normally if it allows you to.

---

### Post by Kafubie on 2010-07-31
> **adalal said:**
> Right, so, by that I'm assuming you can get to the grub screen?

Not sure what you mean by that.

That computer is not dual booting ubuntu and windows...
Just ubuntu.

Sorry forgot to mention that.

---

### Post by Kafubie on 2010-07-31
ok..  I waited for a bit and went into first terminal..  I didn't see any User name prompt so i put it in anyways just because I wanted to see what it would do..  

I ran the command and some errors were encountered while procesing tzdata-java.

Then did sudo aptitude update
.... then upgrade.

So far it's unpacking packages.

---

### Post by adalal on 2010-07-31
Looks like it was updating tzdata when the plug was pulled maybe? i know you said you don't dualboot, if it is going all the way to trying to load the tzdata, I'm assuming that the kernel is working.

When you turn on the computer, it goes through the Power-on-self-test (POST), and then goes to GRUB. If all you have is Ubuntu on the system, there is a period after the POST, where it says something on the lines of 'Hit ESC to go to grub' for a short while. Hit ESC and go into the recovery mode for the kernel, and drop down to a root shell, and then try the fsck and/or the 'sudo dpkg --configure -a'... 

Let me know how it goes..

---

### Post by Kafubie on 2010-07-31
> **adalal said:**
> Looks like it was updating tzdata when the plug was pulled maybe? i know you said you don't dualboot, if it is going all the way to trying to load the tzdata, I'm assuming that the kernel is working.

When you turn on the computer, it goes through the Power-on-self-test (POST), and then goes to GRUB. If all you have is Ubuntu on the system, there is a period after the POST, where it says something on the lines of 'Hit ESC to go to grub' for a short while. Hit ESC and go into the recovery mode for the kernel, and drop down to a root shell, and then try the fsck and/or the 'sudo dpkg --configure -a'... 

Let me know how it goes..

Don't worry man..  I let the update through terminal 1 download and install again.  Everything is back to normal

[Solved] im going to rename the thread.

---

### Post by 2uk_ on 2010-07-31
I pulled out the power cable before my laptop had finished shutting down once and completely ruined the HDD.
It was under warenty though so I sent it off to Sony to be repaired.

Anyways I think you need to tell your sister to grow up :|

---

### Post by MCVenom on 2010-07-31
> **2uk_ said:**
> Anyways I think you need to tell your sister to grow up :|

I think you should use harsher words than that :evil:

---

### Post by Bachstelze on 2010-07-31
Made me LOL.  Go, sis, you rock.

---

### Post by Sonybuntu on 2010-07-31
When I'm updating/reinstalling/fixing, my mom complains that I never let her use it, but she is smart enough to not pull the cord. That's a dumb@** sister you got there, pulling the cord when its writing to the drive.

---

### Post by Kafubie on 2010-07-31
As soon as she pulled the cord, I kind of died a little bit inside.

I wished she pulled it out when the writing was complete.
She's 17 btw.

I was about to slap a b****.

---

### Post by randumnumber on 2010-07-31
At least now you can tell her, she is the one breaking the computer, and you are the one fixing it. If all else fails you can use a liveCD to recover the system.

---

### Post by Kirkland14 on 2010-07-31
Total bummer about the sis, bro

---

### Post by Sonybuntu on 2010-08-13
Wait, thats the family computer. . .

That means she can get in a sh**load of trouble if the drive fails!!!

EDIT: Its solved, but i've found that the life of the drive is shortened A LOT.

---

### Post by endotherm on 2010-08-13
> **Sonybuntu said:**
> Wait, thats the family computer. . .

That means she can get in a sh**load of trouble if the drive fails!!!

EDIT: Its solved, but i've found that the life of the drive is shortened A LOT.
really? what leads you to believe that? does it show so in the SMART data you can access from System -> Administration -> Disk Utility? SMART data is designed to estimate the performance and health/fitness of the physical drive.

generally when power is pulled, the filesystem potentially gets corrupted, but it doesn't affect the hardware too much, unless your hdd is doing exactly the wrong thing at the time the power goes. in 14 years, I have only ever had 1 drive be physically damaged by a power failure. It is possible but rare.

---

### Post by Sonybuntu on 2010-08-13
> **endotherm said:**
> really? what leads you to believe that? does it show so in the SMART data you can access from System -> Administration -> Disk Utility? SMART data is designed to estimate the performance and health/fitness of the physical drive.

generally when power is pulled, the filesystem potentially gets corrupted, but it doesn't affect the hardware too much, unless your hdd is doing exactly the wrong thing at the time the power goes. in 14 years, I have only ever had 1 drive be physically damaged by a power failure. It is possible but rare.

Hmmm. maybe it was just the 8GB IDE shitty excuse HDD I was using. I unpluged the cord (I was 8, and I used 6.06!!!) and it died 4 days later. . .

EDIT: Do IDE(PATA) HDDs have SMART?

---

### Post by earthpigg on 2010-08-13
frustrating.

if you've put more than an hour of work into attempting to recover this install, and expect it to take more than an additional hour to fix... time to cut your time losses and do a fresh install.

boot from LiveCD, back up the /home folder to an external hard drive or similar. (optional: exclude your sister's home folder :P )

Reinstall, restore the backed up /home folders.

---

### Post by Dustin2128 on 2010-08-13
17? I thought this was supposed to be the technologically literate generation...

---

### Post by linux18 on 2010-08-13
> **Dustin2128 said:**
> 17? I thought this was supposed to be the technologically literate generation...
not anymore, 15 years ago, 17 year old girls could use ms-dos, now they can only use facebook. Windows is corrupting the tech literacy of the worlds youth! anyway, the hard disk's life isn't reduced by hard shutdowns anymore (in the event of unexpected power failure, spring action pulls the R/W heads to a no write zone of the disk before the platters spin down to a level in which the 'cushon of air' between the platters and heads destabilize)

---

