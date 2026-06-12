---
title: "Need Help &quot;No Space left on Disk&quot;"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by neo.patrix on 2009-07-14
I have a serious problem with my /home. I run fsck quite a few times from LiveCD but to no good. I know with every fiber in my body, that something terribly out of place with my system.

Any file operation ends with error "No space left on device", which incorrect error message, because I can show there on my harddisk which is ill-calcuated by OS

Output from df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             6.1G  974M  4.9G  17% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  124K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  160K 1007M   1% /dev
tmpfs                1007M   48K 1007M   1% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6              27G   18G  7.8G  70% /home
/dev/sda7              17G  5.7G  9.7G  37% /usr
```

Now, I am only user on the system, so /home/patrix is only directory with some disk usage for /home  (I expect it to be so, please explain if it could be otherwise).I have deleted /home/lost+found.

now /home/patrix is only 3.7GiB in size. So where is other 14.3 GiB going which df -h reports as used. I am very sure that there is nothing like movies or games on my /home/patrix that can eat up that amount of memory.
Even if assume that 14.3 GiB is used by some mystical being, why do I get error message "No Space left on device" with sitll 7.8 GiB at hand?

Please I am hard pressed to fix this, cannot work with any programs, everything ends up with "No space left on device", I cannot enter GNOME main session aswell, have to used Failsafe, but now I know it is only side affect.

---

### Post by donkyhotay on 2009-07-14
How big is your swap partition? Even with a ton of RAM linux assumes there is a minimal amount of swap available (can't remember the amount) and gets a little strange if it's not there.

---

### Post by neo.patrix on 2009-07-14
SWAP is 2GB, but I wonder if that could be problem, hardly ever I have seen it being used. Ok my partition table is as

```

255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        2034    16289910    7  HPFS/NTFS
/dev/sda3            2035        2839     6466162+  83  Linux
/dev/sda4            2840       14593    94414005    f  W95 Ext'd (LBA)
/dev/sda5            2840        8645    46636663+   7  HPFS/NTFS
/dev/sda6            8646       12214    28667961   83  Linux
/dev/sda7           12215       14354    17189518+  83  Linux
/dev/sda8           14355       14593     1919736   82  Linux swap / Solaris


```

sda3 is mounted as /, sda6 is mounted as /home & sda7 is mounted as /usr. Remaining are windows partition.

---

### Post by Irony on 2009-07-14
Follow these instructions;

[http://ubuntuforums.org/showthread.php?t=315654](http://ubuntuforums.org/showthread.php?t=315654)

---

### Post by neo.patrix on 2009-07-14
Thanx Irony, I will check on that. But I have one more strange update

I usually mount /home in windows using Ext2Fsd v 1.0 .
So here is memory analysis result on windows, sda6 which is partition for my /home is mounted as X: on windows. 

Well good news (although not very comforting) is, X: also shows 
17.5 GB used as well. The properties show 4.11GB used also but 
"size on disk" is 17.5G. What am I suppose to understand by this 
is that 4.11GB occupies 17.5GB on disk. ](*,)](*,)

[[IMG]http://img43.imageshack.us/img43/7526/xpartition.th.jpg[/IMG]](http://img43.imageshack.us/i/xpartition.jpg/)

---

### Post by neo.patrix on 2009-07-15
I have solved the problem with help of "Disk Usage Analyser". The problem was a shell script used by Conky which runs at interval of every 60s probably. The script uses calcurse as an intermediary to display my 
appointments and tasks stored in Evolution. Everytime this script is executed it imports Evolution stuff to calcurse does some formating operations , then deletes appointments & todo from calcurse.

But, calcurse internally generates files present at ~/.calcurse/notes for every todo or task, now this files where not deleted unfortunately.
The "notes" folder containted very very large number of small files occupying 13.5 GiB of memory. Once, I got ride of those files and fixed my script , all works great now.

So, if anyone is using evolution-task.sh which comes with conky-colors
make sure, you delete files from ~/.calcurse/notes

---

