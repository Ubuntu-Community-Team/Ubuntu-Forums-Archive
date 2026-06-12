---
title: "backup strategy"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by mjjohanson on 2010-12-30
After 22 years as a usoft user I have stepped up to linux. I wish to emulate a backup strategy developed for my old systems and am seeking advice on how to do it. 

On the old system I have two drives each with two primary partitions. The first partition on the first drive has the boot- and usr-like files. The second partition on the second drive has var- and home-like files. Every night any file that is changed or added during the day gets copied to the parallel partition on the other drive. The objective is to save the latest copy of current files as well as one copy of old files that have been replaced. On the old system when the boot drive failed (happened twice) I simply changed a jumper and booted off of the other drive until I installed a replacement drive and copied stuff over. I could also go back to yesterday's version of a file if I really trashed something up. Third, I would have one copy of old data files as a near-line archive while keeping the current directory cleaned out (I also saved the archive-like folders to a third drive every so often). And, fourth, it provided a modest level of load balancing between drives.

I just need a bit of help to make the shift from the drive-oriented nature of DOS to the file-system-oriented nature of Linux. 
-How do I create parallel file systems on two drives, one primary, one secondary with the ability to swap roles?
-How do I make it possible to boot from one file system normally and then the other after a drive crash? (I would change the boot drive in the BIOS rather than jumpers.)
-What is the best utility to duplicate the functions of xcopy in DOS?

All of this is not RAID, mirroring, archiving or synchronizing. I have considered and applied all of these at one time or another and nothing has worked as well as what I have. (For the last month I have been running a pilot system with maverick so I am a bit familiar with system internals.) Thank you, in advance, for your help.

---

### Post by mjjohanson on 2011-01-03
Is this impossible under Linux?

Am I in the wrong forum?

---

### Post by nothingspecial on 2011-01-03
I`m not sure if this will help because I do it a completely different way.

I have a "home" computer - a very old  cheap thing that holds all the data.

I have a laptop and a pc.
 
They both mount the data from the "home" computer to their /home directories remotely over lan. If one fails, the other can be used in the exact same way. Using sshfs


[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
_[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)_
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

 to mount the data, whatever changes are made, to the data from either the pc or the laptop, are made to the drive on the "home"  computer (if you see what I mean).

Then I use rsync

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

to back the data up to another computer (very old and cheap also), on a completely different circuit (if the town`s electricity went this would not be any use) but on the lan.

Periodically, I back the real inportant stuff to removeable media, which I obviously remove. And of course, the daily modifications to my plans for world domination go on 2 different removable sticks.

I`m not talking about an organisation here. At the moment, I work at home, on my own. And I include work documents and wedding photos in this scenario. However, if I lost the important stuff I would be just as screwed as a large company (more if I lost the wedding photos).

I have also discussed setting up a ssh connection with my brother-in-law to copy each others stuff remotely to each others systems (protection from fires, explosions etc)  although we haven`t implemented it. He is also a linux user, works at home, and is married to my wife's sister (our potential problems are the same).

Anyway, I digress, there are loads of ways of accomplishing your ends, I just don`t know how to do it your way.

Cheers :p

---

