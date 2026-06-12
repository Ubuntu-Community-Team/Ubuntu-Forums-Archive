---
title: "I Want my Ubuntu Back!"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by upsman on 2011-01-27
If this was the first time I used Ubuntu, I call it Free Crap!  But I've used it for the passed 6 months, and it great!
 I tried to upgrade from 10.04 to 10.10 and I can't get the video to the right size 1280X1024. I can't get any higher than 640X480 with the Nvidia drivers installed. Without them the highest is 1024X786?? I even reinstalled the 10.04 same problem? I'm trying to load it on a Dell Inspiron 8200. The display went bad so I connected a Dell 17" LCD I had.  It has a Nvidia GeForce4 go card. 

When I booted this morning Black Screen:confused: I started it on the live card,,,Now What??

Help Please:( I've search the Forum tried some things, no luck yet!

---

### Post by [Snc] on 2011-01-27
> **upsman said:**
> If this was the first time I used Ubuntu, I call it Free Crap!  But I've used it for the passed 6 months, and it great!
 I tried to upgrade from 10.04 to 10.10 and I can't get the video to the right size 1280X1024. I can't get any higher than 640X480 with the Nvidia drivers installed. Without them the highest is 1024X786?? I even reinstalled the 10.04 same problem? I'm trying to load it on a Dell Inspiron 8200. The display went bad so I connected a Dell 17" LCD I had.  It has a Nvidia GeForce4 go card. 

When I booted this morning Black Screen:confused: I started it on the live card,,,Now What??

Help Please:( I've search the Forum tried some things, no luck yet!

I have very bad experience with OS upgrades and proprietary drivers. So the best way to upgrade in my opinion is to first disable third party drivers, upgrade and then re-enable them back.

My first guess would be: drivers are bad
Have you checked "System" -> "Administration" -> "Additional Drivers", if they are enabled?

Second guess would be: Your X configuration got whacked ... badly
So try to rename Xorg.conf and reboot, this will make you system try to redetect resulutions.
location:
```
/etc/X11/xorg.conf
```
(if this does no good, you can revert by renaming xorg.conf back)

---

### Post by upsman on 2011-01-27
Third Party Drivers are on,, I'll turn them off, and It will not let me change the name Xorg.conf, ""You are not the owner, so you cannot change these permissions""

Thanks soooo much for trying to help!

---

### Post by [Snc] on 2011-01-27
> **upsman said:**
> Third Party Drivers are on,, I'll turn them off, and It will not let me change the name Xorg.conf, ""You are not the owner, so you cannot change these permissions""

Thanks soooo much for trying to help!

sudo :)

```
sudo cp /etc/X11/xorg.conf /etc/X11/_Xorg.conf.org
```if this doesn't get you any result, rename it back

```
sudo cp /etc/X11/_Xorg.conf.org /etc/X11/Xorg.conf
```I know i had to reinstall my FGLRX, it made me sad

---

### Post by upsman on 2011-01-27
I reinstalled 10.10, with no third party drivers, no internet update,, there is no xorg.conf file in the X11 folder,,Monitor Preferences available: 1024X768, 800X600 and 648X480. :confused:

Stuck,,,,,,,I'm so glad I backed up my documents:P

---

### Post by collinp on 2011-01-27
In theory, Xorg can run completely without a xorg.conf. However, in the case of Nvidia drivers, you have to have one that is specifically configured for using the nVidia drivers. After installing the nvidia drivers, execute the following command and it will generate a xorg.conf for you.
```
sudo nvidia-xconfig
```

---

### Post by Maximus559 on 2011-01-27
Not sure why a fresh install of 10.04 would be acting up, but 10.10 doesn't support any Nvidia cards older than the Geforce5 (bug report [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974")). Until the issue gets resolved, your best bet is probably to stick with 10.04. I have a Geforce4 MX 420, and I'm perfectly happy with 10.04.

Of course, if you absolutely must have 10.10, there appears to be some kind of rigmarole you can go through to get your graphics card working. Check the bug report for details. Probably not really worth it, though.

---

### Post by ikt on 2011-01-27
> **maximus559 said:**
> not sure why a fresh install of 10.04 would be acting up, but 10.10 doesn't support any nvidia cards older than the geforce5 (bug report [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974")). Until the issue gets resolved,

> **this bug was fixed in the package nvidia-graphics-drivers-96 - 96.43.19-0ubuntu1**

---------------
nvidia-graphics-drivers-96 (96.43.19-0ubuntu1) maverick-proposed; urgency=low

  * new upstream release:
    - switch to new xsfbs variables to get the server abi
      (lp: #616214).
    -** add support for x.org xserver 1.9 (lp: #626974).**
  * debian/nvidia-96.postinst{.in}:
    - call dpkg-trigger with "--by-package".
  * debian/dkms/patches/nvidia-2.6.36-ioctl.patch:
    - add compatibility with kernel 2.6.3{6|7}.
 -- alberto milone <alberto.milone@canonical.com> sat, 20 nov 2010 17:36:13 +0100

:confused:

---

### Post by upsman on 2011-01-27
[B]this bug was fixed in the package nvidia-graphics-drivers-96 - 96.43.19-0ubuntu1

I installed drivers-96 and theirs only two settings: 640X480 and 320X240 :mad:

[/B] > switch to new xsfbs variables to get the server abi
      (lp: #616214).
    -** add support for x.org xserver 1.9 (lp: #626974).**
  * debian/nvidia-96.postinst{.in}:
    - call dpkg-trigger with "--by-package".
  * debian/dkms/patches/nvidia-2.6.36-ioctl.patch:
    - add compatibility with kernel 2.6.3{6|7}.

I'm not sure how to add support for x.org,,,,,,and all that other stuff ie:  switch to new xsfbs variables to get the server abi
      (lp: #616214). ???:confused:

---

### Post by Maximus559 on 2011-01-27
Like I said, there probably is some roundabout way solve this problem, but I'm not sure what it is. Try searching around. I've heard that some people have gotten the new nvidia-96 drivers working.

---

### Post by sandyd on 2011-01-27
using the non-propreity drivers (disable nvidia in hard ware drivers)
save your work
Press Control + ALT + F1
login.
run
```

sudo killall kdm
sudo killall gdm
X -configure
sudo kdm
sudo gdm

```login.
go to terminal (applications -> accessories -> terminal)

post output of
```

cat /etc/X11/xorg.conf
```and i will give you a xorg.conf that will force the resolutions.
PM me if I forget.

---

### Post by upsman on 2011-01-27
OK A fresh install of 10.04,,, Still got the same Nvidia Driver problem,,,:mad:

There is no xorg.conf to post output of?    

 racerx@racerx-laptop:~$ cat ect/X11/xorg.conf
cat: ect/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$ 

10.04 does have these issues???:confused:

---

### Post by sandyd on 2011-01-27
> **upsman said:**
> OK A fresh install of 10.04,,, Still got the same Nvidia Driver problem,,,:mad:

There is no xorg.conf to post output of?    

 racerx@racerx-laptop:~$ cat ect/X11/xorg.conf
cat: ect/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$ 

10.04 does have these issues???:confused:
its /etc not ect

---

### Post by upsman on 2011-01-27
racerx@racerx-laptop:~$ cat etc/X11/xorg.conf
cat: etc/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$

---

### Post by upsman on 2011-01-27
racerx@racerx-laptop:~$ cat etc/X11/xorg.conf
cat: etc/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$ etc/X11/xorg.conf
bash: etc/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$ 

I tried installing Nvidia x86 that did not work:(

racerx@racerx-laptop:~$ sudo /etc/X11/xorg.conf
[sudo] password for racerx: 
sudo: /etc/X11/xorg.conf: command not found
racerx@racerx-laptop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$ apd-get install pkg /usb20fd/NVIDIA-Linux-x86-1.0-8776-pkg1.run
No command 'apd-get' found, did you mean:
 Command 'apt-get' from package 'apt' (main)
apd-get: command not found
racerx@racerx-laptop:~$ apt-get install pkg /usb20fd/NVIDIA-Linux-x86-1.0-8776-pkg1.run
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
racerx@racerx-laptop:~$ sudo apt-get install pkg /usb20fd/NVIDIA-Linux-x86-1.0-8776-pkg1.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pkg
racerx@racerx-laptop:~$ 

The only thing that is different from the first install that worked great is the display is different.

](*,)

---

### Post by robert shearer on 2011-01-27
It's 
```
cat /etc/X11/xorg.conf
```

just cut and paste it into the terminal...

---

### Post by upsman on 2011-01-27
racerx@racerx-laptop:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
racerx@racerx-laptop:~$

Cut and Pasted

---

### Post by jimmyjones on 2011-01-27
I have an older system with a Geforce2 MX/MX400 video card. Ubuntu 10.10 breaks each time there is a kernel update.

I got the x86-96 package from Nvidia, and saved it in my home.

[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/NVIDIA-Linux-x86-96.43.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/NVIDIA-Linux-x86-96.43.19-pkg1.run)


After a kernel update I boot to the command line and type

sudo sh NVIDIA-Linux-x86-96.43.19-pkg1.run

asks me a couple of questions, and away it goes, I've done this now for 2.6.35-23,24 and today -25.

Might help.

---

### Post by upsman on 2011-01-27
NVIDIA Accelerated Graphics Driver for Linux-x86 (96.43.19)




 
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

                                       OK  










  NVIDIA Software Installer for Unix/Linux                      [www.nvidia.com](www.nvidia.com) 


Xserver???

---

### Post by upsman on 2011-01-27
racerx@racerx-laptop:~$ '/var/log/nvidia-installer.log'
bash: /var/log/nvidia-installer.log: Permission denied
racerx@racerx-laptop:~$ 

Something i found

---

### Post by robert shearer on 2011-01-27
> **jimmyjones said:**
> I have an older system with a Geforce2 MX/MX400 video card. Ubuntu 10.10 breaks each time there is a kernel update.

I got the x86-96 package from Nvidia, and saved it in my home.

[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/NVIDIA-Linux-x86-96.43.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/NVIDIA-Linux-x86-96.43.19-pkg1.run)


[COLOR="Red"]After a kernel update I boot to the command line and type[/COLOR]

sudo sh NVIDIA-Linux-x86-96.43.19-pkg1.run

asks me a couple of questions, and away it goes, I've done this now for 2.6.35-23,24 and today -25.

Might help.

this means reboot and choose 'recovery mode' from the grub prompt and you will go direct to the command line.
Log in as per normal and you will be ready to type...
```
sudo sh NVIDIA-Linux-x86-96.43.19-pkg1.run

```

write it down exactly. Spaces, dots,dashes,case are all important.(or take a photo now of your that text to refer to)

> asks me a couple of questions, and away it goes, 

answer the questions and at the end reboot and login to the normal desktop.

---

### Post by upsman on 2011-01-27
(be sure to exit the X server before installing a new  kernel module)

How do you exit the Xserver? :confused:

---

### Post by robert shearer on 2011-01-27
> How do you exit the Xserver?
[http://ubuntuforums.org/showpost.php?p=10404424&postcount=21](http://ubuntuforums.org/showpost.php?p=10404424&postcount=21)

---

### Post by upsman on 2011-01-27
my guey sais restart,,,, no other options,,,,and it restarts,not in term mode?

---

### Post by robert shearer on 2011-01-27
> **upsman said:**
> my guey sais restart,,,, no other options,,,,and it restarts,not in term mode?

eh ??

Are you running a full Ubuntu install or have you installed **within** Windows as a WUBI install.

If it is a full install then as soon as you restart ( and after any post screen) then hold down the shift key to get to the grub menu where you can select 'recovery mode'


When you get a chance it would be useful to look at these two links for some information that will get you up to speed with Ubuntu..
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by upsman on 2011-01-27
sh can't open  ??

Thanks did not know about the hold shift key thing

---

### Post by jimmyjones on 2011-01-27
The 'sh can't open' sounds like your not in the directory where you saved the file.

I saved it on mine to /home/jimmy

edit to add: on my mini I press ESC to get the Grub menu.

I just did it again (successfully) and wrote down my steps.

rebooted and got into Grub (I'm dual booted on that system, so I always get Grub)

Selected 'recovery'

Then selected the 'root' option (last on the list)

typed ' telinit 3'  I,d forgotten that step, but the NVIDIA package reminded me.

System had me log in ....    username, password

then typed 'sudo sh NVIDIA-Linux-x86-96.43.19-pkg1.run


************


You can type sudo sh NV [presss the 'TAB' key], if the system can see the file it will auto complete. If it can't see it, you need to cd / to the folder it was saved in.

---

### Post by robert shearer on 2011-01-28
@jimmyjones > press ESC to get the Grub menu.

**ESC** to access the menu for legacy GRUB.
**SHIFT** to access the menu for GRUB2.

jimmyjones, I see you multiboot.perhaps when you installed Maverick you manually added it to an existing(legacy)Grub  ? otherwise if it installed its own grub then it should be GRUB2 and use shift.?

---

### Post by jimmyjones on 2011-01-28
> **robert shearer said:**
> @jimmyjones 

**ESC** to access the menu for legacy GRUB.
**SHIFT** to access the menu for GRUB2.

jimmyjones, I see you multiboot.perhaps when you installed Maverick you manually added it to an existing(legacy)Grub  ? otherwise if it installed its own grub then it should be GRUB2 and use shift.?

Wow, your correct, just realized I was still running Grub, All my systems are upgrades from 8.04. I just upgraded to Grub2.

Thanks for pointing that out, now it's <Shift>

---

### Post by upsman on 2011-01-28
T hank's to all for you trying to help,,,,,,,,,Booted after work "Black Screen" I need to quit for a while, Before I smack it with a BIG HAMMER!:evil: 

I'll resume this later, Never thought this would turn into a project.

again Thanks Everyone.

---

