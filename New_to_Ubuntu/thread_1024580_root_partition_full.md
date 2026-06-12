---
title: "root partition full?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by kramer65 on 2008-12-29
Hello,


I've got a separate home and root folder. I now wanted to download something but it says that I don't have enough space in /tmp.

I had a look and it seems that my root partition (37 GB) is full. How can this be? I don't have so many programs to use so much space? Can anybody help me out here?

---

### Post by Elfy on 2008-12-29
I would start by checking trashes - including roots

[http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

Check that page - in particular 3. Free Space - Where Did It Go?

If you want some help then we'll need the output of df -h to start with.

---

### Post by ajgreeny on 2008-12-29
Have a look with Disk Usage Analyser in Programs > Accessories. It may give you some clues.

---

### Post by kramer65 on 2008-12-29
Alright, so I used that. I see some figures. Now what?

(to be honest, I've been using ubuntu for about 2 years now and used to love it up until a month ago. Nowadays, I work more for the computer than that it works for me..)

---

### Post by Sealbhach on 2008-12-29
Maybe you have deb packages left over that you don't need.

Try 

```
sudo apt-get clean
```

```
sudo apt-get autoclean 
```

The Disk Usage Analyser suggested by ajgreeny will show you what's taking up all the space on your disk. It's shows it as a picture if you don't like looking at figures.


.

---

### Post by shankhs on 2008-12-29
> **kramer65 said:**
> Alright, so I used that. I see some figures. Now what?

(to be honest, I've been using ubuntu for about 2 years now and used to love it up until a month ago. Nowadays, I work more for the computer than that it works for me..)
i agree with kramer65 completely,I have been using ubuntu for an year now.
Same prblem here as that of kramer65 the only exception is that my /home partition is full , I think I have to resize it using gparted but the main problem is the free space in my HD is not just adjacent to the filled partition.Can gparted work in this case also : extending /home partition to a free space which is not adjacent to present /home partition????

---

### Post by Elfy on 2008-12-29
> **shankhs said:**
> i agree with kramer65 completely,I have been using ubuntu for an year now.
Same prblem here as that of kramer65 the only exception is that my /home partition is full , I think I have to resize it using gparted but the main problem is the free space in my HD is not just adjacent to the filled partition.Can gparted work in this case also : extending /home partition to a free space which is not adjacent to present /home partition????

No - you'll need to move the unallocated sp[ace next to the home partition to be able to resize home. Gparted can do that.

If you need help with it - then I would suggest starting a thread of your own.

---

### Post by Elfy on 2008-12-29
> **kramer65 said:**
> Alright, so I used that. I see some figures. Now what?

(to be honest, I've been using ubuntu for about 2 years now and used to love it up until a month ago. Nowadays, I work more for the computer than that it works for me..)

Is this a new version or an old one?

Could you post your df -h 

Also run this and post the result (thanks tinivole)
```
sudo du / -xh --max-depth=1 | grep G
```

---

### Post by kramer65 on 2008-12-29
```
kram@mypc-desktop:~$ df -h
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda3              37G   37G     0 100% /
tmpfs                 1,7G     0  1,7G   0% /lib/init/rw
varrun                1,7G  364K  1,7G   1% /var/run
varlock               1,7G     0  1,7G   0% /var/lock
udev                  1,7G  2,9M  1,7G   1% /dev
tmpfs                 1,7G  600K  1,7G   1% /dev/shm
lrm                   1,7G   39M  1,6G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             175G   63G  106G  38% /home
overflow              1,0M   96K  928K  10% /tmp
/home/kram/.Private  175G   63G  106G  38% /home/ricam/Private
/dev/sda1             604G  213G  392G  36% /media/disk
```

```
kram@mypc-desktop:~$ sudo du / -xh --max-depth=1 | grep G
[sudo] password for kram: 
30G	/media
5,1G	/usr
37G	/
```

Does that tell you anything?

---

### Post by 21:27 on 2008-12-29
i'd try checking trash. gksudo nautilus, turn on view hidden items and go to root/.local/trash and check if there are any files there. had likewise problem a couple of days ago.

---

### Post by Elfy on 2008-12-29
What do you have in /media - that's got 30Gb 

Do ```
ls -al /media
```

Check that, on mine I have a few mount points only in /media

---

### Post by kramer65 on 2008-12-29
@ 21:27
I went into gksudo and then turned hidden view on but in the folder /root/.local there is only a folder called share and nothing else.

@ forestpixie
When I do the command you suggest I get this:

```
kram@mypc-desktop:~$ ls -al /media
totaal 40
drwxr-xr-x  6 root  root  4096 2008-12-29 18:26 .
drwxr-xr-x 21 root  root  4096 2008-12-22 09:58 ..
drwxr-x---  4 root  root  4096 2008-12-29 10:01 backup
lrwxrwxrwx  1 root  root     6 2008-07-20 19:24 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2008-07-20 19:24 cdrom0
drwx------  5 ricam root 16384 1970-01-01 01:00 disk
-rw-r--r--  1 root  root   110 2008-12-29 18:26 .hal-mtab
-rw-------  1 root  root     0 2008-12-29 18:26 .hal-mtab-lock
drwxr-xr-x  2 root  root  4096 2008-08-04 10:41 samba_share
```

But I don't think /media is the problem since the problem is the system part and media are all the other things (like external hard drive, CD-rom, usb-stick etc.) right?

---

### Post by Elfy on 2008-12-29
/media is where 30Gb of your 37Gb are - what's in /media/backup?

Yes you are right that /media is usually where things get mounted - but there's nothing to stop anything being mounted there.

I assume that disk is just that a mounted disk

---

### Post by kramer65 on 2008-12-29
Ah yes. I have an external drive with music and movies (about 200GB) which I set the system to backup to another folder (not on the system but on a different partition). So from one secondary partition to another secondary partition. I don't think this would be the problem.. or could it be..?

---

### Post by Elfy on 2008-12-29
Check the folder - see what's there

```
ls -al /media/backup
```

Or just have a look

---

### Post by kramer65 on 2008-12-29
I think you got my problem there. After your command I got this:
```

kram@mypc-desktop:~$ sudo ls -al /media/backup
[sudo] password for kram: 
totaal 16
drwxr-x--- 4 root root 4096 2008-12-29 10:01 .
drwxr-xr-x 6 root root 4096 2008-12-29 18:26 ..
drwxr-x--- 2 root root 4096 2008-12-22 12:30 2008-12-22_10.52.11.952127.kram-desktop.ful
drwxr-x--- 2 root root 4096 2008-12-29 10:01 2008-12-29_10.01.04.316578.kram-desktop.inc
```

Can I just delete these backups and disable the backup function?

---

### Post by kramer65 on 2008-12-29
Ok, with gksudo nautilus I went to the /media/backup folder and deleted the files there by simply hitting the delete button. It disappeared but it is now obviously in the trash can. It is not in the normal trashcan but when I click the trashcan in the sudo nautilus window it says that the contents could not be displayed. 

I still cannot download anything. WHere did those "sudo deletes" go and how can I get rid of them forever?

---

### Post by albinootje on 2008-12-29
> **kramer65 said:**
> ```

Does that tell you anything?

Did you perform a :
[code]
sudo apt-get clean

```

And do a reboot, sometimes df will incorrectly keep saying that still 0% is available for a while.

Post also the result of :
```

sudo du -sh /var/log
sudo du -sh /var/tmp
sudo du -sh /tmp

```

---

### Post by albinootje on 2008-12-29
> **kramer65 said:**
> Ok, with gksudo nautilus I went to the /media/backup folder and deleted the files there by simply hitting the delete button. 

/media is on a separate partition, and therefore you can ignore remarks about that.
Please check the other suggestion that don't mention /media

---

### Post by albinootje on 2008-12-29
> **shankhs said:**
>  Same prblem here as that of kramer65 the only exception is that my /home partition is full

Did you clean your Trash folders ?
And use the "Disk Usage Analyser" -> Applications -> Accessories to find out where the most space is taken.

---

### Post by Elfy on 2008-12-29
```
gksudo nautilus
``` to run nautilus as root

---

