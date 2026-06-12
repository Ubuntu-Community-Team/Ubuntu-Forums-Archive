---
title: "Weird SU / SUDO Problem"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by pruitthall on 2010-11-03
Newbie here, so bear with me...I've got Ubuntu 10.10 installed on a 4Gb flash card. Love it. I've got some time invested in this installation so I'm asking the experts what I can do to prevent having to burn another copy!
 
Two days ago, when booting from Flash copy, the 'normal' user ('Ubuntu') signed in. On this installation, I boot from the flash onto a HP Pavilion Slimline and only have two (2) users; Ubuntu and myself. No biggie, always has worked fine. But on this day, some weird 'Gnome Keyring' message came up...I honestly think the culprit was a Gnome Program (Gnome Do) that I installed the previous day. Now I don't know a Gnome Keyring from a spoon, but somehow I got out of the message (mutliple 'escape' key hits, and finally had to just power down the system) but in doing so, something must've gotten way corrupted.
 
On next boot, all appeared fine, all programs worked, EXCEPT: Package installer wouldn't work, Ubuntu software center wouldn't work and the Archive Manager wouldn't work. Hmmm.....must've whacked something. Went into Terminal and was going to SUDO something when I discovered, my \etc\sudoers (or something like that file) was MAJOR messed up. Line errors everywhere. In doing a 'More' of the file, it's all graphic characters. Maybe this file is causing my other problems, but I know I've got to get SUDO and/or SU working again and here's my problem:
 
I wanted to install / write a new \etc\sudoers file....I tried to boot into Recovery mode (quite the journey unto itself!) and I got a Terminal window. But even in Recovery mode, issuing a 'sudo' command results in the same errors that I got in normal mode.
 
So, my dilmena is I know my \etc\sudoers file is whacked. Everything else, except the previously mentioned programs work fine. But I absolutely do NOT know how to get this file back, because even recovery mode won't work. I tried to use a LIVECD version on a machine, but when I plug in the FLASH card, it doesn't resemble the file structure that I see on the FLASH when it's the boot device. 
 
I know there's gotta be an easier solution than just redoing this flash; I've got a ton of time invested in nVidea drivers and Broadcom wireless and just don't want to start over. Plus I think I may learn something, besides don't EVER, EVER hard boot Ubuntu without safely shutting down....gotta say, Windows sure is well behaved there!
 
Can any experts help me with this one?
 
Many thanks in advance!
 
PH

---

### Post by Old *ix Geek on 2010-11-03
> **pruitthall said:**
> But on this day, some weird 'Gnome Keyring' message came up...The default keyring pop-up will appear for a number of different programs; just enter a password into it.
> Went into Terminal and was going to SUDO something when I discovered, my **[color="red"]\etc\sudoers[/color]** (or something like that file) was MAJOR messed up...it's all graphic characters.Yeah, it got whacked. (NOTE: There are no backslashes in *nix directory paths. :eek:)
> I wanted to install / write a new \etc\sudoers file....I tried to boot into Recovery mode (quite the journey unto itself!) and I got a Terminal window. But even in Recovery mode, issuing a 'sudo' command results in the same errors that I got in normal mode.Perhaps I'm just not seeing it, but I don't see where you tried anything with **su**. Did you? That is totally unrelated to whether or not you're in the /etc/sudoers file.
> But I absolutely do NOT know how to get this file backIt's just a text file with a couple of values that are changed to reflect your user setup. I'm pasting mine in below and you can copy it, then adjust the values accordingly.
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by Zzl1xndd on 2010-11-03
When in Recovery mode did you attempt to complete your task without Using sudo? I could be wrong but it was my understanding the Single User mode gave your Root access meaning Sudo wouldn't be required.

---

### Post by bioterror on 2010-11-03
> **pruitthall said:**
> Newbie here, so bear with me...I've got Ubuntu 10.10 installed on a 4Gb flash card. Love it. I've got some time invested in this installation so I'm asking the experts what I can do to prevent having to burn another copy!


Nice to hear you like it. 

> 
Two days ago, when booting from Flash copy, the 'normal' user ('Ubuntu') signed in. On this installation, I boot from the flash onto a HP Pavilion Slimline and only have two (2) users; Ubuntu and myself. No biggie, always has worked fine. But on this day, some weird 'Gnome Keyring' message came up...I honestly think the culprit was a Gnome Program (Gnome Do) that I installed the previous day. Now I don't know a Gnome Keyring from a spoon, but somehow I got out of the message (mutliple 'escape' key hits, and finally had to just power down the system) but in doing so, something must've gotten way corrupted.


When you first time use wireless nic, it will ask you to put a Gnome Keyring password. How did you power down? Pressed powerbutton ~10secs or graceful shutdown with shutdown command?

> 
On next boot, all appeared fine, all programs worked, EXCEPT: Package installer wouldn't work, Ubuntu software center wouldn't work and the Archive Manager wouldn't work. Hmmm.....must've whacked something. Went into Terminal and was going to SUDO something when I discovered, my \etc\sudoers (or something like that file) was MAJOR messed up. Line errors everywhere. In doing a 'More' of the file, it's all graphic characters. Maybe this file is causing my other problems, but I know I've got to get SUDO and/or SU working again and here's my problem:

I wanted to install / write a new \etc\sudoers file....I tried to boot into Recovery mode (quite the journey unto itself!) and I got a Terminal window. But even in Recovery mode, issuing a 'sudo' command results in the same errors that I got in normal mode.
 
So, my dilmena is I know my \etc\sudoers file is whacked. Everything else, except the previously mentioned programs work fine. But I absolutely do NOT know how to get this file back, because even recovery mode won't work. I tried to use a LIVECD version on a machine, but when I plug in the FLASH card, it doesn't resemble the file structure that I see on the FLASH when it's the boot device. 


Well, first of all, in Windows you have C:**\**, in *nix systems we have **/**. Like /etc, /usr/local/bin, /home/ubuntu/ and so on... mystical backwards people they are at the Redmond ;)

Can you explain more about the file structure? As you know, when the flash card is boot device, it will be /, when you insert it, it will be /media/Flashcardsname/

So you still find the same files from it, but sudoers file is located in /media/Flashcardsname/etc/sudoers

> 
I know there's gotta be an easier solution than just redoing this flash; I've got a ton of time invested in nVidea drivers and Broadcom wireless and just don't want to start over. Plus I think I may learn something, besides don't EVER, EVER hard boot Ubuntu without safely shutting down....gotta say, Windows sure is well behaved there!
 
Can any experts help me with this one?
 
Many thanks in advance!
 
PH

Well, you could paste us your sudoers -file if possible. So that we could examine it. Hard to help without really knowing the issue.

I would do the reinstall, with my style: Boot LiveCD, wait it to load desktop, insert flash stick/card and start installer, and install it to the flashmedia. I don't like to fool around with those LiveCD-thingies and persistence modes, I want my USB pendrive to act like a real installation on harddrive.

But back to this case, here's my /etc/sudoers:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

So, you can now edit that file with your live media.
Hope it works.

Ps. now when you've done all that NVidia & Broadcom stuff once, it's atleast twice faster to do it second time ;D

---

### Post by bioterror on 2010-11-03
Damn, I was slow! :cry:

---

### Post by CharlesA on 2010-11-03
You need to change yer password in the GUI for the keyring password to be in sync with yer user password.

---

### Post by pruitthall on 2010-11-03
Thanks all for the great help.  I think the most valuable things I've learned are:
 
>Keep Gnome keyrings in sync with my user password
>Shut down gracefully
>What the file structure looks like when I'm booted into a LiveCD.
 
I'm going to try the fixes tonight when I get home.  Many thanks for everyone's help on this.

---

### Post by Zzl1xndd on 2010-11-03
> **pruitthall said:**
> 
>Shut down gracefully
>

This is good advise on any OS. Normally a cold boot wont cause issues, but I have seen Mac, Linux and Windows all go bad from it.

---

### Post by CharlesA on 2010-11-03
> **tweakedenigma said:**
> This is good advise on any OS. Normally a cold boot wont cause issues, but I have seen Mac, Linux and Windows all go bad from it.

Indeed. Just powering a PC off can lead to file corruption.

---

