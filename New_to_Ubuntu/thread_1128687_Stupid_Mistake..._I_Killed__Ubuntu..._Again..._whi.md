---
title: "Stupid Mistake... I Killed  Ubuntu... Again... while Upgrading"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-04-17
I was trying to upgrade my Ubuntu 8.10 to 9.04 Beta using Update Manager. It worked... kind of.
After the downloading phase, it started actually installing the packages. It estimated that it would finish installing in about 40 minutes. Just intime, I had to leave for a short appointment and knew that I would be back in about 50 minutes. So, I decided to multi-task and allow Ubuntu to upgrade itself while I was away. Big mistake.
When I came back I say that the screen of my laptop contained only my wallpaper. Nothing more. No flashing green lights below the screen. no hum of the disk or CD drive. no activity when a button was pressed. No signs of any activity whatsoever. Nothing worked to make it keep working.
Desperate, I pulled the plug, un-attatched the battery, and re-attatched it again. Another big mistake.
When my laptop reloaded again, I expected the options to be for Ubuntu 9.04 Beta (and its recovery mode), Ubuntu 8.10 (and its recovery mode), Ubuntu memtest, and Windows Vista (and its recovery mode). Instead, I found that the Vista (and its recovery mode) was spared , but the 5 options for Ubuntu were all for 9.04 (and its recovery mode). I tried all both non-recovery mode Ubuntu 9.04 options and found that the first really was for 9.04 (but would freeze just after the login page) and that the other supposed 9.04 was acutally 8.10 but also froze after the login page.
Man, I really screwed-up here. 
I hope I don't have to delete all the data in the Ubuntu partition, install 9.04, and start all over with my personal data, specialized settings, and extra programs lost.
Is there another way of repairing/undoing the damage I did? Please help!
I'm desperate! _&#915;L*

Take care,
RedStarYellowSun

---

### Post by Walter Melon on 2009-04-17
On the man pages of apt-get, it says the "-f" attachment fixes broken dependencies, but i don't know the syntax of how its used.  There's also ```
apt-get check
``` but i don't think that's going to be of much help because it only checks for broken dependencies.

---

### Post by iponeverything on 2009-04-17
No big mistake on your part.  The mistake is not getting things mucked every now and again, and thus never getting the opportunity too see where it takes you.

I would boot into single user, remount / read/write and start working with apt from that point:

remount / like so:

```
mount -o rw /

```then do:
```
apt-get upgrade
```
and post the output..

---

### Post by sandyd on 2009-04-17
> **Walter Melon said:**
> On the man pages of apt-get, it says the "-f" attachment fixes broken dependencies, but i don't know the syntax of how its used.  There's also ```
apt-get check
``` but i don't think that's going to be of much help because it only checks for broken dependencies.
```

apt-get -f install

```
should fix dependencies

my upgrade didn't have any problems.....
i left the computer running....upgrading... while i went out to supper.

all fine when i came back.

and this is another reason why you don't use Beta software.... the only reason why its beta is that it has bugs :)

---

### Post by RedStarYellowSun on 2009-04-18
Thanks for the advice!

Ubuntu works again!

Take care,
RedStarYellowSun

---

