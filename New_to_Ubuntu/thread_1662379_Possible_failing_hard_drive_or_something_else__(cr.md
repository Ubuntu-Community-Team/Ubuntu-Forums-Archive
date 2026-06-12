---
title: "Possible failing hard drive or something else ? (crash + does not boot afterwards)"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Mike- on 2011-01-08
Right now Ubuntu (10.10, 32 bit) won't start: [http://dl.dropbox.com/u/10057323/DSCN0364.png](http://dl.dropbox.com/u/10057323/DSCN0364.png)

I'm writing this using Ubuntu on a flash drive (like a live CD).


Some information:

Two  moths ago my motherboard died and had to be replaced (old PC from  2006). I used windows XP for a few weeks after that until it crashed and  won't boot afterwards (when starting it after trying to load for a few  minutes it would bluescreen complaining about a missing dll and reboot -  and crash again and so on). 

I decided it wasn't worth the  trouble to fix it and installed Ubuntu on another partition (20 GB) on  the same HDD. I set it up as a dual boot and left the 30 GB win XP  partition intact. 

Everything was great again for a few weeks until:
-  a few days ago Ubuntu froze completely. Didn't respond to the keyboard  or mouse.  I left it a few minutes, maybe it would recover - nope. I  forced a shutdown (holding the power button). On reboot it said it  needed to run checkdisk - I left it do its thing. All was alright after  that except for OpenOffice Word complaining that it lots its config  file. 

- a day after that - same freeze while copying some files.  Forced a shutdown again as there was nothing I could do.  After that it  wouldn't boot - kept sending me into BusyBox and saying it can mount  some directories (see the picture at the beginning of the post). On  boot,  choosing another kernel, or Recovery mode didn't make any  difference.

I used Ubuntu Live CD - initially I couldn't mount  the ext4 partion. I used the check feature from GParted (here's the log:  [http://dl.dropbox.com/u/10057323/gparted_details.htm](http://dl.dropbox.com/u/10057323/gparted_details.htm) Note: I edited  some filenames for privacy reasons - replaced them with EDITED). After  that I mounted all the partitions on that HDD successfully in Nautilus  and backed up a few files on another HDD. 
After that Ubuntu turned on just fine. The only things I lost this time was Transmission's settings.

Yesterday  - weird crash - the menu and taskbar disappeared and the few remaining  programs (Xchat and Rhythmbox) looked like they were running on windows  2000 (low graphics mode?).  I activated the shut down (used the shutdown  button on my keyboard - Ubuntu asked to confirm - Yes). It looked like a  normal shut-down - then l it got stuck. I forced the shutdown  again. 

It turned on after that and ran OK for a few hours and  then all of the sudden Rhythmbox stopped playing. It seems that none of  the files would play. Note: the files were on another HDD. I tried to  open a picture (jpg)  on the desktop - it gave me an error that there's  no program installed to handle it. Same with a text file. I couldn't open **any**  programs from the menu - it said that the launcher pointed to an  invalid location. Chrome wouldn't open any new sites though the tabs  already open were fine.  By now I noticed that many buttons on the  interface lost their graphics. Desktop effects worked fine though. 
I  checked the LED on the PC case that indicates HDD activity - as  expected - off - and nothing I did (trying to open files or run  programs) made any difference. It was as if all the the running programs  still loaded in RAM ran somewhat OK but the HDD was off-limits. I triggered a shutdown from Ubuntu - looked like it was shutting down - got  stuck - so I forced it.

Next Ubuntu won't turn on - see the picture at the beginning of the post. 

My question: what's causing this? Is the HDD (3 years old) holding the OS dying or it's something else?

---

### Post by cariboo on 2011-01-08
Go to your hard drive manufacturers web site and download and use the diagnostic tools to check to see if your hard drive is dying.

---

