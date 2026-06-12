---
title: "Accidental partial system recovery on XP Media Center 2005 try to fix with live cd"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Argon27 on 2009-01-17
I'm really sorry if I am bumping an old topic but I have searched and searched and I just can't seem to find a solution.  My computer runs Windows XP Media Center 2005.  A few weeks ago I tried to install Windowsblinds, but little did I know (my stupid virus scanner didn't pick it up, time to update to AVG) it was infected and completely rendered my system useless.  I tried to use the system recover option to set the computer back to an earlier date.  It gave the option to choose that or system restore to set it back to factory defaults.  I chose the first option, it rebooted, opened the **restore**menu, and automatically started formatting my drive.  It surprised me and ran for about three seconds before I unplugged it, not the smartest thing to do I know but I panicked, when I turned it on again it would just show a blank screen.  I then hoped to boot up Ubuntu (Hardy Heron)to see if I could access my hard drive and back up my critical files.  But all i see is gibberish and locked files.  I've tried using ms-sys to rewrite the MBR but it can't find the package for it, and now I'm just tired of the whole thing.  Please help me.  Thank you.

P.S. I have really bad habits like not creating boot disks and backing up my data but I'll change, I promise!!!!  BTW Fry's didn't give me an OS disk with the computer.  Also I'm only a newbie to Ubuntu.  I have PLENTY of experience with Windows.

---

### Post by blueridgedog on 2009-01-18
It sounds to me like the master file table for the NTFS drive is missing due to the unplugging...

Perhaps another forum participant will have an ubuntu based solution, but my search only reveals windows based tools (some shareware) to do the job:

[http://www.google.com/search?q=+restore+master+file+table+NTFS&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=+restore+master+file+table+NTFS&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by cariboo on 2009-01-18
I would suggest, you use the the set back to factory standard, as you are probably not going to be able to do any thing unless you do. If you can mount the hard drive using the LiveCD, backup your important files, then set everything back to factory standards. If you got a virus from Windowsblinds, I would be complaining to the manufacturer.

Jim

---

