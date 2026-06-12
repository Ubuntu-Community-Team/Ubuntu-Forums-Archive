---
title: "Can't Log in to Ubuntu 10-4"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Norman Thom on 2010-09-28
I've just intalled Ubuntu 10.4 onto my computer.
I shut it down last night and reopened it today
when I did so I got a dialog box that asked me to sign in
The dialog box was showing my proper username but when I add my password as requested instead of letting me into the system it returns to the dialog box.  If I intentionally use the wrong password it notifies me of a password failure.  If I, however, use the correct password it merely returns me to the dialog box.  could this be a problem when I initialized the system?  
Can anybody help me to work around and hopefully repair this problem.

Thanks for any help

Norm

---

### Post by andrewthomas on 2010-09-28
From the login screen, press <CTL>+<ALT>+<F2> and log in, then enter

```
sudo apt-get update && sudo apt-get upgrade
``` to update.

---

### Post by Norman Thom on 2010-09-28
re andrewthomas

I tried the solution you suggested and when I restarted the computer I got a grub screen to boot into Ubuntu.

I did so but got the same log in dialog with the same result
I rebooted again and went into the repair window and chose to repair broken packages the resumed normal boot.
I signed in and the computer asked for a restart.  As I did not know the command for this I restarted manually by pressing the interrupt button on my computer.  after much clicking of my monitor I got a low graphic mode indicator to which I indicated OK.  In the next window I selected restartx, again much clicking of my monitor then I got this screen:

Ubuntu 10.04.1 LTS username - desktop tty1

username-desktop login [ 22.498693] codec_read: codec 0 is not valid [0x107e5370]
this was then repeated 3x using the numbers [22.505555] [22.513152] and [22.519968]

at this point I am completely lost

Please help me

---

### Post by andrewthomas on 2010-09-28
You can restart from the terminal with 

```
sudo shutdown -r now
```If gdm will not let you log-in

From the login screen, press <CTL>+<ALT>+<F2> and log in, then enter

```
sudo aptitude update && sudo aptitude reinstall gdm
```

Are you using proprietary drivers?

What graphics card do you have?

---

### Post by Norman Thom on 2010-09-28
Tried to reinstall gdm.  when I tried to log in it took me to the same log in screen and refused to let me in.

BTW I am using an Nvidia fx 5200 graphic card and the suggested driver

Norm

---

### Post by Norman Thom on 2010-09-28
andrewthomas:

when I reboot Ubuntu it went into the low graphics mode screen
wherein it mentioned that it could not find the drivers for my Nvidia graphics card:

EE failed to open device
EE failed to initialize GLX extension (compatible NVIDIA x driver not found)

Norm

---

### Post by andrewthomas on 2010-09-28
Maybe some config file is screwed up

```
sudo aptitude purge gdm && sudo aptitude install gdm
```

---

### Post by andrewthomas on 2010-09-28
```
sudo apt-get install nvidia-current
```

---

### Post by Norman Thom on 2010-09-28
andrewthomas:

sorry to be such a pain!

Tried the purge/install command
seemed to go ok but at end all I could think to do was to type 'startx' at which point I went to a completely blackscreen with a pointer icon (movable)

Norm

---

### Post by andrewthomas on 2010-09-28
Have you done :

```
sudo apt-get install nvidia-current
```

---

### Post by andrewthomas on 2010-09-28
> **Norman Thom said:**
> 

seemed to go ok but at end all** I could think to do was to type 'startx'** at which point I went to a completely blackscreen with a pointer icon (movable)

Norm
This is where you could 

```
sudo shutdown -r now
``` to reboot to see if you can log-in through gdm.

---

### Post by Norman Thom on 2010-09-28
andrewthomas: re install nvidia-current

at least we're getting changes
ran the command you gave me and rebooted the machine
this time it booted to a black screen with a white box in upper left hand corner with my ' username@username-desktop:~$ ' in it???
any suggestions!

---

### Post by andrewthomas on 2010-09-28
what happens when you 

```
startx
```
from there?

---

### Post by Norman Thom on 2010-09-28
when I type in startx in this window I get the error:
user not authorized to run the x server, aborting

---

### Post by andrewthomas on 2010-09-28
Can you <CTL>+<ALT>+<F3> at this point and get a terminal login prompt?

---

### Post by Norman Thom on 2010-09-28
did Ctrl Alt F3
logged in
stated my last login (today @2:23 EDT on tty2)
Linux username-desktop 2.6
32.25 generic#44-Ubuntu SMP Fri Sept 17 20:26:08 UTC 2010 10.04.1 LTS

Welcome to Ubuntu!
* Documentation:  http:// help.ubuntu.com/

---

### Post by andrewthomas on 2010-09-28
Can you try to```
 startx
``` from that screen (when you are logged in.)

---

### Post by Norman Thom on 2010-09-28
Sorry old son:

When I command 'startx' I get:

Fatal server error:
server is already running for display 0
     if server is no longer running, remove /tmp/.X0-lock and start again

---

### Post by andrewthomas on 2010-09-28
If it is already running try to <CTL>+<ALT>+<F7> and see if it brings you to the desktop

---

### Post by Norman Thom on 2010-09-28
<Ctrl> <Alt> <F7> just takes me to the black screen with the white 'username-desktop' screen in upper left corner

---

### Post by andrewthomas on 2010-09-28
And the system is fully updated?
```

sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by Norman Thom on 2010-09-28
Option:

Is there a way to reinstall Ubuntu without losing certain files like Music, Pictures, Videos etc.

Norm

---

### Post by andrewthomas on 2010-09-28
is there room on your HD for another partition?

---

### Post by Norman Thom on 2010-09-28
ran safe-upgrade as suggested
outcome: 0 pkg upgraded, 0newly installed, 0 to remove and 0 not upgraded.

Norm

---

### Post by Norman Thom on 2010-09-28
re new partition - yes
I have an empty partition on there just now I believe should I reinstall on that and migrate desired files across?  and then what?
how will I distinguish between the Ubuntu sets in Grub

Norm

---

### Post by andrewthomas on 2010-09-28
> **Norman Thom said:**
> re new partition - yes
I have an empty partition on there just now I believe should I reinstall on that and migrate desired files across?  and then what?
how will I distinguish between the Ubuntu sets in Grub

Norm
There will be labels as to which partition is which.

Before you do anything you should post the output of 

```
sudo fdisk -l
```

---

### Post by Norman Thom on 2010-09-28
Output to fdisk -l follows:

Disk /dev/sda: 160gb, 160041885696 bytes
255 heads, 63 sectors/track 19457 cylinders
Units = cylinders of 16065*512 = 8225280 b
sector size (logical/physical): 512b/512b
IO size (minimum/optimal): 512b/512b
Disk identifier: 0x77e177e1

Device Boot      Start     End       Blocks    ID    System
/dev/sda1         1        261     2096451    82 Linux swap/solaris
/dev/sda2 *       262       10533   82509840  83  Linux
/dev/sda3      10534      19457    71682030   83  Linux

Norm

---

### Post by andrewthomas on 2010-09-28
ok 

```
df -h 
```will show you what is currently mounted, so you can note.  Then you can reinstall to the other partition, then copy the files over.

---

### Post by Norman Thom on 2010-09-28
Thanks for all your help andrewthomas

Norm

---

### Post by andrewthomas on 2010-09-28
You're welcome.

---

### Post by Carole S on 2010-10-01
I am in the same position.

Have tried "sudo apt-get install nvidia-current"

Response = "nvidia ia already the latest version"

Not a lot of help

---

