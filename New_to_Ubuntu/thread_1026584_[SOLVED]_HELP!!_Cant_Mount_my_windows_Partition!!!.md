---
title: "[SOLVED] HELP!! Cant Mount my windows Partition!!!"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by USFMD82 on 2008-12-31
I have been trying for a while now, and am having no luck getting my windows partition to load.. Here are some outputs I get when I run the commands here at this tutorial I found
[http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/](http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/)

```
timber@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8453    67898691    7  HPFS/NTFS
/dev/sda2            8454        9729    10249470    7  HPFS/NTFS
timber@ubuntu:~$ sudo cp /etc/fstab /etc/ftab.bak
timber@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
timber@ubuntu:~$ /dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
bash: /dev/sda1: Permission denied
timber@ubuntu:~$ 


```

Here is what comes up when i run this command (I read this in a few other posts.. 
df -h

```
timber@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      5.1G  2.8G  2.1G  59% /
tmpfs                 186M     0  186M   0% /lib/init/rw
varrun                186M  104K  186M   1% /var/run
varlock               186M     0  186M   0% /var/lock
udev                  186M  2.8M  183M   2% /dev
tmpfs                 186M     0  186M   0% /dev/shm
/dev/sda2             9.8G  6.3G  3.6G  64% /host
lrm                   186M  2.4M  183M   2% /lib/modules/2.6.27-9-generic/volatile
timber@ubuntu:~$ 

```

Anyone that could help me out here, thanks so much in advance!!

P.S. Everything else has been done in that tutorial with no problems up to the point I put the code in

---

### Post by Nepherte on 2008-12-31
You should put
```
/dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
```
in /etc/fstab as they tell you to do so in the tutorial you provided and not just enter it in the terminal.

---

### Post by USFMD82 on 2008-12-31
Im confused isn't that what I did when I put

> timber@ubuntu:~$ cat /etc/fstab

timber@ubuntu:~$ /dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1



forgot that I have also run the  gksu gedit /etc/fstab command the line still gives me the same result when I type it in I get this

```
timber@ubuntu:~$ /dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
bash: /dev/sda1: Permission denied

```

Is there some reason its not giving me the permission?

---

### Post by vanadium on 2008-12-31
The line beginning with "/dev/sda1" is a line that you should put in a text file called "fstab". "fstab" is located under /etc, and hence is easily referred to as /etc/fstab.

To add that line, you need to load the file in an editor. Because it is a system file, you need administrator rights (root rights) to be able to change the file.

First open the file with an editor of choice, for example gedit, with root permissions (sudo or gksudo)

```

sudo gedit /etc/fstab

```

The sudo command will instruct you to enter your user password, your usual login password. Only users with root privileges, such as the first installed user, can do this.

At the end of the file, add the line

```

/dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 2

```
Notice that I changed the last number from 1 to 2, which is preferred.

When done, save the file and close gedit.

There is a quick way to see if all is correct. Rather than restarting your system, just enter the command

```

sudo mount -a

```

This instructs ubuntu to read the file /etc/fstab and perform all mounts that are in there. This command should not produce any output. If there is output, there is a mistake somewhere in /etc/fstab. In the latter case, you better post the output here so we can help to correct the error.

---

### Post by USFMD82 on 2008-12-31
```
timber@ubuntu:~$ sudo gedit /etc/fstab
[sudo] password for timber: 
sudo: gedit: command not found
timber@ubuntu:~$ 

```

I also tried just opening it form the file manager and it let my type in the line but it wouldnt do anything afterwards it would let me save.. so Im lost even more now..


I dont know what editor I should open up either, or if it automatically should open one?

---

### Post by vanadium on 2008-12-31
Sorry, sorry, I did not notice you are a xubuntu user. gedit is standard with Ubuntu.

Anyway, you can use the text based "nano" editor. The command becomes

```

sudo nano /etc/fstab

```

---

### Post by USFMD82 on 2008-12-31
WORKS!! I will see if I can read write and all that good stuff, and if it auto mounts in the future thanks so much!!

---

### Post by radius611 on 2009-01-03
Thanks for the topic! ofcouse I had to change gedit to mousepad and in the etc/fstab, i changed the /media/windows part because it said now derictory found so now it's on my desktop =D! Thanks!!:popcorn:

---

### Post by amitkr on 2009-07-10
> **vanadium said:**
> Sorry, sorry, I did not notice you are a xubuntu user. gedit is standard with Ubuntu.

Anyway, you can use the text based "nano" editor. The command becomes

```

sudo nano /etc/fstab

```


I am using ubuntu 7.04, but now i am not able to login. It starts with black screen saying- /etc/init.d/rc: 2: sed: Permission denied

after i enter the root & password, it asks me to run apt-get install sed.

I don't have any clue, why it is happening?

I am able to see my files with ls command.

Command prompt is - root@(none):/#

when i run command  **sudo fdisk -l**

            Device      boot  Start     End      Blocks        Id      System
           /dev/sda1    *       1        1913    1536641      7      HPFS/NTFS
           /dev/sda2            **1914 **  9729    62782020     f      W95 Ext'd (LBA)
           /dev/sda5            **1914**   3122    9711261      83     Linux
           /dev/sda6            4464   7013    20482843+  b       W95 FAT32
           /dev/sda7            7014   9729    21816238+  b       W95 FAT32
           /dev/sda8            3189   4463    10241406    7        HPFS/NTFS
           /dev/sda9            3123   3188    530113+      82     Linux swap / solaris  

But now when i am trying to mount the linux partition /dev/sda5 with the following command, it is showing [B]sudo: mount: command not found
[/B]
**sudo mount /dev/sda5 /etc/amit**

Eveen when i am running **mount** command, it's showing -

**-bash: /bin/mount: Permission denied**

It seems i don't have the permission to mount it. plz help me out. thanx in advance

---

### Post by mikechant on 2009-07-10
amitkr: This is the second thread you have posted to. Please create your own thread instead of posting on the end of other people's threads.
Also, you need to try to make your post clearer. You say you can't log on, and then you say you are running the commands. How are you running them if you can't log on? Do you have two seperate problems? If so you need to deal with one at a time.
Anyhow, please don't add your post to any more threads. It just causes confusion and you are less likely to get help.

---

