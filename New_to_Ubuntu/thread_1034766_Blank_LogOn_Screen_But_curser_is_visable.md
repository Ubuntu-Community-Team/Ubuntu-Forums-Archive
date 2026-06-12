---
title: "Blank LogOn Screen: But curser is visable"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by scootatheschool1990 on 2009-01-09
I have Ubuntu 8.10 and I restarted it. After it booted it up (the part with the black background and text running up) the courser came on the screen. I can move it around, but it shows the busy signal(circle rotating). the screen is blank! is there something to fix my log on screen? if the answer is no, then can i log onto the GUI from a sudo or some other command?

---

### Post by minsf on 2009-01-09
is it possible that you installed the new update to the nvidia graphic card driver before you restarted? 
we may need to look into your /etc/X11/xorg.conf later. 
first, let's make it clear, after reboot you get a blank black screen with a cursor, or do you get the command line prompt?
if it is just a black screen, does alt+ctrl+f1 gets you a command line prompt?
do you see the ubuntu splash screen before that?
do you see the gnome welcome screen before it goes blank?
[COLOR="Red"]one tip:[/COLOR] from the command line prompt, to get the GUI, restart gnome by
```
 sudo /etc/init.d/gdm restart 
```

---

### Post by scootatheschool1990 on 2009-02-11
is it possible that you installed the new update to the nvidia graphic card driver before you restarted? 
we may need to look into your /etc/X11/xorg.conf later. 
first, let's make it clear, after reboot you get a blank black screen with a cursor, or do you get the command line prompt?
if it is just a black screen, does alt+ctrl+f1 gets you a command line prompt?
do you see the ubuntu splash screen before that?
do you see the gnome welcome screen before it goes blank?
one tip: from the command line prompt, to get the GUI, restart gnome by


wow! i thought i replied a long time ago. i guess it didn't work. :( anyway

alt ctrl f1 does get me to cmmnd line promp
there is no splash scree at all
no gnome welcome screen at all
it just shows text going up the screen ( booting i believe)
and then my curser appears... nothing else! :(

---

### Post by minsf on 2009-02-12
been awhile...
LOL
so really no ubuntu splash screen with orange bar that fills itself... hmmm...
i am not sure if i can help in this situation, but it may be interesting to people to know what video card and what driver you are using. from the command line, enter the following command and please post here its output:
```
sudo lshw -C display
```
it may also be interesting to know your X configuration. please post here the file /etc/X11/xorg.conf
cheers :)

---

### Post by scootatheschool1990 on 2009-02-28
ok. i'll go check that information out! thanks

---

### Post by scootatheschool1990 on 2009-02-28
hey ok heres the info

VGA Comp
rc410 (radeon x press 200)
phy id -5
version : 00
width 32
clock 66mhz

xorg.conf i couldn't open for some reason... idk whats wrong with that. ha

---

### Post by minsf on 2009-02-28
> **scootatheschool1990 said:**
> hey ok heres the info
VGA Comp
rc410 (radeon x press 200)
phy id -5
version : 00
width 32
clock 66mhz

hey, could you actually cut and paste the output. it seems like you did not post the complete output of "sudo lshw -C display".
as for the configuration file, try to use
```
sudo less /etc/X11/xorg.conf
```
then scroll with the arrow keys (you can quit with the "q" key)
cut and paste it here wrapped in code tags (so it wont take too much space)

---

### Post by soldbyorion on 2009-04-24
I am having the same problem:
I have a mini 9 with ubuntu 8.04
I just purchased it and was running an update when it froze/powered down.
When I restarted it, it goes through normal start up to the splash screen and the bar fills 3/4's of the way and then the screen goes to a blank orange screen with only the pointer (which I can move).
The only thing I can get it to do is CTRL+ALT+BKSPACE, which takes me to a sign on screen.
From the sign on screen there are "options" in the lower left hand corner.
I have tried restarting it from there and the same thing happens, blank screen.
I am a Linux newbie and had only had it up for 20 mins. so please be simple with your instructions. Thanks in advance.

I just downloaded 9.04 to a flashdrive, should I just install that and not worry about my previous issue?
If so how do I do it?

---

