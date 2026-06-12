---
title: "Synaptic Package Manager Error--among others"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by bgmitch on 2010-03-18
[FONT="Georgia"][/FONT]I have just installed Ubuntu 9.10 on my Sony Vaio VGN-NS135E.  I had Windows Vista installed on my computer and chose to partition the drive when installing Ubuntu.  When I restarted the computer after set up, I received a message that read:
"Your system encountered a serious kernel problem. Your system might become unstable now and might be restarted. You can help the developers to fix the problem by reporting it."

When I click "report problem" nothing happens.

I also have a message in my toolbar i guess that says 
"An unresolvable problem occurred while initializing the package information. Please report this bug against the 'update-manager' package and include the following error message:
'E:Type 'bo' is not known on line 1 in source list/etc/apt/sources.list, E:The list of sources could not be read.'

I've gone to other forums and plugged in several things into the Terminal to no avail. I still get the 'bo' error. I can't download ANYTHING. The synaptics manager doesn't work. I get error messages when i try to install anything. the software manager also doesn't pull anything up when i even try to look up programs.  Please help! This is my first experience with Ubuntu. Thanks.

---

### Post by the yawner on 2010-03-18
Type:
```

head /etc/apt/sources.list

```
And post here the output on the very first line.

---

### Post by bgmitch on 2010-03-18
> **the yawner said:**
> Type:
```

head /etc/apt/sources.list

```And post here the output on the very first line.

bo#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted

---

### Post by mtron on 2010-03-18
open a terminal and type:

```
sudo gedit /etc/apt/sources.list
```

And remove the 2 letters "**bo**" from the first line (After it is done the first line in the file should look like
```
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted 

```
then save the text file, close the text editor and back in the terminal run
```
sudo apt-get update
```

this should get you rollin' again.

---

### Post by bgmitch on 2010-03-18
> **mtron said:**
> open a terminal and type:

```
sudo gedit /etc/apt/sources.list
```

And remove the 2 letters "**bo**" from the first line (After it is done the first line in the file should look like
```
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted 

```
then save the text file, close the text editor and back in the terminal run
```
sudo apt-get update
```

this should get you rollin' again.
It worked!!!!!!! Thank you sooo much! I just KNEW it was gonna be something simple.  Still new to all of this. lol.  Enjoyed the learning process though.

---

### Post by Paqman on 2010-03-18
> **bgmitch said:**
> It worked!!!!!!! Thank you sooo much! I just KNEW it was gonna be something simple.  Still new to all of this. lol.  Enjoyed the learning process though.

This has got you connected to the repos, but it hasn't necessarily fixed your kernel problem (unless you installed a new kernel, of course).

Btw:
```
sudo gedit /etc/apt/sources.list
```

is not good practice. For graphical apps like gedit you should use gksudo:

```
gksudo gedit /etc/apt/sources.list
```

If you're lazy like me "gksu" works just the same as "gksudo" ;)

---

