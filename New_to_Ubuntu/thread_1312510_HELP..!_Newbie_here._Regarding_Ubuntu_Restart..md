---
title: "HELP..! Newbie here. Regarding Ubuntu Restart."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by nicofaller on 2009-11-03
Hi. I am only in my 3rd hour of Ubuntu, and its amazing. But I encountered some problems.

1. Every time I would restart (reboot) my computer, I would LOOSE all my settings. Such as my wallpaper, my bookmarks in mozilla as if I used UBUNTU for the first time again.

2. Every time I would restart my computer: I would encounter a notification telling me to remove my flash drive where I have my ubuntu in. And if I don't it would not restart or turn off properly. thus making me press the power button to turn my laptop off.

3. I cannot seem to install an Ubuntu in my 320Gb external HD. I am using ubuntu now but on an 8Gig flashdrive, which isn't mine... 

Please Help! thanks so much.! 

Nico

---

### Post by yeats on 2009-11-03
Hi, and welcome.  When you're running from a Live USB, unless it has been configured to retain your settings, this is the way it will work.

> 3. I cannot seem to install an Ubuntu in my 320Gb external HD. I am using ubuntu now but on an 8Gig flashdrive, which isn't mine...

What about the installation is giving you trouble?

---

### Post by nicofaller on 2009-11-03
Hi CHRIS,

I cannot seem to understand what its trying to ask me. I know its straight forward but I am having a hard time. I am using a WD 320Gb external HD on NTFS format.. do you have any step by step..?  I get lost on the partitioning thingy..

---

### Post by yeats on 2009-11-03
Are you only installing Ubuntu?  Or are you trying to dual boot with Windows or any other OS that is already installed?  If only Ubuntu, try automatic partitioning (select to use the entire disk) and just walk through the rest of the installation (which will be simple).

---

### Post by waspbr on 2009-11-03
from what you have posted, it seems that you are using a live usb (non-persistent install), which means that the settings are not going to stick after reboot. 

On live sessions, you have an installation icon on the Desktop, alternatively you may press alt+F2 and type the command "ubiquity" which should start the installation dialogue. 

this video should cover all the installation basics

[http://www.youtube.com/watch?v=_MLKaOKRhBE]("http://www.youtube.com/watch?v=_MLKaOKRhBE")

---

### Post by nicofaller on 2009-11-03
@CHRIS: I already have Ubuntu on my 8Gig Flash and I want it to install on my 320Gig. Do you think I should just stick to my 8gig and just use the 320Gig as an extra hard drive for my movies and stuff.? 

@WASPBR: Yeah, I have an "install ubuntu 9.10" icon on my desktop. I am going to view the video after i install ADobe Flash.. :) 

Ohh yeah by the way. My INTERNAL Hard Drive w/c came w/ my laptop is busted.. its making a Crackling sound. SO installing Ubuntu on my local (internal) HD is OUT!!! :)

---

### Post by nicofaller on 2009-11-03
WASPBR: I opened the youtube link you gave and it asked me to get a FLASH PLAYER, so i went to adobe, after download it gave me this: 

[SIZE=4]**Software index is broken**[/SIZE]
*"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."*

---

### Post by rockin_goliath on 2009-11-03
The previously posted video is very good. Pay attention to Step #4, where the disk is partitioned. I would click manual and select the external hard drive as the installation destination.

BE VERY CAREFUL HERE! If your settings are incorrect, you might end up formatting the internal hard drive where some other operating system exists.

Also, at the very end of the installation process, you might have to click "Advanced" and make sure GRUB is installed to the external hard drive. I can't really give any more information without the computer sitting in front of me or some screenshots of the manual partitioning screen.

---

### Post by nicofaller on 2009-11-03
I attached a screenshot while installing ubuntu 9.10

---

### Post by nicofaller on 2009-11-03
Please Help!

---

### Post by oskarloko on 2009-11-03
It seems that you have mounted - used with Nautilus, the file explorer, a partition of your main hard disk ( /dev/hda ). 

Simply say yes and unmount it, it won't do anything to your disk.

Caution with next steps...

---

### Post by 3rdalbum on 2009-11-03
"Mounting" is the process where you tell the operating system that it's okay to start working with a disk. So yes, you just want to "unmount" that disk, because it can't erase the disk while it's still in use by the main part of the operating system.

---

### Post by nicofaller on 2009-11-03
After running the "Install Ubuntu 9.10" I run the Steps 1 to 6 and then on installation I would be stuck on 5% and then crash to desktop. And then I would get 2 notifications.

I attached the screenshots. Help! thanks!

---

### Post by waspbr on 2009-11-03
not really sure what is wrong here, it should have gone through with the installation, it is very unusual for ubiquity to break like that. Is that the beta version or the stable release? 

considering that is the stable release, try rebooting and try again 

if that doesn't work, try downloading a cd from ubuntu.com


does else anyone have a clue on how to get around this?

---

### Post by yeats on 2009-11-03
You might try the alternate installation disk.  Look for "Alternate install CD" on this page:

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by yeats on 2009-11-03
Another thought... have you tried selecting the "Install Ubuntu" option from the startup menu of the Live USB?  You might be exhausting available memory after booting into the full GNOME environment.

---

### Post by nicofaller on 2009-11-03
how do i go to the LIVE install in the Boot menu w/o going to GNOME..??

---

### Post by Locke_99GS on 2009-11-03
When you boot off the flash drive, a menu shows up asking you what you want to do (check disk for defects, try ubuntu without changes, install ubuntu, &c...) Choose "Install".

---

