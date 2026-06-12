---
title: "how to remove ubuntu from a dual boot with xp?"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by zereshk on 2010-07-26
Hi, I know there are several ways to do so in case that I have windows live cd, but have a pecular problem here:

I bought a second hand laptop with windows xp on it (without any windows cd). So, I installed ubuntu 10.04 as my usual first step to start touching the box. Now, I am going to sell the laptop to someone who expects to receive a windows os, and I can not change his mind. So how can I remove ubuntu from the dual boot machine, while I have only ubuntu live cd/usb? 

If total removal is not possible in my situation  then , as the last resort, how can I shrink the ubuntu partition size to the minimum?

---

### Post by hhh on 2010-07-26
You can restore the Windows master boot record with Super Grub Disc...
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
...and then delete the Ubuntu partition(s) and expand the Windows partition with Gparted from your Ubuntu Live CD.

---

### Post by jtarin on 2010-07-26
Are you booting both OS's with Grub? You will need to accomplish the fix with FIXBOOT and FIXMBR, then BOOTCFG. 
It only worked if I was in the root directory for the instance that I wanted to fix: 

example:
Boot with XP cd if you don't have Recovery Console installed. 
Selecting repair function when cd boots.
Choose your installation you want to repair 
C:\WINDOWS
then enter...line by line 
```
CD .. 
FIXBOOT C: 
FIXMBR 
BOOTCFG /rebuild 
```

after all that I was able to select the new entry from the selection menu. You will notice that you end up with a second instance of "Microsoft Windows XP Professional" in the NTLoader when you start up. But that will be quickly removed when you edit the boot.ini file in Windows to remove it.

---

### Post by zereshk on 2010-07-26
> **jtarin said:**
> Are you booting both OS's with Grub? You will need to accomplish the fix with FIXBOOT and FIXMBR, then BOOTCFG. 
It only worked if I was in the root directory for the instance that I wanted to fix: 

example:
Boot with XP cd if you don't have Recovery Console installed. 


Thanks, but my problem is that I have no XP cd.

---

### Post by zereshk on 2010-07-26
> **hhh said:**
> You can restore the Windows master boot record with Super Grub Disc...
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
...and then delete the Ubuntu partition(s) and expand the Windows partition with Gparted from your Ubuntu Live CD.

How can I do this?[ the wiki page]("http://www.supergrubdisk.org/wiki/Main_Page") is under construction.

---

### Post by louieb on 2010-07-26
The 1st thing you want to do so replace the code in the MBR that loads GRUB with code that loads the XP boot loader. Lots of ways to do just that.  
[IDBS Remove Replace Uninstall Grub]("http://members.iinet.net.au/%7Eherman546/p18.html") 

Once thats done and it boots straight to windows - just use any partition tool you care to use.  Whatever you want - delete the the Linux partitions and grow the windows partition to fill the space.  

or the safest is don't delete the Linux partition(s)  - just format them to NTFS - that way XP can can use the space to store more data.

---

### Post by egalvan on 2010-07-26
It worked when I tried it...

Try going direct...

[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)


and here is the info (copied from that page) in case you still can't access...


[B]  Advanced solution

Sometimes the partition where Windows is found might not be the first one. If you want to recover a non-standard Windows installation (like a laptop one).you can choose:

   1. Choose Language & HELP  :- ))
   2. English Super Grub Disk
   3. Windows
   4. Windows (Advanced)
   5. Fix Boot of Windows
   6. Select the partition where Windows is found. 

[/B]



Another note... MAKE SURE that you can access gparted from the LiveCD before you start anything...

Me, I always use PartedMagic LiveCD to do any partitioning/formatting..

[http://partedmagic.com/](http://partedmagic.com/)

(I use this in my Linux consultation business, so I have a $2/month subscription.. see my signature)
The authors actually read feed-back/problems from users.. it's a great mini-distro))

---

### Post by uRock on 2010-07-26
> **presence1960 said:**
> you can repair the mbr to a windows mbr from  ubuntu or the ubuntu live cd. Install lilo by running in terminal  ```
sudo apt-get install lilo
```ignore the warning and next run in  terminal ```
sudo lilo -m /dev/sdx mbr
```where is sdx is your  disk/device, i.e. Sda, sdb,sdc, etc:d

---

### Post by hhh on 2010-07-26
> **zereshk said:**
> How can I do this?[ the wiki page]("http://www.supergrubdisk.org/wiki/Main_Page") is under construction.

egalvan's link is right, but that page's screen shots are a bit confusing. Each screen has stuff to read that requires you to "Press any key to continue". When you get to "English Super Grub Disc" choose "Windows", then "Fix boot of Windows", then choose the drive Windows is on.

I'm going to fire up my copy now and make sure my instructions are right... I'll edit this post when I'm done.

-edit- Yeah, they're close enough, the disc is pretty self-explanatory.. I didn't run it through all the way obviously, I like my dual boot. The only other thing I remember that was slightly confusing was when you get the message "Success!", "Press a Key", it doesn't take you to an exit menu. Just scroll up to "Back one menu" until you get to the screen with options to exit.

---

### Post by jtarin on 2010-07-26
> **zereshk said:**
> Thanks, but my problem is that I have no XP cd.
This is a download of an .iso file of just the Recovery Console for XP.
Burn to CD with Nero or other 'disc image' capable tool and boot.
It looks just like the start of a normal XP CD, but will only offer the Recovery Console by pressing "R."

All normal Recovery Console procedures can be run from this utility.
[Direct download]("http://www.thecomputerparamedic.com/files/rc.iso"):

---

