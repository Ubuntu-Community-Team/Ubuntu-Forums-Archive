---
title: "Problems starting ubuntu 10.10 linux"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by devinsoles on 2011-01-23
Hi, I am having troubles with my version of linux(ubuntu 10.10). I burned the image file onto a dvd-r disk and followed the instructions online to start up ubuntu. The problem is after the ubuntu screen with the dots goes away my screen is nothing but black and white lines. I will sometimes hear the ubuntu start up noises but it will not go past the screen described. I thought it may have been from the way I started up ubuntu so I clicked the second option of installing into windows so I could switch. When the boot screen gives me the options of windows 7 or ubuntu I click ubuntu but the same white lined screen appears. What should I do to fix this problem?

---

### Post by Paqman on 2011-01-23
What hardware are you trying to install it on? Can you boot up into a command line in Recovery Mode? If so what happens when you type:
```
startx
```

---

### Post by Rubi1200 on 2011-01-23
Hi and welcome to the forums devinsoles :)

Could you please confirm whether this is a normal install to the hard-drive or a Wubi (inside Windows) install?

What graphics card do you have installed?

---

### Post by sandyd on 2011-01-23
> **devinsoles said:**
> Hi, I am having troubles with my version of linux(ubuntu 10.10). I burned the image file onto a dvd-r disk and followed the instructions online to start up ubuntu. The problem is after the ubuntu screen with the dots goes away my screen is nothing but black and white lines. I will sometimes hear the ubuntu start up noises but it will not go past the screen described. I thought it may have been from the way I started up ubuntu so I clicked the second option of installing into windows so I could switch. When the boot screen gives me the options of windows 7 or ubuntu I click ubuntu but the same white lined screen appears. What should I do to fix this problem?
nomodeset comes into mind.

---

### Post by devinsoles on 2011-01-23
When the disk is put in it pops up the menu and its name is wubi.exe so its probably wubi. It brings up the ubuntu menu afterwards with the demo and full installation, inside windows installation, and learn more options.

---

### Post by Rubi1200 on 2011-01-23
If you want to install using Wubi, start by reading the Wubi Guide:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

For boot options after the first phase, read this:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by devinsoles on 2011-01-23
The problem did not fix after I put in nomodeset as the walkthrough said. 
[http://s1096.photobucket.com/albums/g331/devinsoles/?action=view&current=002.jpg](http://s1096.photobucket.com/albums/g331/devinsoles/?action=view&current=002.jpg)
That is a picture of what my screen is doing. It will manage to go through the installation but after it says its rebooting when I click ubuntu and the first option (generic) this pops up.

---

### Post by devinsoles on 2011-01-23
graphics card and such is
Generic PnP Monitor @ 1680x945
NVIDIA GeForce GTS 360M

---

### Post by devinsoles on 2011-01-23
It does not recognize startx as a command.

---

### Post by bcbc on 2011-01-23
> **devinsoles said:**
> The problem did not fix after I put in nomodeset as the walkthrough said. 
[http://s1096.photobucket.com/albums/g331/devinsoles/?action=view&current=002.jpg](http://s1096.photobucket.com/albums/g331/devinsoles/?action=view&current=002.jpg)
That is a picture of what my screen is doing. It will manage to go through the installation but after it says its rebooting when I click ubuntu and the first option (generic) this pops up.

You need to add 'nomodeset' every time you boot until you have either made  it a permanent option or added it to grub.
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by devinsoles on 2011-01-23
I only added nomodeset once.

---

### Post by bcbc on 2011-01-23
> **devinsoles said:**
> I only added nomodeset once.
OK try again. That post I linked to shows how to do it ( under the title: **How to temporarily set kernel boot options on an installed OS (not wubi)** you can ignore the (not wubi) bit as it's the same once wubi is installed) - and how to make nomodeset permanent (although I'm sure you can just install the nvidia drivers instead).

Let us know how it goes.

PS: the instructions on how to permanently set boot options are also the same for a Wubi install even though it says "(not wubi)".

---

### Post by devinsoles on 2011-01-23
Everytime that I try to start up ubuntu now it opens up Gnv grub version with the option to input commands

Grub> 
Thats all its doing now, do I need to uninstall and start over?

---

### Post by bcbc on 2011-01-23
> **devinsoles said:**
> Everytime that I try to start up ubuntu now it opens up Gnv grub version with the option to input commands

Grub> 
Thats all its doing now, do I need to uninstall and start over?
```
configfile /boot/grub/grub.cfg
```
If that doesn't work it's probably easier to reinstall (particularly as you have nothing to lose on your install).

---

### Post by devinsoles on 2011-01-23
Ohkay will do, now the screenshot error in the link you provided was typing so does nomodeset go after or before quiet splash?

---

### Post by bcbc on 2011-01-23
> **devinsoles said:**
> Ohkay will do, now the screenshot error in the link you provided was typing so does nomodeset go after or before quiet splash?
It doesn't matter. I always put it after.

---

### Post by devinsoles on 2011-01-23
Ohkay so I put the code you provided in the grub>
but it only removed the top information and gave me another grub>

Whenever I do the install into windows if there is already a file the same it normally uninstalls it and installs again yet now it tells me to remove the file and gives me a location. When I open it in run it is a read only file and now Im just completely confused.

---

### Post by bcbc on 2011-01-23
> **devinsoles said:**
> Ohkay so I put the code you provided in the grub>
but it only removed the top information and gave me another grub>

Whenever I do the install into windows if there is already a file the same it normally uninstalls it and installs again yet now it tells me to remove the file and gives me a location. When I open it in run it is a read only file and now Im just completely confused.
If you could rewrite what you said above in clear language it would help me figure out what is going on.

Are you saying that you tried to reinstall Wubi and you are getting an error? If so, what error. Please be specific about what you did and what the response was.

---

### Post by devinsoles on 2011-01-23
Im sorry I should have been more clear. Yes I got an error 

An error occured:

Cannot install into C:\ubuntu.
There is another file or directory with this name. 
Please remove it before continuing. 
For more information please see the log file;

Then it lists the log file. I open run and type in the log file and its a notepad file put doesn't take me to the file location like Im wanting. Normally it just uninstalls and installs.

---

### Post by bcbc on 2011-01-23
Yes normally it should uninstall and then reinstall. There must be something strange going on. Hard to say what that could be, but I'd follow the manual uninstall instructions listed in the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?") and then try again.

Also, I'd take a cautious approach to this. Please make sure you have adequate backups and recovery disks. While Wubi removes the risk of partitioning, you're still running a new operating system and it's possible to damage Windows if you blindly follow commands/advice that is inappropriate.

---

### Post by devinsoles on 2011-01-24
Well I would like to happily inform you I am replying this from my new ubuntu os! With your kind help I have finally installed it successfully. :D

---

### Post by bcbc on 2011-01-24
> **devinsoles said:**
> Well I would like to happily inform you I am replying this from my new ubuntu os! With your kind help I have finally installed it successfully. :D
Great to hear! Enjoy :)

---

