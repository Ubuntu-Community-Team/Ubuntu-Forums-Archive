---
title: "100% CPU usage."
date: 2009-06-25
forum: New to Ubuntu
---

### Post by SVWander on 2009-06-25
This Dell Inspiron 1200 is running at 100% cpu usage right now and it isn't dropping. I am worried about it overheating so I am going to keep this short. I have tried Killing Processes in the System Monitor but no matter what I close the usage stays at 100%.
I am running 9.04 with all the updates, with 1 gig of RAM. 
Any help would be appreciated!

---

### Post by LewRockwell on 2009-06-25
open a terminal window and run top to check your cpu usage

```
top
```

---

### Post by LewRockwell on 2009-06-25
if that's the only computer you can use to connect to this forum for troubleshooting then I would suggest making sure the cooling inlet and outlet are unobstructed and also a fan blowing over the machine would help to keep it much cooler

---

### Post by starcraft.man on 2009-06-25
Open a terminal (applications > Accessories > Terminal), type in *top* and then hit enter. After that, you should see a long list of things sorted by CPU%. This is a live task manager, to stop it updating hit Ctrl+C. Then copy the fixed output into a new reply to this thread if you don't know what should or shouldn't be there ( with code tag, the number sign in the GUI). The entries are in descending order of CPU use so first thing should be your problem.

Edit: Beaten to post!

---

### Post by lovinglinux on 2009-06-25
It's probably the Remote Desktop.

Go to "System >> Preferences >> Startup Applications", disable the Remote Desktop, then reboot.

Also check if you have the latest proprietary drivers for you graphics card.

If you have intel graphics card then visit [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by del_diablo on 2009-06-25
> sudo apt-get install htop
xterm -e htop

htop is top + kill + a bit more colors

---

### Post by SVWander on 2009-06-25
> **LewRockwell said:**
> if that's the only computer you can use to connect to this forum for troubleshooting then I would suggest making sure the cooling inlet and outlet are unobstructed and also a fan blowing over the machine would help to keep it much cooler

The cooling system is clean. I took the entire thing apart a month or so ago to repair the DC power jack.
tm

---

### Post by SVWander on 2009-06-25
> **lovinglinux said:**
> It's probably the Remote Desktop.

Go to "System >> Preferences >> Startup Applications", disable the Remote Desktop, then reboot.

Also check if you have the latest proprietary drivers for you graphics card.

If you have intel graphics card then visit [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Disabled Remote Desktop and rebooted.

Yes, the Dell Inspiron 1200 uses the Intel graphic card. I will visit that thread as soon as I finish writing this. tm

---

### Post by SVWander on 2009-06-26
> **LewRockwell said:**
> open a terminal window and run top to check your cpu usage

```
top
```

Okay I ran htop but don't understand what's it is telling me. I have  tried to attach the screen shot to this message. However I cannot take the screen shot in Gnome! This screen shot was taken in KDE. Each time I try in Gnome I get an error message.

---

### Post by reeseslover531 on 2009-06-26
what processor is this? Also it looks like Ksnapshot is using the most CPU which is very odd.

---

### Post by SVWander on 2009-06-26
> **reeseslover531 said:**
> what processor is this? Also it looks like Ksnapshot is using the most CPU which is very odd.

Intel Celeron M processor 1.30GHz
L2 1024 KB
Total Memory 1247  Free 60%
using Gnome 2.26.1
Kernel      2.6.28-13-generic
GCC version 4.3.3 (i486-linux-gnu)
Xorg version unknown (09 April 2009 02:10:02 AM)
VGA compatible controller:
Intel Corporation Mobile 915GM/GMS/910ML Express Graphics Controller

---

### Post by SVWander on 2009-06-26
> **lovinglinux said:**
> It's probably the Remote Desktop.

Go to "System >> Preferences >> Startup Applications", disable the Remote Desktop, then reboot.

Also check if you have the latest proprietary drivers for you graphics card.

If you have intel graphics card then visit [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I followed the thread and updated the drivers. Rebooted and if anything the CPU usage was still 100%. Booting into KDE seems the only solution that works but I like the Gnome interface better.

---

### Post by LewRockwell on 2009-06-26
How did it run when you used the live-run test-drive function?

Get [http://www.partedmagic.com/](http://www.partedmagic.com/) which is a live-run utilities suite and see how that works

---

### Post by SVWander on 2009-06-26
> **LewRockwell said:**
> How did it run when you used the live-run test-drive function?

Get [http://www.partedmagic.com/](http://www.partedmagic.com/) which is a live-run utilities suite and see how that works

Ubuntu Gnome has run on this machine for the last year or so. Only in the last week has the CPU usage been a problem. It is ONLY a problem in Gnome. In KDE the CPU usage is normal. Right now I have VirtualBox, XP Guest, Firefox and Pidginrunning and htop shows the % of CPU usage seldom goes above 50%.

---

### Post by Papa-san on 2009-06-26
Are you looking at it through a terminal with the 'top' command, or are you using 'System>Admin>System monitor'?
The sys monitor can be buggy, and can use all of your CPU on running itself...

---

### Post by SVWander on 2009-06-27
> **Papa-san said:**
> Are you looking at it through a terminal with the 'top' command, or are you using 'System>Admin>System monitor'?
The sys monitor can be buggy, and can use all of your CPU on running itself...

No I am looking at 'top' output not System Monitor. I also use GKreIIM that has a monitor function but its real function on this laptop is to control the fan speed.

---

### Post by NightwishFan on 2009-06-27
Did you install using an Ubuntu GNOME CD? Make sure you check it for errors. The '100% cpu' was ALWAYS (for me) a bad cd used in an installation.

---

### Post by SVWander on 2009-06-27
> **NightwishFan said:**
> Did you install using an Ubuntu GNOME CD? Make sure you check it for errors. The '100% cpu' was ALWAYS (for me) a bad cd used in an installation.

It was installed months ago from a CD that came from Shipit. I might just transfer all my user files to a USB drive and reinstall. I really like Gnome better than KDE for this low powered machine.

---

### Post by durand on 2009-06-27
You say that you are only using gnome but the screenshot looks a lot like kde and ksnapshot and krunner are both kde programs.

---

### Post by LewRockwell on 2009-06-27
> **durand said:**
> You say that you are only using gnome but the screenshot looks a lot like kde and ksnapshot and krunner are both kde programs.

Original poster already stated...Gnome=broken...using KDE=screenshot

---

### Post by durand on 2009-06-27
Whoops, I may have misread that :S

---

### Post by SVWander on 2009-06-27
> **durand said:**
> You say that you are only using gnome but the screenshot looks a lot like kde and ksnapshot and krunner are both kde programs.

Sorry no, I am using KDE because in Gnome the cpu usage is 100% and bogs the machine down.

---

### Post by durand on 2009-06-27
So do you know what program is causing problems in gnome? You should start gnome, run h/top and post the results here. The programs there would be different to in kde so we can't diagnose the problem with your kde screenshot.

---

### Post by SVWander on 2009-06-28
> **durand said:**
> So do you know what program is causing problems in gnome? You should start gnome, run h/top and post the results here. The programs there would be different to in kde so we can't diagnose the problem with your kde screenshot.

I would like to be able to do just that but for some reason I get an error message each time I try to take a screenshot. I tried to search for information about the error message with no luck. It is impossible, at least for me, to write down the readings because they flash on and off to fast for me.

---

