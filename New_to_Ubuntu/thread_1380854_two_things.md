---
title: "two things"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by dzon65 on 2010-01-14
1)Got this old compaq with this vanta card.Would've searched for a driver but it's had it's best time.Gonna put another card in it.What would be a good a good choice,something around 50 euros?Don't do anything fancy with this pc,just some surfing,some youtube.....
2)Someone gave me this custombuild pc,on old thing but pretty solid.Only 128mb ram and an S3 virge card.Couldn't get it to boot so I swapped the HD's and installed a minimal ubuntu on it.But,when I put it back in,there was a black screen with a command line:john$....
I'll be getting some more of these old pc's (most likely this HD swapping will have to be done again)so,being a newbie,what command should I use in order to get it started?

---

### Post by ibizatunes on 2010-01-14
128 meg of ram wont run, any version of ubuntu, your better off getting some more ram or installing Puppy linux

---

### Post by dzon65 on 2010-01-14
I got 128mb running minimal flawlessly on a machine.Minimal install,xfce4,xorg,thunar.....Sure,puppy would do the job even better but this runs as well.Instead of xfce,openbox or flux could make it faster though.

---

### Post by audiomick on 2010-01-14
> **dzon65 said:**
> 1)Got this old compaq with this vanta card

vanta = video card? I think nVidia is a good choice at the moment.

> ...and installed a minimal ubuntu on it.But,when I put it back in,there was a black screen with a command line:john$....

As far as I know, there is no GUI (graphical desktop) on a minimal install by default. In any case, what you are seeing is a command line promt, not unlike running DOS in the old days. ;) The system is up and running. Try typing
```
ls
```
and enter, for instance. It should show you a list of the contents of the directory you are in.


So, either there is no GUI installed, or it is not starting. The command you need to install a desktop (or anything) is
```
apt-get install <name of application>
```

by the way:
To safely shut down the computer from there,
```
shutdown -P now
```
should turn it off, and
```
shutdown -r now
```
should make it reboot.

---

### Post by cascade9 on 2010-01-14
If you only have 128MB of RAM, bt your getting other, old computers, try swapping soem RAMfrom 1 machine to another. 256MB or even better 384MB is a lot nicer than 128MB. 

I think old S3 cards have limited support under linux. Never tried one myself, I ditch my last S3 in the 1990s (its still in a box as a test card, but I havent used it since then) 

> **audiomick said:**
> vanta = video card? I think nVidia is a good choice at the moment.

Vanta IS nVidia. Its the 1st series cards nVidia released. 

There are actually drivers for them still around (currently 71.86.11) 

BTW, be carefull with things that have vantas. A lot of vantas appeared in motherboards with AGP x1/x2 slots, and quite often newer cards wont work in older slots..and sometimes the old slots can kill new cards 

AGP 1x and 2x- 3.3 volt
AGP 4x 1.5volt
AGP 8x- 0.8volt

---

### Post by dzon65 on 2010-01-14
> **audiomick said:**
> vanta = video card? I think nVidia is a good choice at the moment.


As far as I know, there is no GUI (graphical desktop) on a minimal install by default. In any case, what you are seeing is a command line promt, not unlike running DOS in the old days. ;) The system is up and running. Try typing
```
ls
```and enter, for instance. It should show you a list of the contents of the directory you are in.


So, either there is no GUI installed, or it is not starting. The command you need to install a desktop (or anything) is
```
apt-get install <name of application>
```by the way:
To safely shut down the computer from there,
```
shutdown -P now
```should turn it off, and
```
shutdown -r now
```should make it reboot.

The gui is installed,I'm working with the machine right now.But when I put this HD into another machine the problem occurs.Maybe I don't get it, but,the system is fully installed,works fine on this one.Should work on the other one,no?

---

### Post by halitech on 2010-01-14
do both systems have the same video card? could be a driver is installed for 1 card but the other machine is using a different card and doesn't know to load the other driver

---

### Post by dzon65 on 2010-01-14
Yep,this one's the vanta,the other one's an S3.

---

### Post by halitech on 2010-01-14
ok, so different video cards. try booting into Single USer Mode from Grub and run xfix and see if that makes any difference.

press ESC when you see loading Grub to get into the grub menu to find single suer mode

---

### Post by dzon65 on 2010-01-14
Just a sec,only one monitor....right back.

---

### Post by dzon65 on 2010-01-14
Nope,no grub.Goes directly to this: (trying t o type this):root@john:~#
The "@" looks more like the debian logo and the "~" is a bit higher.

---

### Post by halitech on 2010-01-14
ok, so you are logged in as root (Single User Mode) as indicated by the #

try running xfix and see what it does

---

### Post by dzon65 on 2010-01-14
"command not found"

---

### Post by dzon65 on 2010-01-14
tried again,now it's giving suggestions.Did you mean xfig,xmix,gfix,efix

---

### Post by halitech on 2010-01-14
try this
```
sudo dpkg-reconfigure xserver-xorg
```

it *shouldn't* work in 9.04 or 9.10 but something seems weird. if it does work, then try running
```
startx
```

---

### Post by dzon65 on 2010-01-14
Nope,nothing.

---

### Post by theozzlives on 2010-01-14
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by dzon65 on 2010-01-14
Wait,something just popped up:fatal server error,please consult x;org foundation support.........

---

### Post by dzon65 on 2010-01-14
> **theozzlives said:**
> [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I know.One thing I'd like to mention though.When i got this pc,xp pro was on it.Slow as a snail but working.This is a really minimal install,exept for xfce perhaps but was planning to use openbox afterwards.
Besides,the hd works fine on the other machine.

---

### Post by dzon65 on 2010-01-14
I could try to reboot from the cd but since it simply wouldn't boot from cd,no specs for the bios (to upgrade it) the only option was to boot it from the other machine.

---

### Post by dzon65 on 2010-01-14
Hey guys.I'll give it another try with the cd and if it doesn't work......I'll consider this thread solved.People on the forum needing more urgent help.Thanks for all the help.
Kind regards.

---

### Post by halitech on 2010-01-14
I'm still thinking it is something to do with the video card. Maybe try removing xorg and reinstall it and see if that works.
```
sudo apt-get remove xserver-xorg xserver-xorg-core && apt-get install xserver-xorg xserver-xorg-core
```

you will need a network connection for this I believe although it might pull the files from the cd.

---

### Post by dzon65 on 2010-01-14
Nope,the package list or status file could not be parsed or opened.Really,I think this isn't worth putting more effort in.
Thanks all !

---

