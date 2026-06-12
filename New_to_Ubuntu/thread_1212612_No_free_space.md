---
title: "No free space"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by toonewbie on 2009-07-13
Hello.  This is my first time at this.  I have installed 9.04 as a dual boot system.  When i made the partition I allocated 100gb to Ubuntu.  I have just tried to save a project to my desktop and for some reason I only have 900meg available.  I checked all other folders and found that I only have 900meg available to all of them.  There is a volume that has 94gb available but I do not have permission to write to it.  i have been through all the permissions and granted myself access but I still cannot access the free space.  I am as NEW as they come, any help would be greatly appreaciated.

---

### Post by nhasian on 2009-07-13
hello,

please open up a terminal and give us the output of the following commands:

```
sudo fdisk -l
```

```
df -h
```

---

### Post by toonewbie on 2009-07-13
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdaebdae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      108853   874360832    7  HPFS/NTFS
/dev/sda2          108854      121601   102398310    5  Extended
/dev/sda5          121078      121601     4208998+  82  Linux swap / Solaris
/dev/sda6          108854      120574    94148869+  83  Linux
/dev/sda7          120575      121077     4040316   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)

---

### Post by sdlynx on 2009-07-13
You have 2TB of space!
Sorry for that off topic comment...

---

### Post by toonewbie on 2009-07-13
This was the reply to 
df -h

Filesystem            Size Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       17G   15G  883M  95% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  220K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  164K  1.6G   1% /dev
tmpfs                 1.6G  148K  1.6G   1% /dev/shm
/dev/sda1             834G   81G  753G  10% /host
lrm                   1.6G  2.2M  1.6G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6              89G  184M   84G   1% /media/disk
/dev/sr1              7.2G  7.2G     0 100% /media/cdrom1
wazza@ubuntu:~$ Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
bash: Disk: command not found
wazza@ubuntu:~$ 255 heads, 63 sectors/track, 121601 cylinders
bash: 255: command not found
wazza@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
wazza@ubuntu:~$ Disk identifier: 0xbdaebdae
bash: Disk: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
wazza@ubuntu:~$ /dev/sda1   *           1      108853   874360832    7  HPFS/NTFS
bash: /dev/sda1: Permission denied
wazza@ubuntu:~$ /dev/sda2          108854      121601   102398310    5  Extendedbash: /dev/sda2: Permission denied
wazza@ubuntu:~$ /dev/sda5          121078      121601     4208998+  82  Linux swap / Solaris
bash: /dev/sda5: Permission denied
wazza@ubuntu:~$ /dev/sda6          108854      120574    94148869+  83  Linux
bash: /dev/sda6: Permission denied
wazza@ubuntu:~$ /dev/sda7          120575      121077     4040316   82  Linux swap / Solaris
bash: /dev/sda7: Permission denied
wazza@ubuntu:~$ 
wazza@ubuntu:~$ Partition table entries are not in disk order
bash: Partition: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$ Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
bash: Disk: command not found
wazza@ubuntu:~$ 255 heads, 63 sectors/track, 121601 cylinders
bash: 255: command not found
wazza@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
wazza@ubuntu:~$ Disk identifier: 0x44fdfe06
bash: Disk: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
wazza@ubuntu:~$ /dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
bash: syntax error near unexpected token `('

---

### Post by sdlynx on 2009-07-13
It looks to me as if Ubuntu has been installed and mounted on the wrong partition than what you wanted.

Did you run this off of a live cd? It must be run off of your host system for (at least) me to interpret it correctly.

---

### Post by nhasian on 2009-07-13
when i type in the terminal:

```
df -h
```

I get:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G  4.7G   15G  25% /
tmpfs                1005M     0 1005M   0% /lib/init/rw
varrun               1005M  348K 1005M   1% /var/run
varlock              1005M     0 1005M   0% /var/lock
udev                 1005M  308K 1005M   1% /dev
tmpfs                1005M   88K 1005M   1% /dev/shm
/dev/sdb1             111G  188M  105G   1% /data
/dev/sda3              80G   33G   43G  44% /home

```

see how i used the CODE tag? It makes reading the output a lot easier :)  You can just copy and paste it from the terminal here.  highlight the data and click on the CODE tag.

---

### Post by toonewbie on 2009-07-13
I downloaded the ISO from ubuntu main page and installed it .  If I run Windows and go into c: I have 850+ gb.  I also have an external hard drive connected to the system which is 1tb as well.  The hard drive was on my dersktop and i could access it but for some reason it no longer is there.  I can see it in the menu places but I cannot mount it.

---

### Post by toonewbie on 2009-07-13
I see that you did that but I have absolutely no idea how to do that. lol.  Sorry.

---

### Post by nhasian on 2009-07-13
> **toonewbie said:**
> I see that you did that but I have absolutely no idea how to do that. lol.  Sorry.

I wrote you instructions on how to quote text and code up a few messages above this.


i noticed you had two swap partitions.  You only need on of those if any at all :)

also i noticed you had a /host.  did you install ubuntu from within windows?  if so then you installed ubuntu within your windows C: and not into its own partition that you made for it.  if you want to install ubuntu into its own partition, you must boot from the LiveCD and start the installation from there.

---

### Post by toonewbie on 2009-07-13
I should probably try to re install?

---

### Post by toonewbie on 2009-07-13
Where do I get this CODE tag from?

---

### Post by toonewbie on 2009-07-14
Sorry,  where do i get the CODE tag from?

---

### Post by nhasian on 2009-07-14
if you did indeed install ubuntu from within windows then yes.  first in windows go to add/remove programs and uninstall ubuntu.  then boot from the liveCD and select boot ubuntu without making any changes to your hard disk.  once ubuntu loads you can double click on the install icon on the ubuntu desktop.  at the beginning of the installation it will have a graphical partition editor to help you find the right place to put it.  make sure to use manual partition instead of automatic.  I would also disconnect your usb drive while doing the install.  

psychocats had a tutorial on how to install ubuntu in a dual boot configuration with windows but i couldnt find it... i only found the wubi method which is not what you want.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by sdlynx on 2009-07-14
> **toonewbie said:**
> Sorry,  where do i get the CODE tag from?

you'll want to type '[' + 'code' + ']' to start what text will be in the code format and '[' + '/code' + ']' to end it. I would type it normally but then the text would show up as code lol.  Or you can hit the # button right below the Message: after highlighting what you want as code.

---

### Post by toonewbie on 2009-07-14
I Just checked Windows and Ubuntu is not on its c:.  When i boot the PC it comes up with the page to choose which O\S you would like to Run.  If this helps any.  I still have the disc I installed off.

---

### Post by toonewbie on 2009-07-14
[code]df -h
Filesystem            Size Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       17G   15G  883M  95% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  220K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  164K  1.6G   1% /dev
tmpfs                 1.6G  148K  1.6G   1% /dev/shm
/dev/sda1             834G   81G  753G  10% /host
lrm                   1.6G  2.2M  1.6G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6              89G  184M   84G   1% /media/disk
/dev/sr1              7.2G  7.2G     0 100% /media/cdrom1
wazza@ubuntu:~$ Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
bash: Disk: command not found
wazza@ubuntu:~$ 255 heads, 63 sectors/track, 121601 cylinders
bash: 255: command not found
wazza@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
wazza@ubuntu:~$ Disk identifier: 0xbdaebdae
bash: Disk: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
wazza@ubuntu:~$ /dev/sda1   *           1      108853   874360832    7  HPFS/NTFS
bash: /dev/sda1: Permission denied
wazza@ubuntu:~$ /dev/sda2          108854      121601   102398310    5  Extendedbash: /dev/sda2: Permission denied
wazza@ubuntu:~$ /dev/sda5          121078      121601     4208998+  82  Linux swap / Solaris
bash: /dev/sda5: Permission denied
wazza@ubuntu:~$ /dev/sda6          108854      120574    94148869+  83  Linux
bash: /dev/sda6: Permission denied
wazza@ubuntu:~$ /dev/sda7          120575      121077     4040316   82  Linux swap / Solaris
bash: /dev/sda7: Permission denied
wazza@ubuntu:~$ 
wazza@ubuntu:~$ Partition table entries are not in disk order
bash: Partition: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$ Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
bash: Disk: command not found
wazza@ubuntu:~$ 255 heads, 63 sectors/track, 121601 cylinders
bash: 255: command not found
wazza@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
wazza@ubuntu:~$ Disk identifier: 0x44fdfe06
bash: Disk: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
wazza@ubuntu:~$ /dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
bash: syntax error near unexpected token `('
[code]

---

### Post by toonewbie on 2009-07-14
I have absolutely no idea.  LOL.

---

### Post by sdlynx on 2009-07-14
the ending code tag is /code not just code

---

### Post by toonewbie on 2009-07-14
Ya gotta laugh at newbies

```
df -h
Filesystem            Size Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       17G   15G  883M  95% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  220K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  164K  1.6G   1% /dev
tmpfs                 1.6G  148K  1.6G   1% /dev/shm
/dev/sda1             834G   81G  753G  10% /host
lrm                   1.6G  2.2M  1.6G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6              89G  184M   84G   1% /media/disk
/dev/sr1              7.2G  7.2G     0 100% /media/cdrom1
wazza@ubuntu:~$ Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
bash: Disk: command not found
wazza@ubuntu:~$ 255 heads, 63 sectors/track, 121601 cylinders
bash: 255: command not found
wazza@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
wazza@ubuntu:~$ Disk identifier: 0xbdaebdae
bash: Disk: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
wazza@ubuntu:~$ /dev/sda1   *           1      108853   874360832    7  HPFS/NTFS
bash: /dev/sda1: Permission denied
wazza@ubuntu:~$ /dev/sda2          108854      121601   102398310    5  Extendedbash: /dev/sda2: Permission denied
wazza@ubuntu:~$ /dev/sda5          121078      121601     4208998+  82  Linux swap / Solaris
bash: /dev/sda5: Permission denied
wazza@ubuntu:~$ /dev/sda6          108854      120574    94148869+  83  Linux
bash: /dev/sda6: Permission denied
wazza@ubuntu:~$ /dev/sda7          120575      121077     4040316   82  Linux swap / Solaris
bash: /dev/sda7: Permission denied
wazza@ubuntu:~$ 
wazza@ubuntu:~$ Partition table entries are not in disk order
bash: Partition: command not found

```

---

### Post by toonewbie on 2009-07-14
whoo hoo!!!

---

### Post by toonewbie on 2009-07-14
Dose any one know what this means


```
wazza@ubuntu:~$ Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
bash: Disk: command not found
wazza@ubuntu:~$ 255 heads, 63 sectors/track, 121601 cylinders
bash: 255: command not found
wazza@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
wazza@ubuntu:~$ Disk identifier: 0xbdaebdae
bash: Disk: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
wazza@ubuntu:~$ /dev/sda1   *           1      108853   874360832    7  HPFS/NTFS
bash: /dev/sda1: Permission denied
wazza@ubuntu:~$ /dev/sda2          108854      121601   102398310    5  Extendedbash: /dev/sda2: Permission denied
wazza@ubuntu:~$ /dev/sda5          121078      121601     4208998+  82  Linux swap / Solaris
bash: /dev/sda5: Permission denied
wazza@ubuntu:~$ /dev/sda6          108854      120574    94148869+  83  Linux
bash: /dev/sda6: Permission denied
wazza@ubuntu:~$ /dev/sda7          120575      121077     4040316   82  Linux swap / Solaris
bash: /dev/sda7: Permission denied
wazza@ubuntu:~$ 
wazza@ubuntu:~$ Partition table entries are not in disk order
bash: Partition: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$ Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
bash: Disk: command not found
wazza@ubuntu:~$ 255 heads, 63 sectors/track, 121601 cylinders
bash: 255: command not found
wazza@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
wazza@ubuntu:~$ Disk identifier: 0x44fdfe06
bash: Disk: command not found
wazza@ubuntu:~$ 
wazza@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
wazza@ubuntu:~$ /dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
bash: syntax error near unexpected token `('
wazza@ubuntu:~$ 


```

---

### Post by nhasian on 2009-07-14
did you check your add/remove in the control panel?  you will have an ubuntu line in there you should uninstall.  

> **toonewbie said:**
> I Just checked Windows and Ubuntu is not on its c:.  When i boot the PC it comes up with the page to choose which O\S you would like to Run.  If this helps any.  I still have the disc I installed off.

---

