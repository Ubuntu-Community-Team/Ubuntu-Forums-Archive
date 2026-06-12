---
title: "is this a real and safe to run command ???"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-23
i found this command while searching for possible help for my no audio problem...

it looks very much out of place and i wanted to check it out before running it...

is it safe to run a command this long ???

thanks...


sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pulseaudio gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

---

### Post by bacil on 2009-07-23
Yes it is :-)

---

### Post by Sub101 on 2009-07-23
> **bacil said:**
> Yes it is :-)

Agreed.

---

### Post by masux594 on 2009-07-23
It's only a long list of packages to install.. nothing particular, don't worry..

Sysc, A

---

### Post by ~sHyLoCk~ on 2009-07-23
It just installs gstreamer but not sure if you have an audio problem that will fix it.

---

### Post by mthalis on 2009-07-23
I used, No bad thing happen.

---

### Post by Bucky Ball on 2009-07-23
No bad thing would. It is legit.

---

### Post by NOTAGEEK on 2009-07-23
thanks for all the quick input...

if i learned 1 thing so far it is to check before running something that looks out of the ordinary...

here are my results...

 sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pulseaudio gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
[sudo] password for wxyz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-ffmpeg set to manually installed.
gstreamer0.10-pulseaudio is already the newest version.
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by masux594 on 2009-07-23
Oki, you're just up to date.. Nothing change..

Sysc, A

---

### Post by NOTAGEEK on 2009-07-23
ok---thanks again to all...

thread closed...

---

### Post by Bucky Ball on 2009-07-23
FYI:

Some things to look out for are commands that contain:

```
rm = This means remove
mv = This means move
```There are others and syntax you can use (especially with rm) that renders this command extremely lethal. Just have a look.

Anything with 

```
sudo apt-get 
```is about to install or remove a package, 99% of the time fine. 

```
sudo = su (super user); do (do) = superuser do
```This command makes you root for your next command only. Not a good idea to be root always (in fact v bad).

---

### Post by benj1 on 2009-07-23
sudo - give you root powers, basically you can do anything in the system, including deleting it all, this is why you needed to enter a password 

apt-get install - 'apt-get' is a command line package manager, it has many options, one of which is install, im sure you can guess what that does

ubuntu-restricted-extras gstreamer0.10-ffmpeg .... - packages to install

if you aren't sure about a command 'man command' eg 'man apt-get' will tell you what it does. theres also a sticky about commands you shouldn't run.

the major ones are
'sudo rm -rf' will basically delete everything on you computer.(rm is the delete command) always be sure you know what a command is doing when it uses rm especially with sudo
':(){ :|:& };:'is a fork bomb, probably more annoying than damaging (it forks processes until your computer kills it or crashes), there are many variations on this theme.
although of course there are many others

EDIT the fork bomb should be ': ( ) {  : | : &  } ; :' without spaces

---

### Post by Ratscallion on 2009-07-23
The command just installs some things. You tried to install them, then apt just says "Everything's up to date as it should be" no harm doing things like that, to make sure it's all there, everything you need.

---

### Post by NOTAGEEK on 2009-07-23
i sure appreciate all the help---now if i could just get audio !!!

---

### Post by Soulcage on 2009-07-23
Try right clicking on the sound icon in the tray choose "open volume control" then click on switches tab, then click or unclick the checkbox there. Does that help any?

---

