---
title: "Manny, Many problems!!! Is it a virus?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by abybaddi on 2009-03-13
Recently I rebooted and I got pop-up of "do" asking to unlock the keyring. Whether I put the pass or deny, it again popped-up. This happened for a long time. I was neither able to take a screenshot nor able to open the menu by clicking/alt+F1. I just hit Esc many times and it went away. What was that?

And now when I've mounted the Ubuntu 8.10 i386 form archive mounter, I can't open it to view the contents. The nautilus just closes. Tried many a times same thing happens.

Can somebody help?:confused::(

---

### Post by gandaran on 2009-03-13
> **abybaddi said:**
> Recently I rebooted and I got pop-up of "do" asking to unlock the keyring. Whether I put the pass or deny, it again popped-up. This happened for a long time. I was neither able to take a screenshot nor able to open the menu by clicking/alt+F1. I just hit Esc many times and it went away. What was that?

And now when I've mounted the Ubuntu 8.10 i386 form archive mounter, I can't open it to view the contents. The nautilus just closes. Tried many a times same thing happens.

Can somebody help?:confused::(
a virus? definitely not, are you using wireless? have you added any application to start up/sessions that use the keyring? try deleting the keyring profile, applications » accessories » keys and encrypted keys » edit » preferences, delete/remove the default profile.

---

### Post by abybaddi on 2009-03-13
I just add nothing else but avant window navigator. And I'm not using wireless.

---

### Post by abybaddi on 2009-03-13
But still I can't browse the mounted drive.:(

---

### Post by taurus on 2009-03-13
What is the mount point of that drive (or partition)?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by abybaddi on 2009-03-13
> **taurus said:**
> What is the mount point of that drive (or partition)?


abybaddi009@abybaddi009-desktop:~$ sudo fdisk -l
[sudo] password for abybaddi009: 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aa72aa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9732    57689415    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101        8415    26627706    7  HPFS/NTFS
/dev/sda7            8416        8457      337333+  82  Linux swap / Solaris
/dev/sda8            8458        9732    10241406   83  Linux
abybaddi009@abybaddi009-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda8 :
UUID=0f92bbeb-f20c-410c-bc31-49176c787ab8	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=4CECEC0BECEBECE0	/media/19.5	ntfs-3g	defaults,locale=en_IN,force	00
#Entry for /dev/sda6 :
UUID=A44436444436198E	/media/25.3	ntfs-3g	defaults,locale=en_IN,force	00
#Entry for /dev/sda7 :
UUID=c641bb4e-57d6-41c6-83bf-7aacae5f0518	none	swap	sw	0	0


abybaddi009@abybaddi009-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             9.7G  8.0G  1.2G  88% /
tmpfs                 244M     0  244M   0% /lib/init/rw
varrun                244M  100K  244M   1% /var/run
varlock               244M     0  244M   0% /var/lock
udev                  244M  2.8M  241M   2% /dev
tmpfs                 244M  372K  243M   1% /dev/shm
lrm                   244M  2.0M  242M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda5              20G   13G  7.3G  63% /media/19.5
/dev/sda6              26G  9.6G   16G  38% /media/25.3
abybaddi009@abybaddi009-desktop:~$ 

What is this?

---

### Post by barbolanero on 2009-03-13
I'm not sure if this helps but... do you have adual boot?. Why?, I had a disk with several partitions and when I didn't close other OS properly then Ubuntu would start but it wouldn't mount the hard drives. Maybe it helos.

---

### Post by abybaddi on 2009-03-13
I dual boot Win Xp and Ubuntu. But use only Ubuntu. Xp is for my Brother.

---

### Post by taurus on 2009-03-13
Which one(s) do you have problems viewing/accessing?

```
ls -la /media/19.5
ls -la /media/25.3
```

p.s.  There should be a space between the **00** for the two ntfs entries in /etc/fstab.

---

### Post by stalkingwolf on 2009-03-13
try running the recovery mode and " fix broken packages"

---

### Post by LowSky on 2009-03-13
you could always log into windows and shut down correctly, it should fix the mounting issue.

Do is a program actually called Gnome Do, the keyring is a  normal thing, it pops up to save multiple password under one main passord, personally i hate it, but for some it serves a purpose.

---

### Post by abybaddi on 2009-03-13
> **taurus said:**
> Which one(s) do you have problems viewing/accessing?

```
ls -la /media/19.5
ls -la /media/25.3
```

p.s.  There should be a space between the **00** for the two ntfs entries in /etc/fstab.

I'm having problem accessing the CD which I mounted with Archive Mounter and I can access both the above drives without any problem.

---

### Post by abybaddi on 2009-03-13
> **stalkingwolf said:**
> try running the recovery mode and " fix broken packages"

I'll try this.

---

### Post by abybaddi on 2009-03-14
Nothing happens. Uh, I mean I again can't browse the Archive-mounted Ubuntu Disc.

Any suggestion?

---

### Post by hyper_ch on 2009-03-14
it's not a virus... virsues are no issue on linux.

---

### Post by abybaddi on 2009-03-14
> **hyper_ch said:**
> it's not a virus... virsues are no issue on linux.

Then what should I do?

---

