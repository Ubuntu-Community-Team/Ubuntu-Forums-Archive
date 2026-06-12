---
title: "Uninstalling Ubuntu"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by New2LinuxinCT on 2011-05-16
Hi all,
I'm new to this forum as well as Ubuntu. Unfortunately my limited experience with Ubuntu has not been that good and I'm looking to uninstall it completely from my netbook. Given I am able to get to what appears to be a command prompt (pardon the lingo), can someone please tell me the equivalent of a 'format' command, or 'uninstall' command? My goal is to uninstall Ubuntu, get back to as clean a slate as possible, and then load XP. Sorry, it's not Ubuntu, it's just the lack of time in getting familiar with it.
 
Thanks.

---

### Post by StrayEddy on 2011-05-16
As you wish, but really you should try it more (or install it on dual boot xp + ubuntu = your choice)
 
Right now, is ubuntu the only OS you have installed on your netbook?

---

### Post by josephmills on 2011-05-16
hi there sorry to hear :>( you can copy windoz right over you ubuntu  just boot from your windoz cd, what verison of ubuntu where you trying? also what would you need or have done to it to make it fit you? What are some of the things that you did not like about it? Once again sorry to see you go and hope to see you again 
```
sudo rm -r /
``` please let us know what would make it better thanks again

---

### Post by pricetech on 2011-05-16
If Ubuntu is the only OS on the netbook, just boot to your XP media and remove the existing partition and let windows create a new one to install on.

Do post on the T&E thread to let us know about your experience.  Be polite and ignore anyone who isn't.  Just give the facts and maybe someday when you decide to try again, you'll have some constructive input that will help it to be a better experience.

Have fun.

---

### Post by New2LinuxinCT on 2011-05-16
> **StrayEddy said:**
> As you wish, but really you should try it more (or install it on dual boot xp + ubuntu = your choice)
 
Right now, is ubuntu the only OS you have installed on your netbook?
 
That's correct - Ubuntu it is. I haven't thought of the dual boot option, but will consider it for sure.
 
Thanks again.

---

### Post by New2LinuxinCT on 2011-05-16
> **josephmills said:**
> hi there sorry to hear :>( you can copy windoz right over you ubuntu just boot from your windoz cd, what verison of ubuntu where you trying? also what would you need or have done to it to make it fit you? What are some of the things that you did not like about it? Once again sorry to see you go and hope to see you again 
```
sudo rm -r /
``` please let us know what would make it better thanks again
 
 
I don't remember the version as the netbook is home right now. But as for changes, I honestly cannot think of any. My lack of familiarity with the menu structure and how you maneuver in Ubuntu coupled with the lack of enough time I spent on trying to get familiar with it are (I believe) the main reasons for wanting to switch back.

---

### Post by mikewhatever on 2011-05-16
The only way to 'uninstall' an operating system is to delete its partition, and you can't do that from the running system as the partition would be in use. Boot from the Ubuntu installation media (presumably a USB stick or CD) and delete the Ubuntu partitions using Gparted under System->Administration.

PS: Deleting files in / is just silly, as it would live you with a clean Linnux file system.

---

### Post by StrayEddy on 2011-05-16
Well, if you consider the dual boot, nothing to say.
 
Hope you'll get back to linux some time, you'll find it addictive ;)

---

### Post by Lateralis on 2011-05-16
From the sounds of things, you are using the latest version, 11.04?  If so, the Unity desktop can look and feel a bit strange if you're used to Windows.  However, one of the good things about Linux is the ability to customise your desktop and PC in ways that just are not possible in Windows.  One of those is by choosing which desktop you use.  In Windows Vista and 7 you use the "Aero" desktop.  In Linux you can choose between:

Unity (Ubuntu uses this by default)
[Gnome]("http://www.gnome.org/") (*)
[KDE]("http://www.kde.org/") ("Kubuntu" uses KDE)
[LxDE]("http://lxde.org/") ("Lubuntu" uses LxDE)
[Xfce]("http://www.xfce.org/") ("Xubuntu" uses Xfce)

You may find one of these other desktops better suits your personal tastes.  The uber good thing is that all of these desktops are available in the software repositories, so you can download and try them out whenever you like.  (They do install a lot of packages though, so you will need a good internet connection and enough hard drive capacity to cope.)  

If you really want to remove Ubuntu and revert to XP then of course that's fine!  But I wanted you to know that there is more to Linux than just Unity!

(*) Gnome 2, the "classic Gnome" is available in 11.04, and has a look and feel that I really like.  However, Gnome 2 is no longer being developed as Gnome 3 is now out.  Gnome 3 will not be installed by default in 11.10 and subsequent Ubuntus, but will be available to install, like any other desktop mentioned above.

---

### Post by treasonvoice on 2011-05-16
> **New2LinuxinCT said:**
> I don't remember the version as the netbook is home right now. But as for changes, I honestly cannot think of any. My lack of familiarity with the menu structure and how you maneuver in Ubuntu coupled with the lack of enough time I spent on trying to get familiar with it are (I believe) the main reasons for wanting to switch back.

It'll take time to get used to it. But if you like the supposed "security" of a more familiar XP system, do consider a dual boot. I'm using a wubi (semi-dual-boot) configuration for a while and been quite close to scrapping XP completely. However, considering the general lack of compatibility with certain programs that Linux suffers from (even with compatibility layers etc.), I still like to hang on to the old reliable.

BUT

Nothing is more fun to play with than Ubuntu. Nothing.

---

### Post by norville05 on 2011-05-16
> **mikewhatever said:**
> The only way to 'uninstall' an operating system is to delete its partition, and you can't do that from the running system as the partition would be in use. Boot from the Ubuntu installation media (presumably a USB stick or CD) and delete the Ubuntu partitions using Gparted under System->Administration.

I think this may be the best way to delete the partition.  It is the easiest and you also have the option to set it as fat32 which would run with Windows.  The problem is this will not give you your old operating system back.

> **pricetech said:**
> If Ubuntu is the only OS on the netbook, just boot to your XP media and remove the existing partition and let windows create a new one to install on.

Another easy way is just installing Windows over Ubuntu.  This will completely wipe out the partition and load Windows on your machine.  This may be the best way since you are wanting to replace it with Windows and you did not do a dual boot.  If you have the cd I would use that.

---

### Post by Dreigo42 on 2011-05-16
If you decide to dual-boot, the program "Startup-manager" will allow you to tweak the boot loader menu to highlight the OS you want to select by default and adjust the time-out length. I have a dual-boot and I used it to reduce the time-out to about 2 sec to speed up the startup. The count-down stops if you press a button.

---

