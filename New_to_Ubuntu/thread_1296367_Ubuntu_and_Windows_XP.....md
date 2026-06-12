---
title: "Ubuntu and Windows XP...."
date: 2009-10-20
forum: New to Ubuntu
---

### Post by GSI on 2009-10-20
A month ago I installed windows XP and when I rebooted fot first start of XP there was no GRUB loader and I cant load ubuntu.

Is there any way to reinstall grub WITHOUT reinstalling windows XP or ubuntu ?

---

### Post by martrn on 2009-10-20
> **GSI said:**
> Is there any way to reinstall grub WITHOUT reinstalling windows XP or ubuntu ?

Yes, if you have your copy of the ubuntu cd from which you installed ubuntu.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Its different way to reinstall grub depending on your dual-boot setup.  But ther is always a way to reinstall grub without reinstalling windowze or ubuntu.

I am supprised at the number of people that re-install windowze or ubuntu after some problem such as bad/missing master boot record.

---

### Post by LewRockwell on 2009-10-20
with many OEM versions of Windows, re-installing reformats the complete drive and writes over previous data

you'll need to determine whether your other partitions/data even still exist

.

---

### Post by GSI on 2009-10-20
Ok,thank you I will try this tomorow when I get back from school :)

---

### Post by GSI on 2009-11-08
Ok,I managed to recover grub boot loader but I can't boot windows XP Now.I dont know how to add Windows into the grub boot list

HELP!

---

### Post by Bucky Ball on 2009-11-08
First up, open a terminal and paste this in:

```
 sudo blkid
```You should be able to work out what partition your Windows install is on from that. Remember the sda* for that partition. What is it?

---

### Post by GSI on 2009-11-08
Heres the output: 

ico@GSiPoWeR:~$  sudo blkid
[sudo] password for ico: 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: TYPE="swap" UUID="d8873088-ae5b-4103-8842-102bb25c8c32" 
/dev/sda5: UUID="54CDEE3125F8BFA4" LABEL="DATA" TYPE="ntfs" 
/dev/sda2: UUID="ea475b46-ac5c-4f74-8d09-62ca879da7a7" TYPE="ext3" 
/dev/sda4: UUID="50308A8E308A7AAC" TYPE="ntfs"

---

### Post by Bucky Ball on 2009-11-08
Okay, that looks kinda weird. Did you install Windows last? It looks like it might be on sda4 as sda5 has LABEL=DATA. Also, there is only one EXT3 partition. You have your / (root) and /home directories on the same partition? Ubuntu is all on the one partition?

Anyhow, give this a go:

1/ In a terminal copy and paste"

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```This makes a backup of your menu.lst file in case you screw something up. 

2/ Paste this in a terminal:

```
sudo nano /boot/grub/menu.lst
```3/ At the bottom of that file add this (or if you're feeling confident add it under the first Ubuntu kernel but make sure it is between kernels NOT halfway through a kernel's grub entry!):

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windoze (You can put what you like on this line)
root            (hd0,3)
savedefault
makeactive
chainloader     +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
```

sda4 = hd0,3.

4/ Reboot and let us know how you go. If you get an error message try to remember it. It should be a numbered code (Error 17 or something like it). 

This could work but you may need to map the partition as Windows generally likes to be on disk1, partition1 or it's not happy so you sometimes need to trick it into thinking that.

---

### Post by GSI on 2009-11-08
The result is an error message : 
'Error 15 File not found...'
Press any key to continue..

---

### Post by LewRockwell on 2009-11-08
> **GSI said:**
> Heres the output: 

ico@GSiPoWeR:~$  sudo blkid
[sudo] password for ico: 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: TYPE="swap" UUID="d8873088-ae5b-4103-8842-102bb25c8c32" 
/dev/sda5: UUID="54CDEE3125F8BFA4" LABEL="DATA" TYPE="ntfs" 
/dev/sda2: UUID="ea475b46-ac5c-4f74-8d09-62ca879da7a7" TYPE="ext3" 
/dev/sda4: UUID="50308A8E308A7AAC" TYPE="ntfs"

sda1 is a primary partition set as file system type swap

sda2 is a primary partition set as file system type ext3

sda3 is not shown so we must assume that it is an extended partition

so it would seem that sda4 and sda5 are logical partitions in the extended partition area

windows in the extended partition area is not recommended or encouraged

.

---

### Post by LewRockwell on 2009-11-08
secure your valuable data then reinstall/repartition as desired

we always leave a primary partition at the beginning of the drive especially for windows(even if we aren't installing it right then)

.

---

### Post by GSI on 2009-11-08
The windows partition is sda4 and its primary..

---

### Post by Bucky Ball on 2009-11-08
Change the entry I gave you for the menu.lst to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windoze (You can put what you like on this line)
root              (hd0,3)
map             (hd0,3) (hd0,0)
map             (hd0,0) (hd0,3)

savedefault
makeactive
chainloader     +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
```I don't see an extended partition there but the other post was right, not a good idea to put a Windows install in an extended partition and leaving a partition at the beginning of the disk a good idea (although this will not necessarily be allocated as (hd0,0) if the other partitions are installed with an OS first. It can't be hd0,0 if another partition already is. You would need to map it just the same.

> 15 : File not foundThis error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.       From this page:

[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

You don't have a major problem here and there is no reason whatever to reinstall at this stage. Your grub is entry is just pointing to the wrong partition. Try those changes to the Windows grub entry in menu.lst. It is a matter of getting the mapping right. I think that is right but I will check on my desktop which has a mapped Windows partition a little later. (I think that is the syntax though - it may need to be tweaked a little) :)

* You can also download the Super Grub Disk ISO, burn it and boot from the disk. Will probably fix your prob in a jiffy:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by GSI on 2009-11-09
Thank you,Bucky Ball that helped alot!

The problem is now SOLVED!

---

### Post by Bucky Ball on 2009-11-09
It worked? Great! I like it when a plan comes together. Happy Ubuntu-ing!

---

