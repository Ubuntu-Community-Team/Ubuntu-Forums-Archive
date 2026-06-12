---
title: "Ubuntu installation issues."
date: 2009-07-16
forum: New to Ubuntu
---

### Post by helmandollar on 2009-07-16
Im very new to Ubuntu and im having major problems with installation. Im getting things like fatal error no screens and No such file or directory on majority of commands. When trying to do alot of stuff its telling me to enable universe. Any help would be greatly appreciated. Thank you.

---

### Post by Het Irv on 2009-07-16
Do you have any specific issues to start on.  Its kinda hard to diagnose your problems without any specific examples

---

### Post by Bucky Ball on 2009-07-16
If you are actually at a desktop, go to:

System->Administration->Software Sources

... and make sure you have the correct repositories ticked (the universe repository in particular).

But yea, deep breath and tell us exactly where you are at with it and what you have done so far.

Details about the machine (and screen) and the version of Ubuntu you have installed or are attempting to (Desktop or Alternate) would help your chances of help immensely. :)

---

### Post by helmandollar on 2009-07-16
Well basically i have no desktop, all i see is what looks like a windows cmd screen. When i type in dir all i get the only thing that shows up is desktop. It will let me update some things. Its kind of hard for me to explain everything cause i dont know anything about ubuntu yet other than trying different commands and people helping me.

---

### Post by halitech on 2009-07-16
did you do a server install or a commandline install?

---

### Post by Zero++ on 2009-07-16
Did the live CD run ok?

Are you having problems with the Live CD or an actual installation?

---

### Post by Bucky Ball on 2009-07-16
As Halitech says. What version of Ubuntu did you download? You may have managed to not load the desktop environment. I have done that exact same thing somehow! Fixable.

---

### Post by helmandollar on 2009-07-16
Im having problems with an actual install. At the command line when i type in startx i get Fatal server error: no screens found. I also get undable to connect to x server

---

### Post by helmandollar on 2009-07-16
How do i go about seeing if i have the desktop environment installed.

---

### Post by halitech on 2009-07-16
what cd did you download?

---

### Post by helmandollar on 2009-07-16
Ubuntu 8.04 desktop version

---

### Post by halitech on 2009-07-16
do you know if you have internet access on the machine? If you do, you could try
```
sudo apt-get install ubuntu-desktop
```and have it download and install the gui.

---

### Post by LewRockwell on 2009-07-16
how about getting the latest version and checking it out

then, if you are still having problems you might also let us know your system information

for all we know you could be trying to install on an Atari 400...

keep us posted

(it's a shame that no one before has asked for system information...what were they thinking?)

.

---

### Post by helmandollar on 2009-07-16
> **halitech said:**
> do you know if you have internet access on the machine? If you do, you could try
```
sudo apt-get install ubuntu-desktop
```and have it download and install the gui.
when i type in sudo apt-get install ubuntu-desktop it tells me ubuntu-desktop is already the newest version

---

### Post by Bucky Ball on 2009-07-16
then type in:

```
sudo /etc/init.d/gdm start
```

or 

```
startx
```

---

### Post by halitech on 2009-07-17
ok, time for some info about the machine. What do you have for a processor? how much RAM? what video card?

---

