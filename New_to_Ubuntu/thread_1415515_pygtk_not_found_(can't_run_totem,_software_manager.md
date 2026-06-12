---
title: "pygtk not found (can't run totem, software manager, etc)"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-02-24
I cant run the ubuntu software manager, totem or rhythmbox. Below is an example of the error that I get. Any idea what I need to do? Thanks


```

bryan@bryan-desktop:~$ sudo software-center 
[sudo] password for bryan: 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

```

---

### Post by n0dix on 2010-02-24
```
sudo apt-get install pygtk
```

---

### Post by bnhrobotics on 2010-02-24
That was the first thing I tried. 

E: Couldn't find package pygtk

---

### Post by n0dix on 2010-02-24
sounds like you don't have python set well. 
Try in a console
```
 python 
```
```
 import pygtk 
```
Post if you get an error.

---

### Post by sandyd on 2010-02-24
sudo apt-get install python-gtk2

---

### Post by bnhrobotics on 2010-02-24
Not sure what caused the problem. Things suddenly stopped working out of the blue recently. Also had an issue with the automatic updates freezing up and installing "flash-installer" or something for 12 hours. Seemed like it knocked my system out of whack pretty good.

Anyway, my fix was:

sudo apt-get remove python-gtk2

That removed ubuntu-desktop.. as well as about 65 other things. I reinstalled ubuntu-desktop and luckily those other things were reinstalled too. The programs that were not working before are working now. Lets just hope I didn't mess anything else up.

edit: Oh yeah, then I reinstalled python-gtk2. No idea what was wrong with it. I tried updating it first, but it said it was the most up to date version.

---

### Post by tintsu on 2010-10-07
I tried all the previous, and now the situation is really bad. Removing python-gtk2 did remove the desktop, but I cannot fix it. Now I cannot even shut down the computer. So decided to upgrade the whole Karmic Koala to a newer distribution, but it is not possible without the update manager. This basic problem with python stuff prevented starting pitivi, and installing some src code... 

PLEASE help with some easy solution to get out of here ASAP?

There are some instruction for upgrading Ubuntu release from command line by modifying souces list, but also warnings not to do so, and after deleting the desktop, I`m a bit scared to try.

x@x:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: system-config-printer-gnome but it is not going to be installed
                  Recommends: bluez-cups but it is not going to be installed
                  ...
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
E: Broken packages

---

### Post by tintsu on 2010-10-10
The desktop came back with this:

```
sudo aptitude install ubuntu-desktop
```:)

(And decided to install OS again from cd/usb.)

---

