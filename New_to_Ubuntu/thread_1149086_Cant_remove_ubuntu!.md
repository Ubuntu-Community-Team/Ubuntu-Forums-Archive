---
title: "Cant remove ubuntu!"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Fallzak on 2009-05-04
Hey i want to uninstall and reinstall Ubuntu but I cant get in uninstalled....... Help?

---

### Post by fdrake on 2009-05-04
[link]("http://ubuntuforums.org/showthread.php?t=1137509")

---

### Post by Svensk023 on 2009-05-04
Just re-install over it. It will get deleted when it reformats your partitions.

---

### Post by RedSingularity on 2009-05-04
You can always boot the live CD and use gparted (partition editor)

---

### Post by Fallzak on 2009-05-04
> **Shadow121 said:**
> You can always boot the live CD and use gparted (partition editor)

hmmmmm.... sounds good!!! how do i do that?

---

### Post by RedSingularity on 2009-05-04
Just put the ubuntu CD in the drive and reboot the computer.  Then once your in type in terminal "sudo gparted"  That will give you the editor.

---

### Post by Fallzak on 2009-05-05
and thats for 9.04 right?

---

### Post by waspbr on 2009-05-05
the version doesn't really matter, tho I would probably stick to a 9.04 liveCD since the partition editor in that version should be newer.

also it doesn't matter what version of ubuntu u have installed.

---

### Post by Fallzak on 2009-05-05
ok so i got the partition deleted.... but grub is still there..... And it gives me error 22
 
I cant get into windows either...

---

### Post by Fallzak on 2009-05-05
and yes i know i'm an idiot this is my first time using ubuntu.....

---

### Post by arapa on 2009-05-05
Are you planning to reinstall Ubuntu? If so, the installation should fix grub.

If not you'll have to re-write your MBR using the Windows XP cd. 

Let us know which.

---

### Post by Fallzak on 2009-05-05
yes i'm going to install it for today.....
 
I would like to get rid of it though its giving me problems....

---

### Post by arapa on 2009-05-05
If you want to remove ubuntu and only have XP:

Boot off of your Windows XP cd and enter the "Recovery Console".

When you get a command prompt type:

fixmbr

(if the partition is FAT format type fixboot and then fixmbr)

---

### Post by Fallzak on 2009-05-05
will this work with vista?

---

### Post by raymondh on 2009-05-05
> **Fallzak said:**
> will this work with vista?

from the vista disk, click yes for language then system repair and then command prompt.  Type 

bootrec.exe/FixMbr

Reboot.

---

### Post by jimingkui on 2009-05-06
> **Svensk023 said:**
> Just re-install over it. It will get deleted when it reformats your partitions.

I have installed ubuntu 9.04 and removed 8.10 in this way

---

### Post by Fallzak on 2009-05-06
ok........ So that worked but i dont have the space back on my Hard Drive..........

the Bootrec.exe/fixmbr

---

### Post by arapa on 2009-05-06
boot off the Ubuntu live CD, open gparted, delete the partition where you had ubuntu installed, resize the windows partition to use the space.

---

### Post by johnhdsi on 2009-05-06
I have 8.04 installed and I want to install 9.04 over the top of it to see if it fixes some wireless problems I have had. Here's my main problem. The box I'm doing this to is dual boot 8.04 and win XP, currently I cannot access the internet while in 8.04 as my wireless does not work so I can't just boot and do the upgrade. If I do the 9.04 live cd, can I upgrade install from it? I'm a newbie at this stuff to so please be gentle, it's my work computer so I don't want to screw anything up on it by doing something dumb. Thanks for the help.

John

---

### Post by arapa on 2009-05-06
> If I do the 9.04 live cd, can I upgrade install from it? I'm a newbie at this stuff to so please be gentle, it's my work computer so I don't want to screw anything up on it by doing something dumb. 

It's best not to skip versions when upgrading. I strongly suggest doing a clean install rather than a trying to go from 8.04 - > 9.04. 

If you need more help - open a new thread. There are ways to work around a lot of wireless problems if the still exist in 9.04.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by jakupl on 2009-05-06
> **johnhdsi said:**
> I have 8.04 installed and I want to install 9.04 over the top of it to see if it fixes some wireless problems I have had. Here's my main problem. The box I'm doing this to is dual boot 8.04 and win XP, currently I cannot access the internet while in 8.04 as my wireless does not work so I can't just boot and do the upgrade. If I do the 9.04 live cd, can I upgrade install from it? I'm a newbie at this stuff to so please be gentle, it's my work computer so I don't want to screw anything up on it by doing something dumb. Thanks for the help.

John
BACKUP ALL THE IMPORTANT STUFF and do a complete reinstall. When you are installing, choose the manual option in the partitioning phase. There you can tell it to format the existing ubuntu partition using ext3 and under the "use as", choose "/".

But I recommend that you make your own thread if you are uncertain, in stead of hijacking another thread.

---

### Post by raymondh on 2009-05-06
John...

You've got to go 8.10 first before 9.04 IF YOU WANT TO DO A NETWORK UPGRADE.  Otherwise, a clean install is needed. 

If you have the liveCD for 9.04 ... try it out and see if wireless is working.

If you do install, BACK UP first and then do a manual install on the existing 8.04 partition.

Let us know your decsions and we can go from there ...

---

### Post by johnhdsi on 2009-05-07
> **jakupl said:**
> BACKUP ALL THE IMPORTANT STUFF and do a complete reinstall. When you are installing, choose the manual option in the partitioning phase. There you can tell it to format the existing ubuntu partition using ext3 and under the "use as", choose "/".

But I recommend that you make your own thread if you are uncertain, in stead of hijacking another thread.

I apologize for the "Hijacking" move, I was surfing thru the forums looking for an answer and I thought it was best to ask in a thread that was along the same lines as what I was looking for. I will make sure to not do that again. As far as the upgrade, I will use the live cd and re-partition the drive as suggested and load 9.04 and see what happens. Thank you all for the info I appreciate it.

John

---

### Post by Dex73 on 2009-05-07
Ya, anytime you remove Ubuntu but not GRUB, GRUB freaks out on you.

---

### Post by jacksinn on 2009-05-07
If you're new to Ubuntu and are still married to Windows, I'd recommend restoring your MBR and doing a WUBI install of Ubuntu. Then you don't really have to worry about partitioning, resetting boot records, etc and when you're finally ready to move over just throw on a fresh install (after backup) to your machine.

---

