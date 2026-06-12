---
title: "Upgrade to 10.04 problems...not booting"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by OllieGab on 2010-05-20
Help!
So in the end I decided to upgrade from 9.10 to 10.4.
All went fine and apart from a couple of error messages at start-up (at the Ubuntu logo) the new install started up fine.
At one point I decided to log off and noticed that there was an option to log on i KDE mode. As I didn't think KDE was available by default I tried it. The machine froze up and when I tried to re-boot it stopped at the logo.
After a couple of attempts it tried to log me on in KDE mode, the 'fusion compiz' logo came up and after that it just stops, with a blank screen.

Any way I can get back to Gnome...or at least get back to a functional PC, Gnome or KDE?

Ollie

---

### Post by Peter09 on 2010-05-20
Hold the shift key during boot, this should get you to the grub menu. Select recovery mode and at the menu try - repair broken packages- and perhaps reconfigure graphics.

---

### Post by daimaru on 2010-05-20
you need to get to the login screen. not sure if you have automatic login activated, if not you should be able to select session -> gnome instead of kde or whatever else you have installed. If you do not have a login screen hit ctrl+alt+F2 to get to the terminal login with your username and password and then restart the graphical desktop manager manually.

```
sudo /etc/init.d/gdm restart
```

---

### Post by OllieGab on 2010-05-20
I tried that but that just brings me into the KDE log on screen. However,there's no option there, the image starts to "build" but gets "interrupted" by the fusion compiz logo, and after that the screen just goes black. The cursor is still there though, and it responds to mouse movements.
So perhaps I'm sort on logged on, it's just that I can't see anything!!??

---

### Post by Peter09 on 2010-05-20
Edit:  nope - getting tired - wrong thread- ignore me.

---

### Post by daimaru on 2010-05-20
> **OllieGab said:**
> I tried that but that just brings me into the KDE log on screen. However,there's no option there, the image starts to "build" but gets "interrupted" by the fusion compiz logo, and after that the screen just goes black. The cursor is still there though, and it responds to mouse movements.
So perhaps I'm sort on logged on, it's just that I can't see anything!!??
does the login screen at least show first? so only after you enter your password does the screen freeze?
if so you should be able to hit F10 at login screen which should bring up the select sessions menu. At least once upon a time the F10 key did that . hope it still does. just try it :)

---

### Post by OllieGab on 2010-05-21
> **daimaru said:**
> does the login screen at least show first? so only after you enter your password does the screen freeze?
if so you should be able to hit F10 at login screen which should bring up the select sessions menu. At least once upon a time the F10 key did that . hope it still does. just try it :)

No, it never gets to a point when I can actually do something. A blue KDE style screen comes up (I can only guess that it will evetually turn into the log in screen!), it turns into a Fusion Compiz logo for a couple of seconds and then the Ubuntu logo comes back (the one with the red small dots underneath). And there it stops. The cursor still "active" but nothing I can do!

---

### Post by OllieGab on 2010-05-21
If I boot up with a live CD I have access to all my files. Is there anywhere I can go to edit so that my computer automatically boots up in Gnome (as it used to)?
There must be a config file somewhere which was altered when I tried to log on in KDE (and which it, as far as I can understand, tries to do automatically now whenever I boot) and which I can edit to get it back to its original, or...?

---

### Post by Sef on 2010-05-21
Read Ubuntu Documentation: [GRUB2]("https://wiki.ubuntu.com/Grub2")

---

### Post by Peter09 on 2010-05-21
You need to get to a terminal on your system and try the command
 
```
$ sudo dpkg-reconfigure gdm

```
 
Are you able to get to a terminal throuigh recovery mode. What version of Ubuntu are you running?
 
I think you are running LUCID. What happens when you hold the shift key (start as soon as you see the Bios text come up)
 
If it was an unsuccesful upgrade then try hitting the escape key multiple times while your system boots.

---

### Post by OllieGab on 2010-05-21
It was "probably" a successful upgrade! As mentioned in my initial post, there were some error messages but nothing that prevented me from running my machine.
The cause seems to be that I logged off Gnome and logged back on in KDE (I wish I would stop experimenting!!), so now the machine wants to boot up in KDE and it doesn't seem to like that.

I need to "force" the machine to go back and log on with Gnome.

---

### Post by Peter09 on 2010-05-21
Yes but to do this you need to stop it going to the boot screen and get to recovery mode. It should do that before it ever gets to trying to run KDE or Gnome. If you cannot get to recovery mode then it suggests a deeper problem with Grub.

---

### Post by OllieGab on 2010-05-21
I have no problem getting to recovery mode but whatever I do there sooner or later results in a black screen (with a functioning cursor).
I beginning to think that I'm actually logged on (in KDE) and that it is the 'compiz' thingy that causes problems. Can remember when I upgraded to 9.04 (from 8.10) that I had disable all compiz functions (ie the no, medium and extra....) for the machine to work properly.
So is there any way I can disable compiz, ie without being able to see the screen?

---

### Post by cgroza on 2010-05-21
Maybe the problem is compiz... there is any way to disable it from the command line?

---

### Post by Peter09 on 2010-05-21
Have you issued this command in the recovery mode.
 
```
$ sudo dpkg-reconfigure gdm
```
 
other commands to try are
 
```
sudo apt-get update
```
followed by
```
sudo apt-get upgrade
```
 
once you have done this you could try
 
```
startx
```

---

### Post by OllieGab on 2010-05-22
I still haven't had a luck despite trying out several of the recommendations above...
Any way I can remove kde altogether from the command line...I never really wanted it in the first place and I'm prettys sure it is either KDE - or possibly fusion compiz - which causes me the problem. So any suggestions on how to remove the above (from the command line!!) are welcome!

Cheers

---

### Post by OllieGab on 2010-05-22
Additional question!
Is KDE installed by default when upgrading Ubuntu 9.10 to 10.4?
Could it just be that I tried to log on with a KDE session and because it's not really there (though some default screens may be part of the package!?) it tries to log on and then it stops because it just doesn't know what to do?
If that is the case there must be some way I can force it to log on with Gnome, via the command line. (I can get to a command line if I Ctrl+Alt+F2 during boot up!)

---

