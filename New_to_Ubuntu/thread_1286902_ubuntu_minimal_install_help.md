---
title: "ubuntu minimal install help"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Fatalrewind on 2009-10-09
Hello

I want to have a bare minimum install of ubuntu and i have
been looking at a minimal ubuntu install iso but i dont know
how to use the command line as i am new to ubuntu and i worrie
that the minimal install wouldnt have the drivers i need to get
the system running like the wireless,sound and display drivers.

I have a dell mini 9 and i am happy with 8.04 and 9.04 driver
setup from a fresh install ,so i was wondering how i would go
about doing a minimal install ,would it be difficult as i am
new to linux in general or would the minimal ubuntu install iso
be the same as the graphical full install iso minus the extra
software.

If the minimal install would be too dificult for me to use
then could someone recommend an alternitive ubuntu distro
that is 1gb or less to install ,i am open to trying other
distros but i prefer ubuntu so a small ubuntu would be perfect.

Kind regards

thanks

Paddy

---

### Post by LowSky on 2009-10-09
if you own a mini 9 then why not use the netbook remix edition?

---

### Post by jeremyswalker on 2009-10-09
The minimal Ubuntu iso will get you either the exact same GUI system, or a command line only system. You do get to choose your desktop environment though, if I remember correctly.

---

### Post by wojox on 2009-10-09
Here's how I did it for Gnome, download the mini.iso from here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Boot and install 

Once finished log back into the system and issue these commands to get a minimal desktop enviorment:

```
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils

```

After that you can open Synaptic Package Manager and install whatever you want.

---

### Post by sisco311 on 2009-10-09
[http://psychocats.net/ubuntu/minimal]("http://psychocats.net/ubuntu/minimal")

---

### Post by Fatalrewind on 2009-10-09
Hello

A big thankyou for all the help and advice ,that sounds
like a plan Wojox.

cheers guys

Paddy

---

### Post by Fatalrewind on 2009-10-09
Hello

well i followed the instructions given by Wojox
and now have a complete desktop in use but theres
a problem.

I began the command line instalation and followed
all steps but near the end of the initial steps
i was offered to install aditonal software from a list
and in that list there was ubuntu desktp ,kubuntu desktop
and other software ,i choosen ubuntu desktop as i thought
this might mean that i dont have to install the desktop
from the command line.

So after the instalation was complete i rebooted and
found myself at the command line ,i checked the used
space on the drive with another ubuntu install and the
size was 1.2gb well not bad as ubuntu usualy installs
at around 2.2gb or more.

I then decided to complete the steps that Mojox had given
and installed the default ubuntu gnome desktop enviroment
and now i am up and running but the size/space used on disc
is now 2.2gb and when i followed that last step to install
gnome desktop it had taken a very long time ,almost like
installing ubuntu from scratch.

So all in all i am using 2.2gb of space but i have
none of the extra software installed that would normaly
come with the default ubuntu install and i am wondering
what the hell the point was ?

Paddy

---

### Post by ankspo71 on 2009-10-09
Hi
> i was offered to install aditonal software from a list
and in that list there was ubuntu desktp ,kubuntu desktop
and other software ,i choosen ubuntu desktop as i thought
this might mean that i dont have to install the desktop
from the command line.

I know you already built your OS with Ubuntu Mini Remix, but I just wanted to note that the mini cd found here doesn't have those options.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
I have never tried "Ubuntu Mini Remix" myself.

Ubuntu's "base" or full desktop installs are always going to be large in size no mater what desktop. I was wondering the same thing.... why is it so large? There is still an advantage though, your gnome desktop should be much more responsive now, because it doesn't have the extra packages and unnecessary running services that you might not ever need. Performance is a plus with the base/core installs. The last time I tried gnome-core, it was twice as fast as ubuntu-desktop. Plus now you get to choose any applications you want. 
James.

---

### Post by ikisham on 2009-10-09
Fatalrewind, you shouldn't install anything else at the end of the install process (you installing ubuntu-desktop is what probably borked all your effort). After the normal installation of the minimal Ubuntu you should reboot to the command-line and type the line wotox entered so you'ld have a basic Ubuntu-Gnome.
That would be lighter, smaller and faster than the whole Ubuntu and on top of it you could install the apps you need *always taking care that they don't bring too much unwanted stuff with them*.
Perhaps you could give it another try.

If you want something even lighter but yet functional you could instead only install:
```
sudo apt-get install xorg gdm xfce4 xfce4-goodies
```
[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

Then you could examine the packages in Synaptic carefully so you install software you need that at the same time don't bring too much uneeded dependencies or are lightweight by themselves.

A [list]("http://packages.ubuntu.com/jaunty/") of Jaunty's packages.

---

### Post by Fatalrewind on 2009-10-09
Ok i will give it another go tommorow and i will leave
out any extra software to install ,with the minimal install
what size should it be just after install at the command
line ? as i was sitting at 1.2gb at this stage but i am thinking
mabe it should have been around 700mb/800mb but i could be wrong
and was it a bad idea to install the complete gnome desktop
like advised by Wojox as it took forever and pushed it from
1.2gb to 2.2gb.

I really need a minimal install as i am running from a 
8gb usb pen drive and the smaller the install the faster
the system will react ,as i have tried linux mint and it
was much faster as the install was small and i also
noticed this with moblin.

I am not using notebook remix as i have tried and find it
quite buggy ,the minimal ubuntu i used was 9.04 desktop.

If anyone has any other ideas for having an extremly
small install ubuntu or otherwise please let me know
i was thinking of even 500/600mb install with a desktop
enviroment ,i do really like ubuntu tho and would love
to stick with it dsl was an option but i have read
theres not much driver support out of the box for the
dell mini.


thanks for all the help its really appreciated 

Paddy

---

### Post by ikisham on 2009-10-09
If you're caring more for the space than anything else then you could even try the psychocats link sisco311 posted above. But I think even that could be not so small, specially when you start to install this and that that you need.
To give you an idea, [crunchbang-lite]("http://crunchbanglinux.org/wiki/applications#lite_edition") is based on Ubuntu Jaunty but has only some basic software and would take more than 1.5 GB installed, I think.
Now I'm using antiX and my installation is 1.7 GB big. I think that a small system like antiX-base would take about 1.2 GB.
So if you're well with IceWM or other 'less appealing' window managers you could go that way. But from my experience, unless you know well what you install, in Ubuntu it's just so easy to start to get a bloated system even when coming from a minimal because of how one thing depends on a lot of others.
So probably you could try antiX base if you want to start with a small system (it uses Debian testing repos) up to the minimal Ubuntu with Xfce like I posted above if it's ok to take some more space.
But there are, of course, other systems. The following is a search for distributions for old computers (which would take less space) at Distrowatch:
[http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by louieb on 2009-10-09
Try one of these: Lots of forum members play with building a lighter weight Ubuntu desktop. 
["Ubuntu-Desktop-Minimal"  ck post #121 too]("http://www.uluga.ubuntuforums.org/showthread.php?t=1155961") 
[How to: Create a complete, snappy and beautiful Ubuntu Desktop - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1209904&highlight=minimum+install")

---

### Post by ikisham on 2009-10-11
I'll add [this]("http://ubuntuforums.org/showthread.php?t=1248322") one. It seems to be nice and claim 900 MB when installed.

---

### Post by darksideforge on 2009-10-12
Paddy,
I know you started off by specifically stating that you wanted an minimal [COLOR="DarkOrange"]Ubuntu[/COLOR] distribution, but for some of the minimalist ideas you're requesting, have you considered having a look at [[COLOR="Blue"]LXDE[/COLOR]]("http://lxde.org/lxde")?

It isn't exactly Ubuntu, but it's a free linux distribution and the LiveCD checks out around 451MB...it gives you tons of functionality with a very small footprint (memory/resource usage).

It's just a thought.
~dsf

---

