---
title: "No disc space?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by LordBonney on 2010-09-07
Hi,

I've just started using Ubuntu, running it off an external hard drive on a Samsung N150, and I tried to go and update everything via the Update Manager, but it keeps on telling me that there isnt enough room?

Initially it says that the updates will take up 309.5 MB, but when I click on Install Updates it tells me that 'The upgrade needs a total of 602M free space on disk '/'. Please free at least an additional 130M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'. Following those instructions doesnt seem to work either.

My hard drive has over 100GB left on it, and the hard drive Im running it off has another 400GB or so. I tried with a 2GB USB stick just to check its not my external drive, but I get pretty much the same message?

Thanks.

---

### Post by davidmohammed on 2010-09-07
Please can you open a terminal session and type the following

df

df -i

post the replies to each command here in a CODE tag.

---

### Post by LordBonney on 2010-09-07
Typing in df gets

```
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    508004    197040    310964  39% /
none                    503100       280    502820   1% /dev
/dev/sdb1            488264736    926752 487337984   1% /cdrom
/dev/loop0              675328    675328         0 100% /rofs
none                    508004       168    507836   1% /dev/shm
tmpfs                   508004        20    507984   1% /tmp
none                    508004       104    507900   1% /var/run
none                    508004         0    508004   0% /var/lock
none                    508004         0    508004   0% /lib/init/rw
/dev/sda2               102396     24832     77564  25% /media/SYSTEM
```df -i comes up with

```
 Filesystem            Inodes   IUsed   IFree IUse% Mounted on
aufs                  127001    4913  122088    4% /
none                  125775     788  124987    1% /dev
/dev/sdb1                  0       0       0    -  /cdrom
/dev/loop0            138914  138914       0  100% /rofs
none                  127001       4  126997    1% /dev/shm
tmpfs                 127001      54  126947    1% /tmp
none                  127001      56  126945    1% /var/run
none                  127001       1  127000    1% /var/lock
none                  127001       1  127000    1% /lib/init/rw
/dev/sda2             143100      93  143007    1% /media/SYSTEM
```

---

### Post by davidmohammed on 2010-09-07
are you running ubuntu via a wubi install in windows, or as a dual boot?

---

### Post by LordBonney on 2010-09-07
I'm following the instructions exactly as here - [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download), running off an external hard drive, although I initially tried with a smaller USB stick.

I didnt delete Windows, and if I remove the hard drive/USB stick then Windows starts up and works fine.

---

### Post by davidmohammed on 2010-09-07
Have you actually installed ubuntu, or are you running ubuntu via the USB stick?  If its the latter, you have run out of space on your USB stick.

Use Applications -- Accessories -- Disk Usage Analyser.  Scan your file system, and look for any unusually large files.

---

### Post by LordBonney on 2010-09-07
> **davidmohammed said:**
> Have you actually installed ubuntu, or are you running ubuntu via the USB stick?  If its the latter, you have run out of space on your USB stick.

Use Applications -- Accessories -- Disk Usage Analyser.  Scan your file system, and look for any unusually large files.

Im running it off an external hard drive, but the only thing on it is Ubuntu, and its a 500GB drive, so it shouldnt be a space issue. I've tried just downloading 90MB worth of updates onto the USB stick, which has nearly 1GB left on it, and it still tells me I have no space. 

I cant find the Disk Usage Analyser there, but I'll keep looking.

---

### Post by davidmohammed on 2010-09-07
Check ~/.local/share/Trash and /root/.local/share/Trash to make sure you don't have any large files stuck in trash.

the Disk Usage Analyser can be started from a command line by typing

baobab

alternatively type

sudo du -xsk * | sort -rn

this will give you a directly listing showing which folder contains the largest size of files

you can then "cd" into that directory and rerun that command to "drill" down to find out which folders contain the abnormal files

---

