---
title: "How do i auto mount a partition??"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-10-31
i have a separate partition for my music which i would like to be mounted when i start up, how would i go about doing this?

---

### Post by Zoot7 on 2009-10-31
What type of file system does the partition have? ext3? ntfs? fat32?

Also can you post the output of
```
sudo fdisk -l
```

---

### Post by JamesParnell on 2009-10-31
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a0b9548

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+  83  Linux
/dev/sda2            3917        6527    20972857+  83  Linux
/dev/sda3            6528        6788     2096482+  82  Linux swap / Solaris

```

and they are all EXT4

---

### Post by Zoot7 on 2009-10-31
Firstly make a mount point for the partition.

```
sudo mkdir /media/<name>
```

Then edit fstab
```
gksudo gedit /etc/fstab
```

Assuming /dev/sda1 is the partition of interest, add in the following line at the end of the file:
```
/dev/sda1 /media/<mount point name> ext4	defaults	0   0
```

Then to test it do
```
sudo mount -a
```

Then browse to wherever you mounted it to investigate. Any problems, post them back here.

---

### Post by SuperSonic4 on 2009-10-31
Which one is music? I'm gonna assume it's sda2 because it's non-boot

Create a mount pount, again I will say /mnt/Music

```
sudo mkdir /mnt/Music
```

Open fstab as root:

```
gksu gedit /etc/fstab
```


Add in the line (tabs and/or spaces - both are good)

```
/dev/sda2 /mnt/Music ext4 defaults 0 0
```

Save and exit and then run ```
sudo mount -a
```

More hints and explanation: [http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab) (ignore the fact it's for arch - it still works and fstab is a common file with the same config options across GNU/Linux)

---

### Post by agoodliffe on 2009-11-06
Hello I am encoutnering the same problem.

Here is my fdisk -l
adrian@adrian-laptop:~$ sudo fdisk -l
[sudo] password for adrian: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d6f1d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            3129       11061    63721822+   c  W95 FAT32 (LBA)
/dev/sda3            1913        3128     9767520   83  Linux
/dev/sda4           11813       12161     2803342+  82  Linux swap / Solaris

Partition table entries are not in disk order
adrian@adrian-laptop:~$ ^C
adrian@adrian-laptop:~$
I want to mount the /dev/sda2 and the /dev/sda1
I created two folders in /media one called sda1 and the other windows
Then I did gksudo gedit /etc/fstab
Then I did /dev/sda1 /media/sda1 ext4 defaults 0 0 
and the reply was sudo: /dev/sda1: Permission denied
ANy suggestions and yes I am a newbie to this as you can see
Thanks

---

### Post by harish4linux on 2009-11-06
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time

Code:
sudo aptitude update
sudo aptitude install ntfs-config

Ok so when that returns you to user@pcname, that should be it installed 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). And then run the program from Applications > System Tools

Note: In Ubuntu 9.04 (Jaunty) it appears that the configuration tool has moved to System > Administration.

Enter your password when prompted - and then choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

Enjoy your automounted NTFS Drives

---

### Post by agoodliffe on 2009-11-06
thanks for the advice but I am not connected to the internet. ANy way to manually do it in Terminal? Or is it to dangerous/confusing

---

### Post by Zoot7 on 2009-11-06
> **agoodliffe said:**
> thanks for the advice but I am not connected to the internet. ANy way to manually do it in Terminal? Or is it to dangerous/confusing
Almost the same as I posted above. :)

Firstly make a mount point for the partition.
(Lets say Windows..)
```
sudo mkdir /media/Windows
```

Then edit fstab
```
kdesu kate /etc/fstab
```

Add the following line at the end and save.
```
/dev/sda1 /media/Windows ntfs-3g	defaults	0   0
```

Then to test it do
```
sudo mount -a
```

Browse to /media/Windows to test if it worked.

The terminal takes a bit of getting used to especially if you've never really used it much, but it's well worth it. It's without doubt an extremely powerful tool once you get the hang of it.

---

### Post by synicalx on 2009-11-06
> **harish4linux said:**
> Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time

Code:
sudo aptitude update
sudo aptitude install ntfs-config

Ok so when that returns you to user@pcname, that should be it installed 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). And then run the program from Applications > System Tools

Note: In Ubuntu 9.04 (Jaunty) it appears that the configuration tool has moved to System > Administration.

Enter your password when prompted - and then choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

Enjoy your automounted NTFS Drives

Just browsing around and I saw this - thanks!

I've been having a bit of trouble with my MSI Wind's NTFS partition, this fixed it right up :D

---

### Post by agoodliffe on 2009-11-07
> **Zoot7 said:**
> Almost the same as I posted above. :)

Firstly make a mount point for the partition.
(Lets say Windows..)
```
sudo mkdir /media/Windows
```

Then edit fstab
```
kdesu kate /etc/fstab
```

Add the following line at the end and save.
```
/dev/sda1 /media/Windows ntfs-3g	defaults	0   0
```

Then to test it do
```
sudo mount -a
```

Browse to /media/Windows to test if it worked.

The terminal takes a bit of getting used to especially if you've never really used it much, but it's well worth it. It's without doubt an extremely powerful tool once you get the hang of it.

Thanks I followed these steps and I am using Xubuntu 9.10

```
sudo mkdir /media/Windows
```
```
gksu gedit /etc/fstab
```
```
/dev/sda1 /media/Windows ntfs-3g	defaults	0   0
``` 
then it says bash: /dev/sda1: Permission denied

Any advice?
Thanks

---

### Post by SuperSonic4 on 2009-11-07
Do you have a screenshot to show this?

---

### Post by Zoot7 on 2009-11-07
> **agoodliffe said:**
> Thanks I followed these steps and I am using Xubuntu 9.10

```
sudo mkdir /media/Windows
```
```
gksu gedit /etc/fstab
```
```
**[COLOR="Red"]/dev/sda1 /media/Windows ntfs-3g	defaults	0   0[/COLOR]**
``` 
then it says bash: /dev/sda1: Permission denied

Any advice?
Thanks
Add the line in red above to the end of the file fstab, that you opened with gksu gedit, save it and close. I suspect you just typed it into the terminal; that's not going to work.

---

