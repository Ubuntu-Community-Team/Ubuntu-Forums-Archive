---
title: "&quot;An error occured while mountin Swap&quot;"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Odaym on 2011-01-14
Whenever i boot up, since i last **modified with my /etc/fstab file**, i get an Error at the splash screen saying "could not mount swap, S to skip, M to manually recover."
 
i created this thread because i wasnt getting any replies on the other thread, i thought it was probably because it was labeled SOLVED, so i started this one, excuse any misconception about this topic..
 
"sudo blkid" produces :
> /dev/sda1: UUID="2955b4dc-24e6-4da1-b5b4-cc7e5c25944" TYPE="ext4"
/dev/sda5: UUID="........." TYPE="swap"
 
"cat /etc/fstab" produces :
> /.
.
.
.
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda1 / ext4 errors=remount-ro 0 0
 
#swap was on /dev/sda5 during installation
UUID=9d3ad268-d68c-4308-845f-30cc6ada2171
none swap sw 0 0
 
the repeated dots after one another are commends, talking about how to use blkid
 
 
when i press M to manually recover, i go to the terminal, and when i try to edit my /etc/fstab (nano /etc/fstab) while i am already logged in as root, i get Cannot write changes to disk, Read-only filesystem..??
 
 
thank you very much in advance

---

### Post by Odaym on 2011-01-14
the only restriction i have right now is that i cannot edit /etc/fstab because of "Read-only filesystem"...how is my filesystem read-only? I AM ROOT! please help.

---

### Post by Odaym on 2011-01-14
also, when i run "fsck /dev/sda1" i get :
 
> 
fsck from util-linux-ng 2.17.2
WARNING: bad format on line 11 of /etc/fstab
e2fsck 1.41.11 (14-March-2010)
/dev/sda1 : clean, 263674/18989056 files, etc...blocks

 
and when i run "fsck /dev/sda5" which is the swap, i get : 
 
> fsck from util-linux-ng 2.17.2
WARNING: bad format on line 11 of /etc/fstab
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5
 
the 11th line of /etc/fstab is :
> UUID=9d3ad268-d68c-4308-845f-30cc6ada2171
and under it
none           swap            sw            0               0

---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> the only restriction i have right now is that i cannot edit /etc/fstab because of "Read-only filesystem"...how is my filesystem read-only? I AM ROOT! please help.
The filesystem could be mounted read-only during boot-up due to errors.
You should not be able to write on a read-only mounted filesystem even as root.
You could boot in recovery mode instead, (single user mode) and try to change the file there.

---

### Post by Odaym on 2011-01-14
but how do i do that? i dont have a menu that offers me this single user mode..

---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> but how do i do that? i dont have a menu that offers me this single user mode..
Could you see the grub during boot-up?
If yes you could edit the entries (by e command as I remember; it is written below grub screen).
Simply add **single** to the end of linux line. It will then be like:
```
linux    /vmlinuz-2.6.35-22-generic root=....... ro single
```
and then boot that entry.

---

### Post by Odaym on 2011-01-14
I cannot see grub loading, i boot up and i only get the Ubuntu splash screen..

---

### Post by Verbeck on 2011-01-14
> **Odaym said:**
> I cannot see grub loading, i boot up and i only get the Ubuntu splash screen..
try holding down the shift key while booting up

---

### Post by Odaym on 2011-01-14
i got to see grub loading, but pressing 'e' did not help to stop or do anything. what i got was the grub menu, and i entered (recovery mode), again to see "Warning bad format on line 11 in /etc/fstab, mount: mount point does not exist, mountall: mount [467] terminated with status 32
mountall: filesystem could not be mounted:
/dev/sda1: clean, 231233/198989056 files, etc...blocks"

---

### Post by Odaym on 2011-01-14
when i pressed f8 while the above message was being display, i press M again for manual recovery, and i tried to configure fstab again, and same thing, read-only filesystem

---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> when i pressed f8 while the above message was being display, i press M again for manual recovery, and i tried to configure fstab again, and same thing, read-only filesystem
OK, I think the easiest way for turning around this issue is to use a LiveCD.

Boot from a LiveCD, then mount your root partition (you could mount it by clicking on it from *Places* menu) and then change files there.
You could also do it from a terminal in LiveCD by:
```

sudo su
mount <REPLACE-THIS-WITH-PATH-TO-ROOT-DEV; like /dev/sda1 maybe> /mnt
gedit /mnt/etc/fstab

```

---

### Post by Odaym on 2011-01-14
I am in the LiveCD right now, and i mounted my filesystem, but i have my home folder encrypted, i access it and i get two files, one called README, that reads :

> THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

and a second file called "Access Your Private Data" which when clicked on says :
> Untrusted Application Launcher, The application launcher  "Access-Your-Private-Data.desktop" has not been marked as trusted,  etc....

and when i try the command ecryptfs-mount-private, i get ERROR: Encrypted private directory is not setup properly..

what am i to do? any help at this stage?

---

### Post by Odaym on 2011-01-14
> **sudo blkid** produces 
/dev/sda1: UUID="2955b4dc-24e6-4da1-b5b4-cc7e5c2f5944" TYPE="ext4" 
/dev/sda5: UUID="9d3ad268-d68c-4308-845f-30cc6ada2171" TYPE="swap" 


now i can access my fstab file and edit it totally, and it reads as follows :

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d3ad268-d68c-4308-845f-30cc6ada2171 
none            swap    sw              0       0

before, when executing **"mount -a"** or **"fsck /dev/sda1"** or **"fsck /dev/sda5"** i used to get [B]: 
"Bad format on line 11 of /etc/fstab"[/B] 
which is this line
**UUID=9d3ad268-d68c-4308-845f-30cc6ada2171  **<-- the 11th line of /etc/fstab

---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> I am in the LiveCD right now, and i mounted my filesystem, but i have my home folder encrypted...........................
what am i to do? any help at this stage?
You only need to correct the /etc/fstab file. So probably you do not need to open your encrypted home partition.
Have you separated root and home partitions?
Could you post result of
```
sudo fdisk -l
```
from LiveCD which shows us your partition table (at the end of above command is lower case L not 1; meaning list)?

---

### Post by Odaym on 2011-01-14
**fdisk -l**

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b434

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37810   303700992   83  Linux
/dev/sda2           37810       38914     8867841    5  Extended
/dev/sda5           37810       38914     8867840   82  Linux swap / Solaris


---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> **fdisk -l**
Two works:
**First.** open your fstab file and double check that you have all entry descriptions in their own line. As I could see from your post, the swap entry description is divided in two lines.
Your file should be like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sda5 during installation
UUID=9d3ad268-d68c-4308-845f-30cc6ada2171    none    swap    sw    0    0 			 		

```
**Second.** Post result of
```
sudo blkid /dev/sda5
```
It must be identical with the value in front of UUID in your swap entry description line.

---

### Post by Odaym on 2011-01-14
output of [B]sudo blkid /dev/sda5

[/B]> /dev/sda5: UUID="9d3ad268-d68c-4308-845f-30cc6ada2171" TYPE="swap"value infront of UUID in /etc/fstab file 
> 9d3ad268-d68c-4308-845f-30cc6ada2171they **are** identical, and i fixed the values in fstab on one row, the line now reads 
> 
# swap was on /dev/sda5 during installation
UUID=9d3ad268-d68c-4308-845f-30cc6ada2171 none  swap  sw   0      0


---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> and i fixed them on one row
Good, probably problem was from that line.
Now you could check it by rebooting.
You could also use following command before reboot:
```

sudo mkswap /dev/sda5

```
to be sure that swap partition (/dev/sda5) is OK itself.

---

### Post by Odaym on 2011-01-14
**sudo mkswap /dev/sda5** output was 

> /dev/sda5: Device or resource busy

---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> **sudo mkswap /dev/sda5** output was
The swap partition is in use by LiveCD. You could disable it before **mkswap** by
```
sudo swapoff -a
```

---

### Post by Odaym on 2011-01-14
the swapoff worked, and the mkswap /dev/sda5 produces this 

Setting up swapspace version 1, size = 8867836 KiB
no label, UUID=7f7a0c31-f8d8-49d0-97d5-cc728a6fc268

that UUID doesn't match the original one, but then again, maybe its allocating the id again..or something?

---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> the swapoff worked, and the mkswap /dev/sda5 produces this 

Setting up swapspace version 1, size = 8867836 KiB
no label, UUID=7f7a0c31-f8d8-49d0-97d5-cc728a6fc268

that UUID doesn't match the original one, but then again, **maybe its allocating the id again**..or something?
So replace the new UUID in the fstab file.
It is also good to check with **blkid** to see UUID is still constant!

---

### Post by Odaym on 2011-01-14
it works, thank you :) life saver!

---

### Post by WthIteh on 2011-01-14
> **Odaym said:**
> it works, thank you :) life saver!
Your welcome ;)
You could mark thread as *solved* from *Thread Tools* red link in top of the page.

Also there is one more precautionary action:
Your root partition entry is like:
```
/dev/sda1    /    ext4    errors=remount-ro    0    1
```
but /dev/sda1 could be changed at boot time! So it is good to replace
it with a UUID entry. Find its UUID by
```
sudo blkid /dev/sda1
```
and then replace that line in fstab with something like:
```
UUID=THE-UUID-OF-SDA1-DEVICE    /    ext4    errors=remount-ro    0    1
```

---

### Post by Odaym on 2011-01-14
it works, thank you :) life saver!

---

