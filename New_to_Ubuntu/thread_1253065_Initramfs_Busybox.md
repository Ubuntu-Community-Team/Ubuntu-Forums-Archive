---
title: "Initramfs Busybox"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by n1tr0u543 on 2009-08-29
i'm fairly new to ubuntu (hardy 8.04 with dual boot windows 2k P.E.) and im completely stumped on this. i have a compaq evo n400c and it was working fine up until yesterday when i started having some sound issues. i reset the sound preferences and had everything fine until my battery dies and i went to reboot and it began the BusyBox Initramfs prompt. i started windows ran chkdsk c:/f and chkdsk c:/r (which worked every other time this happened) and still got the busybox prompt. im an absolute newb as far as this as concerned so any detailed help would be greatly appreciated. 

thanks in advance!

---

### Post by SoftwareExplorer on 2009-08-29
Did you install ubuntu using wubi, or did you repartition your hard drive?

---

### Post by SoftwareExplorer on 2009-08-29
Welcome to the ubuntu forums by the way.  :P

---

### Post by n1tr0u543 on 2009-08-29
> **SoftwareExplorer said:**
> Did you install ubuntu using wubi, or did you repartition your hard drive?

i believe i repartioned it. its been a while. i installed it off of a cd. ive been reading that since i didnt properly shut it down, that may be why its not "mounting" right. i tried some of the suggestions like 
"mount -t ntfs-3g  /dev/sda1 /root -o force" 
and it just repeats what i type and returns to the 
(initramfs)_  prompt. 

thanks for the quick reply the welcome.

---

### Post by SoftwareExplorer on 2009-08-29
> **n1tr0u543 said:**
> i believe i repartioned it. its been a while. i installed it off of a cd. ive been reading that since i didnt properly shut it down, that may be why its not "mounting" right. i tried some of the suggestions like 
"mount -t ntfs-3g  /dev/sda1 /root -o force" 
and it just repeats what i type and returns to the 
(initramfs)_  prompt. 

thanks for the quick reply the welcome.
If it helps, wubi setup would have been run while running windows. Repartitioning would be if you rebooted and then ran the installer of Ubuntu's LiveCD Desktop. 
The suggestions you are quoting would be for a wubi install. Second, do you have a Ubuntu Live CD you can boot up with?

---

### Post by n1tr0u543 on 2009-08-29
> **SoftwareExplorer said:**
> If it helps, wubi setup would have been run while running windows. Repartitioning would be if you rebooted and then ran the installer of Ubuntu's LiveCD Desktop. 
The suggestions you are quoting would be for a wubi install. Second, do you have a Ubuntu Live CD you can boot up with?

i installed it off of a live cd, not through windows, i definitly recall that. i don't happen to have the cd anymore and i wont be able to get ahold of one for a while being that my desktop doesnt have a cd burner any longer. 

thanks for your help.

---

### Post by n1tr0u543 on 2009-08-29
is there a command i can give to remount the ubuntu partition? or something i can access through windows to disable the busybox maybe? ive looked through the forums all day and havent found anything relevant that i could comprehend to help me. 

thanks in advance.

---

### Post by MelDJ on 2009-08-29
i had the same problem the other day and i just went into recovery mode and ubuntu worked. maybe you could try doing that

---

### Post by SoftwareExplorer on 2009-08-30
You can't really disable busybox, its like the last resort when ubuntu can boot up. It gives you that prompt because the normal (bash) command line wasn't even loaded yet when whatever went wrong.

---

### Post by n1tr0u543 on 2009-08-30
i tried going into recovery mode with no luck. it took me back to the busybox prompt. i dont think it could be damage to the hard drive because im using windows on the same laptop right now. 

thanks for the help so far.

---

### Post by n1tr0u543 on 2009-08-30
*edit* i tried recovery mode once more and right before it goes to the initramfs prompt it says: 
"Alert! /host/ubuntu/disks/root.disk does not exist. Dropping to shell!"
any idea as to what may be causing this?

---

### Post by SoftwareExplorer on 2009-08-30
From the error it sounds like you did install with wubi. I'm haven't used windows 2000 for awhile, but go to the control panel. Open Administration tools and then computer management. Go to storage and then Disk Management (Local). It will show your hard disks and the partitions. See if there's an unknown partition on your hard drive. If so, you installed be repartitioning and without wubi.

If that's the case you could consider downloading the ubuntu CD image and using [Unetbootin]("http://unetbootin.sourceforge.net/") and make a live usb image. Then you could boot that to try to see what's wrong. It would probably also work with a wubi install, but I would need to read up on how do that.

---

### Post by rob.tozier on 2011-04-06
Hi everyone, I am also somewhat of a newbie.  I have successfully installed ubuntu onto a hard drive in one machine and then moved it over without any problems what so ever.  I have attempted it on a new server and ran into some problems.  Here is how it went, I am running 9.04 lts server and installed it using a desktop computer, I then swapped the hard drive into my dell poweredge 2800 server and when i goto boot it i get the following message.
 
*Gave up waiting for root device common problems*
 
*-Boot args (cat /proc/cmdline)*
*  -check rootdelay= (did the system wait long enough?)*
*  -check root= (did the system wait for the right device?)*
 
*-Missing Modules (cat /proc/modules; ls /dev)*
 
*ALERT! /dev/mapper/dell-root does not exist.  Dropping to shell!*
 
*BusyBox.......*
 
I have exhausted all efforts I can think of, any suggestions as to how to fix this issue?  I have tried to install the Ubuntu OS on this server while sitting at the server and it always blows up! That is why I attempted to install it on another machine and swap the drives.   Any assistance would be greatly appreciated! 
 
Thank You
 
Rob

---

### Post by SoftwareExplorer on 2011-04-06
@rob.tozier:
Can I suggest that you post this as a new thread? The only reason I saw your post is because I previously commented on this thread.

I don't know a lot about fixing these kind of errors, but it might help to find out what it says if you run ```
cat /proc/cmdline
```. 
Also, did you try using the server text-based installer on the server?

Anyway, I would recommend a new thread that mentions the answers to the questions I asked.

---

