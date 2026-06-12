---
title: "Freezes on battery"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Kedster on 2010-11-27
Alright, I have been having problems ever since I upgraded (fresh install) to maverick 10.10

if I am running on battery it will run sometimes for a long time others for mere minutes, but it ends up freezing, completly nothing can move if theres music its loops(the 2 second loop at least) NOTHING CAN BE DONE other then crash it. 

I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/662998") thats similar but its about amd64 architecture and ati graphics and i dont think i have either.

     they said it can be fixed by using an old kernal, but wouldnt that make alot of other problems

and why doesnt cronical or linux/gnu fix that part of there kernal?

---

### Post by Kedster on 2010-11-28
Bump

---

### Post by Kedster on 2010-11-28
does anyone have any ideas

---

### Post by Kedster on 2010-11-29
Bump

---

### Post by BanksKy on 2010-11-30
I have a similar issue, but its only when I plug the laptop in, the computer completely freezes up.

I've been looking for a solution for some time, but nothing yet 

:(

---

### Post by Kedster on 2010-11-30
hmm i hope that someone will be able to help

---

### Post by djsutton on 2010-11-30
Does ctrl + alt + F1 open a tty login, or does crtl + alt + del do anything?

---

### Post by Kedster on 2010-11-30
I just tested it, neither key combo does anything.

one thing that i should mention i have had to do the fisrt fix on [this]("http://ubuntuforums.org/showthread.php?t=1471281") thread

> MSI Wind u100 gnome power manager Issue 

Description: Hibernates when unplugged from AC

When started up with no AC, there is no issue, but when plugged in to AC and then unplugged from AC, the netbook mistakenly thinks the battery life/charge is less than 2%, and thus hibernates.

Bug Location: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/558627](https://bugs.launchpad.net/ubuntu/+s...er/+bug/558627)

Work Around: Press Alt-F2 and use the pop-up to launch gconf-editor.
Navigate to Apps / gnome-power-manager / general.
De-select the option use_time_for_policy.

No need to restart, just close the config editor

i dont know if that is any help

---

### Post by BanksKy on 2010-11-30
Not sure if this is of any help to you, but I resolved my problem.

The ATI graphics card im using had a feature enabled that goes into "Power Play" mode when the plug is connected, basically it just boosts performance when you have power. 

Disabling this solved my issue. I know this isnt exactly your problem but maybe it will help trigger someone's brain into thinking of a solution.

---

### Post by Kedster on 2010-12-03
I Tryed to change power manager setting, and Unticked "spin down hard disks" and so far is been good

---

### Post by lenin.leishangthem on 2010-12-05
i have the same problem ever since i upgraded to ubuntu 10.10... mine is dell vostro 1014....

---

### Post by arsham on 2011-02-18
Hi all,
I solved my problem by installing the 1.3.0-1ubuntu1 version of pm-utils, now I get no freeze.
Just thought you all might try it out.
Cheers

---

