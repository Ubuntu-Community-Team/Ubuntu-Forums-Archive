---
title: "upgraded to 11.04, now have no GUI, only command line. - please help! :)"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by rocka on 2011-04-29
Hi,
I came home to a notification to upgrade, so I did so. All appeared to go normally, just like previous upgrades.

But after rebooting, now I only have a fullscreen terminal with the command line:
```

Ubuntu 11.04 merlin-desktop tty1

merlin-desktop login:
```

after logging in with my username and password I get:
```

Last login: Fri Apr 29 18:00:21 EST 2011 on tty1

 * Documentation: https://help.ubuntu.com/

merlin@merlin-desktop:~$ _
```


What should I do to get my desktop back?

---

### Post by MooPi on 2011-04-29
Try ```
startx
```

---

### Post by rocka on 2011-04-29
thanks for the reply, MooPi.

when I typed that, a large amount of text scrolled past way too fast to see it; here is what's left on the screen now:

```

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 29 18:39:15 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.comf.d"
FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernal module. Please check your
(EE) NVIDIA: system's kernal log for additional error messages.
(EE) Failed to load module "nvidia" (module specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support at http://wiki.x.org for help

Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
merlin@merlin-desktop:~$

```

I should point out that there was nothing wrong this morning when I wen to work, and it was fine when I got home. In fact it was fine all the way through the upgrade process, right up until after the reboot.

I don't know how to access those log files just from the command line. [and not sure if I'd understand anything in them anyway! LOL :) ]

---

### Post by SunnyRabbiera on 2011-04-29
Do yourself a favor and use openSUSE, its far more stable and wont force the limited unity on you

---

### Post by rocka on 2011-04-29
Thanks for your input, Sunny.
I'm just not quite sure how this will help me right now - I have nothing but a black screen and a command line. Right at this moment I'm more focused on getting my screen back..

---

### Post by Balleke on 2011-04-29
Hi,

I have the same problem. (only command prompt after upgrade to 11.04):(

---

### Post by Baldrick_NZ on 2011-04-29
I had this prob with a kernel update once.

From memory I fixed it with an update of grub.
```
sudo update-grub
```
Enter your password when requested.

Then reboot the PC.

---

### Post by rocka on 2011-04-29
ok, tried that:
again it's scrolled a bunch of stuff up the screen, starting this and stopping that - CUPS, sound card stuff etc etc. Nothing to do with the video as far as I can see. Everything says [ OK ] on the right hand side, except for one: automatic crash report generation says [ fail ].

After logging in with username and password, I just get the command line same as before. Typing "startx" also gets me the same result as before, too.

---

### Post by sprintrider on 2011-04-29
Exactly the same problem here :( I did manage to get past the black screen by pressing esc when prompted during startup = watch the top of the screen - this gets you to the os boot option choices menu - and then choosing the third line down, the second one from the top that isn't 'recovery mode'.

You get the Gnome desktop then, but things seem pretty scrambled.

Wifi will detect but not connect to wireless routers

The active zone of the mouse pointer is dozens of pixels above the pointer position in applications

I can't find my way into Admin tools - everything seems frustratingly dumbed-down to a sidebar on the left with user locations and productivity software icons

you need to get into the desktop every time by selecting the os boot choice screen as I've described - it does not remember

I'm using a Dell Vostro 1710 and wish I could restore back to the previous OS - not happy at all.

---

### Post by beew on 2011-04-29
Instead of spending hours trying to fix a blotched upgrade (and not to mention keep posting back and forth on the forum) why don't you guys just do it the easy way and do a reinstall? It will take only 20 minutes. I always do fresh install (keeping my /home partition intact) instead of upgrades. There are a lot more opportunities for things to go wrong in upgrade (if you have proprietary graphic cards, ppas or a lot of customization) and it takes a lot longer especially if you have intermediate versions between the initial and final versions.

---

### Post by rocka on 2011-04-29
> **beew said:**
> Instead of spending hours trying to fix a blotched upgrade (and not to mention keep posting back and forth on the forum) why don't you guys just do it the easy way and do a reinstall? It will take only 20 minutes. I always do fresh install (keeping my /home partition intact) instead of upgrades. There are a lot more opportunities for things to go wrong in upgrade (if you have proprietary graphic cards, ppas or a lot of customization) and it takes a lot longer especially if you have intermediate versions between the initial and final versions.

Hi Beew,
so I'll have to download the whole thing again on my netbook, then boot the desktop from USB and install from there?

How do I make sure my /home doesn't get written over?

---

### Post by waspbr on 2011-04-29
is your /home in a separate partition?

---

### Post by rocka on 2011-04-29
> **waspbr said:**
> is your /home in a separate partition?

Honestly, I can't remember.

I've never needed to even think about since I got the machine close on 3 years ago. I would have just accepted the defaults when I installed it at that stage. [I think that may have been 8.something or early 9.something]. 

I don't suppose there's any way to find out now, is there? :confused:

---

### Post by waspbr on 2011-04-29
from the command line you can use 


> sudo fdisk -l

---

### Post by rocka on 2011-04-29
Hi Waspbr,

This is what that shows:

```

Device      Boot    Start      End      Blocks    Id   System
/dev/sda1     *         1   120656   969169288+   83   Linux
/dev/sda2          120657   121601     7590712+    5   Extended
/dev/sda5          121657   121601     7590681    82   Linux swap / Solaris


```

does that tell you anything?

---

### Post by Lucas32 on 2011-04-29
What happens if you choose the safe/recovery options in Grub?
It sounds like gnome/X isn't starting because the nvidia driver won't load.  check /etc/X11/ and see if you multiple copies of xorg.conf  perhaps you might need to revert to an older or backup copy of xorg.conf before you installed the nvidia driver.

---

### Post by waspbr on 2011-04-29
I reckon that your sda1 is your /home partition and your root, but just to be on the safe side of things. try this (should have asked that in the first place)

```
cat /etc/fstab
```


as for your problem, I think I may have seen it before. Try checking if your xorg is installed.


```
sudo apt-get install xserver-xorg
```

and if possible also do a 

```
sudo apt-get update && sudo apt-get dist-upgrade --fix-missing
```


as a last resort, delete (or rename) you /etc/X11/xorg.conf and reboot. This will force the computer to make another one.

---

### Post by beew on 2011-04-29
> **rocka said:**
> Hi Beew,
so I'll have to download the whole thing again on my netbook, then boot the desktop from USB and install from there?

Download the iso, make a live usb and then boot from it and install.

> How do I make sure my /home doesn't get written over?

If you have a separate /home partition you should choose partition manually during install and use the same /home partition without formatting it, that will keep your data and settings. That's why it is recommended to keep a separate /home partition.

I can't tell if you have one. What is in the extended partition?

Post the output of the command "df -h"

---

### Post by waspbr on 2011-04-29
I may have to go soon, so I hope someone can take over here


anyway I found a thread with a similar issue 
[http://ubuntuforums.org/showthread.php?t=1654243]("http://ubuntuforums.org/showthread.php?t=1654243")

I hope this helps, I had a derp moment 

```
cat /etc/fstab
```

or 

```
df -h
```

would have been a lot more helpful at telling if the /partition was available.

---

### Post by rocka on 2011-04-29
Thank you to all who are helping me on this one...

I have now booted into recovery mode, and started it in "low graphics mode". So at least I can now see my way around the system again:)

in the /etc folder there's a ton of those xorg.conf files:

```
xorg.conf
xorg.conf.backup
xorg.conf.dist-upgrade-200905032026
xorg.conf.dist-upgrade-200911260142
xorg.conf.dist-upgrade-201004302147
```
and so on.
```
merlin@merlin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             910G  859G  5.5G 100% /
none                  2.0G  712K  2.0G   1% /dev
none                  2.0G  572K  2.0G   1% /dev/shm
none                  2.0G  332K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
merlin@merlin-desktop:~$
```
```
merlin@merlin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f3444396-75cb-4ed5-b239-c880d860acdc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7897d2d2-4892-44f2-8e47-be67ca699718 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
merlin@merlin-desktop:~$
```


As I mentioned before, if I have to resort to it I will buy another hard drive and do a fresh install on it, then recover my docs etc from the original drive later. But I'd like to get this going tonight if possible...

---

### Post by beew on 2011-04-29
If you buy another hard drive and do a fresh install on it you have the added bonus of having a portable installation. I have one external drive and I have installed 5 Linux in it and I can boot it off almost any computer (I have tried a lot and most work out of the box) :)

---

### Post by waspbr on 2011-04-29
As far as I can see, there is no /home partition, so a new install would wipe your current home.

---

### Post by rocka on 2011-04-29
Thanks again guys.
I think I'll take the safest option and do a fresh install tomorrow.

I've downloaded the iso and created a startup usb stick ready.

cheers!
8-)

---

### Post by eriktheblu on 2011-04-29
Your earlier posts makes me suspect that the graphics driver could be a part of your problem. I would suggest removing it, but a brief search does not provide a method to do that from the CLI.

Before you reinstall, boot to a live session and open Gparted. If you have enough empty space, you may be able to make an adequate partition to copy over your /home.

Total Disk Size = X
Total data on / partition = Y
Swap size = A

if X - (Y+A) > Y - 20 GB, you should be ok.

In that instance, resize your / partition (SDA1) so it is just big enough to contain the data it has. Create a new partition (you may wish to first expand your extended partition) formatted to EXT. Once done, copy your /home files to the new partition. 

If you have enough disk space, you can leave it there, but if you need to create more room, you can format your original root partition and create a new one (20 GB is usually more than enough for /, but you can get away with less). That will give you room to expand your new /home partition.

Once that is done, reinstall, and identify your partitions and mount points in the advanced partitioning dialog.

---

### Post by rocka on 2011-04-29
Hi Erik,

yeh, nice thought, but there's only about 5G free on the drive right now. I kinda had it in the back of my mind that I would be needing a new drive soon anyhow, this has just given me the push:)

---

### Post by mastablasta on 2011-04-29
i am not sure if this was already said but the OP problem is simple. he didn't uninstall graphics card drivers before updating to new operating system. same thing has to be done in windows usually.

so now you need to remove the old drivers and install the new one. this will solve the issue.

if your card is ATI this is how your remove it: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by rocka on 2011-04-29
I wasn't aware there was any need to do anything about the video card driver. There was no notification or warning message of any kind, and all the previous upgrades had worked just fine.

Btw the video card is a GeForce 9800.

---

### Post by kaldor on 2011-04-29
Proprietary drivers are usually a culprit when an upgrade goes wrong. As an NVIDIA user who needs non-free drivers, I *always* do a fresh install.

---

### Post by roh8880 on 2011-04-29
Before you wipe your hard drive and try again, it may be worth giving one last thing a shot.

```
gksudo apt-get install kdm
```


I had the same issue as you. No GUI. All I had was the command prompt. 

Try this and see if it works for you!

---

### Post by scooby359 on 2011-04-29
I had a problem with my graphics card, Nvidia GeForce FX 5800. Did an upgrade initially from 10.10 and when it didn't work, I assumed it was because I did it early using the Beta release I guessed was buggy.

So I did a clean install and had the same problem, could boot up, got the wallpaper, but nothing else.

The way I worked round it was at the Grub menu, pick recovery, and load the safe graphics mode. That loaded up the old style gnome desktop where I could change my graphics card driver - using the experimental Ubuntu driver seems to work ok. Then, log out of the session, and at the log in screen, change the interface to use Ubuntu Classic as Unity still won't work

It's not ideal, but it's better to use the Classic desktop than none at all until a bug fix comes through.

Hope this helps!

---

### Post by rocka on 2011-04-29
> **roh8880 said:**
> Before you wipe your hard drive and try again, it may be worth giving one last thing a shot.

```
gksudo apt-get install kdm
```


I had the same issue as you. No GUI. All I had was the command prompt. 

Try this and see if it works for you!

Thanks for the thought, but unfortunately it didn't work.
```
<dpkg: error processing kdm (--configure):
 subprocess installed post-installation script returned error exit status 9                                             &#9474;
Errors were encountered while processing:   &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
 kdm                                         
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by rocka on 2011-04-29
I have resolved it!
I was googling more or less aimlessly, and came across a similar thread in the multimedia forum: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

Turns out all I had to do was choose
[Ubuntu icon] > System > Administration > Additional Drivers
and then download the recommended one, and then reboot!

Thanks to all who replied and helped me - every little bit of learning is worthwhile!
:D

---

### Post by cobolt01 on 2011-04-30
```
FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernal module. Please check your
(EE) NVIDIA: system's kernal log for additional error messages.
(EE) Failed to load module "nvidia" (module specific error, 0)
(EE) No drivers available.
```

Can't believe nobody spotted this before. Obviously he just needed to install/re-install his nvidia driver. Not a big problem :P

---

### Post by ozarga on 2011-07-05
> **rocka said:**
> I have resolved it!
I was googling more or less aimlessly, and came across a similar thread in the multimedia forum: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

Turns out all I had to do was choose
[Ubuntu icon] > System > Administration > Additional Drivers
and then download the recommended one, and then reboot!

Thanks to all who replied and helped me - every little bit of learning is worthwhile!
:D
Hey I just upgraded my ubuntu last night to 11.04 and I'm having the same problem as you.

How were you able to select the '[Ubuntu Icon] > System > Administration > Additional Drivers' If you didn't had a GUI for the login? did you reboot in safe graphic mode or something?

Please explain the details, I'm really newbie in Ubuntu

---

### Post by rocka on 2011-07-05
> **ozarga said:**
> Hey I just upgraded my ubuntu last night to 11.04 and I'm having the same problem as you.

How were you able to select the '[Ubuntu Icon] > System > Administration > Additional Drivers' If you didn't had a GUI for the login? did you reboot in safe graphic mode or something?

Please explain the details, I'm really newbie in Ubuntu


yes, I had rebooted in safe or basic mode.
I can't remember, to be honest, it was quite a while ago.

I think you hit <ESC> when grub is loading [there's a quick little count down on the screen as it is booting up] and then you get some boot options to choose from. It took me quite a few tries to get the timing just right to "catch" it.

I'm sure there are many others who are far more knowledgeable than me who can guide you more precisely. I'm more of a "click this, try that, once it's working again don't mess with it" kind of guy :)

---

