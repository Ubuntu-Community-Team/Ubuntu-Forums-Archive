---
title: "Boot order - want XP first!"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by ManfredKlinglmair on 2010-06-13
Hi,

since I'm using WinXP considerably more often than Ubuntu, I'd like WinXP to be the first choice of operating system on the list that appears upon switching on my laptop.

How do I change the order of OS displayed in that list? I'm sure there's some easy way, yet I don't know it.

Thanks, M.

---

### Post by bcbc on 2010-06-13
Try this link to create a custom menu, e.g. just windows and ubuntu, with any title, and order. I've used it and it's easy to follow... [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

Otherwise this is a good guide to tweaking grub [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by wilee-nilee on 2010-06-13
Not to usurp you bcbc but startup manager in synaptic is the easiest way to set the default boot.

---

### Post by bcbc on 2010-06-13
> **wilee-nilee said:**
> Not to usurp you bcbc but startup manager in synaptic is the easiest way to set the default boot.
:) I'll have to try it now

---

### Post by ManfredKlinglmair on 2010-06-13
So what do I do?
(Excuse my ignorance...)

By 'Synaptics Manager', do you mean the one accessible via the 'System' tab in the main menu?

---

### Post by oldfred on 2010-06-13
Yes System, Administration, synaptic is how to install programs (I think better than software center).

The custom menu lets you reorganize the menu anyway you want. 

Startupmanager just tells grub to boot number 5 (or what ever number it is on the menu). Windows will then be the default even though it is last on the list. You can still scroll up and select Ubuntu.

---

### Post by Don1500 on 2010-06-13
Only problem is that the start up manager does exactly what it says it will do, start "#5" first. The next time there is a kernel upgrade it is placed at the top of the list and all of a sudden "#5" is a memory test, not Windows. This will happen all the time. Grub2 is a pain in the butt if you don't want to do things they way "they" want you to. If I am wrong about this, PLEASE tell me how to make sure I can fix Grub2 once and have it stay that way no matter what changes to the system are made by the update manager and update-grub. Don't get me wrong, it happens that I like the way Grub2 is set up for my system, 2 Ubuntu Kernels, memory test, windows, two Fedora Kernels. In that order, but if I wanted something different then the problems would start. 


I believe the way update-grub searches for OS's is to start at the Grub install drive then search other drives. I have two hard drives one with Windows and one with the Linux partitions. Grub is on the Linux drive. If I put Grub on the Windows drive and booted off that, would Windows always be the primary? Just a thought. 

I know that when I added Fedora I expected it to become the first entry. Instead it is after Windows, it was like it found all the stuff that was there and added fedora to the end. Since then every new kernel is added in front of the OS it is is for. 

```

Original:
Ubuntu kernel 1
Ubuntu memory test
Windows XP
Fedora kernel 1

Updated:
Ubuntu kernel 2
Ubuntu kernel 1
Ubuntu memory test
Windows XP
Fedora kernel 2
Fedora kernel 1

Please note that this is not my complete Grub menu.
```

---

### Post by bcbc on 2010-06-13
> **Don1500 said:**
> Only problem is that the start up manager does exactly what it says it will do, start "#5" first. The next time there is a kernal upgrade it is placed at the top of the list and all of a sudden "#5" is a memory test, not Windows. This will happen all the time. Grub2 is a pain in the butt if you don't want to do things they way "they" want you to. If I am wrong about this, PLEASE tell me how to make sure I can fix Grub2 once and have it stay that way no matter what changes to the system are made by the update manager and update-grub.

+1 on this. I just installed and tested it, and found that after removing a kernel windows is no longer the default. 

Meierfra's custom menu solution works all the time (first link in my previous post), although it is slightly more work to get it setup.

---

### Post by oldfred on 2010-06-13
I agree that a custom menu is the best. There are several semi custom approaches also. But after posting all the things (most I have done) Meierfra's custom menu solution may be easier.

includes script line to limit display to two Ubuntu lines
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

So you do not get duplicate entries
I added this :
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true

after all changes"
sudo update-grub

---

### Post by wilee-nilee on 2010-06-13
I had never noticed a line default before but that seems to be correct. Learning the customizing of grub is a good tool for sure.

I had a 16 gig thumb with Lucid and maverick fully installed and removed Lucid yesterday and when I restarted it was defaulting to the memory test. All I had to do was change the line in startup manager, but I guess I should learn the customizing grub process, if I'm going to work with people in this area, thanks.;)

---

