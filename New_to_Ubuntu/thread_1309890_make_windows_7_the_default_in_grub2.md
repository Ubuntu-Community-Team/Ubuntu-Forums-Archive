---
title: "make windows 7 the default in grub2"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by nikhilbhardwaj on 2009-11-01
i've got a new laptop with windows 7
i've installed ubuntu 9,10 on it 

grub2 recognized windows7 and boots easily
how can i make windows 7 the default option in grub2??

it says that the file grub.cfg shouldn't be edited

---

### Post by Tykin on 2009-11-01
The easiest, least technical way is to download the startup-manager.

Goto the Ubuntu Software Center and search "startup". The one you want is called startup-manager. It has a picture of a wrench. 

After you install the software, it should be in your system --> administration tab. Open it up and you will see the option "Default Operating System." Simply hit the dropdown, select windows 7 and close. 


You should be good to go!

---

### Post by ajgreeny on 2009-11-01
Startup manager does not work properly in grub 2, apparently, so that may not work, though is worth a try.

Has anyone actually sorted out how to add anything to grub 2 manually?  I used to do it all the time in legacy grub without a second thought, but now?  Well, I've read all the wiki about grub 2, and which files I can edit before running update-grub, but I'm completely baffled about what I actually put into the **/etc/grub.d/40_custom** file.  Perhaps I'm just a bit thicker than I thought, but this grub 2 leaves me a bit overwhelmed, I'm afraid.

And why oh why did they choose to count devices from 0, but partitions on the device from 1, so **hd0,0** now suddenly becomes **hd0,1**?

Never mind, hopefully it will all become clear as time progresses and I start using grub 2 instead of legacy grub which is on my working jaunty system.

---

### Post by oldfred on 2009-11-01
This thread has more info:
[http://ubuntuforums.org/showthread.php?t=1308701](http://ubuntuforums.org/showthread.php?t=1308701)

---

### Post by ranch hand on 2009-11-01
You should look at the link in my sig.

Go to /etc/default/grub and edit the line for the default OS there.

---

### Post by nikhilbhardwaj on 2009-11-02
> **ranch hand said:**
> 
Go to /etc/default/grub and edit the line for the default OS there.

thanks
that did it

---

### Post by ranch hand on 2009-11-02
Great

---

### Post by nariub on 2011-09-08
Sorry to revive an old thread.

Had this same issue today

mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober

update-grub

it moves the detected OS partition to the top of the GRUB menu
now when you update the Ubuntu Kernel you dont have to worry about it moving around.

if you update grub. you will have to go back and rename 30_os-prober again.

if you have multiple windows partitions, it will probably detect them in order.
and startupmanager would be a better bet

but for basic dual boot with;  one Ubuntu and one Windows
make the os-prober script run before the linux kernel script will make windows the default.

---

### Post by dataq on 2012-01-13
> **nariub said:**
> Sorry to revive an old thread.

Had this same issue today

mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober

update-grub

it moves the detected OS partition to the top of the GRUB menu
now when you update the Ubuntu Kernel you dont have to worry about it moving around.

if you update grub. you will have to go back and rename 30_os-prober again.

if you have multiple windows partitions, it will probably detect them in order.
and startupmanager would be a better bet

but for basic dual boot with;  one Ubuntu and one Windows
make the os-prober script run before the linux kernel script will make windows the default.

Thanks Nariub. Just found this thread and your tip worked perfectly. 

Startup Manager didn't work right. It made the relevant changes to grub.cfg but grub would still boot to Ubuntu instead of Windows 7.

---

### Post by OliverN on 2012-01-20
> **nariub said:**
> Sorry to revive an old thread.

Had this same issue today

mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober

update-grub

it moves the detected OS partition to the top of the GRUB menu
now when you update the Ubuntu Kernel you dont have to worry about it moving around.

if you update grub. you will have to go back and rename 30_os-prober again.

if you have multiple windows partitions, it will probably detect them in order.
and startupmanager would be a better bet

but for basic dual boot with;  one Ubuntu and one Windows
make the os-prober script run before the linux kernel script will make windows the default.

yea, this was just what I needed. thanks a bunch.

---

### Post by Mark Phelps on 2012-01-20
Instead of startup manager, which doesn't work well anymore, you should be using Grub-Customizer: 

[http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer")

---

### Post by lthanga on 2012-01-30
> **dataq said:**
> Thanks Nariub. Just found this thread and your tip worked perfectly. 

Startup Manager didn't work right. It made the relevant changes to grub.cfg but grub would still boot to Ubuntu instead of Windows 7.

Run grub2-update after running startupmanager

---

### Post by danmbox on 2012-02-07
> **nariub said:**
> Sorry to revive an old thread.

Had this same issue today

mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober

update-grub



While this works, it will stop working every time the package grub-common (which owns 30_os-prober) gets upgraded. That's the issue with a lot of the fixes I see in this forum.

The fact is that the grub2 configuration is not well designed. Otherwise you wouldn't see all these threads around. It *should* be a simple matter to add some file to /etc/grub.d to make your preferred entry stick (and maybe it is, but it's not discoverable -- the files in grub.d are basically unreadable).

---

### Post by InnerBushman on 2012-09-11
> **nariub said:**
> Sorry to revive an old thread.

Had this same issue today

mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober

update-grub

it moves the detected OS partition to the top of the GRUB menu
now when you update the Ubuntu Kernel you dont have to worry about it moving around.

if you update grub. you will have to go back and rename 30_os-prober again.
(...)
but for basic dual boot with;  one Ubuntu and one Windows
make the os-prober script run before the linux kernel script will make windows the default.

Heh. I'll dig it up too.

If i'm not wrong, what i just did to your method should prevent the os-prober to be moved back in place after update.

I have added file 06_move-os-prober:
```

#! /bin/sh -e

# This script checks if ther 30_os-prober file exists
# and renames it to 07_os-prober in order to
# place any possible windows OS menu entries on
# top of the menu list.

if [ -e "/etc/grub.d/30_os-prober" ]
then
  mv /etc/grub.d/30_os-prober /etc/grub.d/07_os-prober
fi


```Hope anyone will find it useful.  ;)

---

### Post by Elfy on 2012-09-11
and I'll close it.

---

