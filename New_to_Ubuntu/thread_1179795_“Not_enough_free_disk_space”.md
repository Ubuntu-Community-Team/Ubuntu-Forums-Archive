---
title: "“Not enough free disk space”"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Sedative on 2009-06-06
When I try to install the updates in my update manager, I get this message:

```
Not enough free disk space

The upgrade needs a total of 123M free space on disk '/'. Please free at least an additional 85.2M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
```


Umm, I most certainly DO have free space. What's going on?

---

### Post by Elfy on 2009-06-06
Can you post the result of

```
df -h
```

---

### Post by Sedative on 2009-06-06
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              29G   27G  8.5M 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  184K  1.5G   1% /dev
tmpfs                 1.5G  1.7M  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             422G  137G  286G  33% /media/disk

```

---

### Post by Elfy on 2009-06-06
/dev/sda5              29G   27G  8.5M 100% /

You have 8.5Mb free on root - is trash full?

Check through this it should help - [http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

---

### Post by Sedative on 2009-06-06
I don't think it could be. I just installed Ubuntu last night.

*goes to link*

EDIT: not one item in my trash.

EDIT #2:

I installed a few things for Firefox and it now says this in update manager:

```
Not enough free disk space

The upgrade needs a total of 123M free space on disk '/'. Please free at least an additional 122M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
```

EDIT #3: I used 

```
sudo apt-get clean
```

Like it says, and it now says this;

```
Not enough free disk space

The upgrade needs a total of 123M free space on disk '/'. Please free at least an additional 20.0M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

```

---

### Post by Elfy on 2009-06-06
mmm - ok so what have you done since you installed last night?

You can get a visual representation of the drive - Applications > Accessories > Disk Usage Analyzer - once it is opened in the toolbar choose check filesystem - see what that shows up.

From the link I gave you it is also possible to look for files above a size.

---

### Post by Sedative on 2009-06-06
I went there. Look at this:

Total filesystem capacity: 450.0 GB (used: 163.4 GB avaliable: 286.6 GB)


So yeah, I have the space.

---

### Post by Elfy on 2009-06-06
I'm not saying that you don't have space on the hard drive - but you don;t have space on the / partition.

If I open the disk usage tool - it says I have 300Gb - but it includes other partitions I have mounted.

Run the tool again - do a screenshot of it and paste it here - screenshot tool in apps > accessories - though the PrtSc button should do so too.

---

### Post by Sedative on 2009-06-06
Sorry, it's really late. I'll do it tomorrow when I wake up. Will edit.

---

### Post by Elfy on 2009-06-06
Good night then :)

---

### Post by Sedative on 2009-06-06
[http://i43.tinypic.com/24pks8z.png](http://i43.tinypic.com/24pks8z.png)


[http://i39.tinypic.com/33dz98z.png](http://i39.tinypic.com/33dz98z.png)

---

### Post by Elfy on 2009-06-06
Hi - you have 25Gb almost in your home - music/videos maybe - but that is where all you space has been taken up.

Check in there - Places,Home Folder - when it's opened do Ctrl+H - it will show the hidden files/folders.

If you run the analsyer again and do Ctrl+S it will scan your home folder only, as that is where the space has gone it will be useful.

---

### Post by Sedative on 2009-06-06
Oh, that's where all of my documents from Vista are- including thousands of pictures (I'm a photographer) and all of my random things. So, I'm not going to be able to do my updates?

---

### Post by Elfy on 2009-06-06
Were they copied from vista, moved from vista?

You can access files on your vista install if you wish to.

If not then you will need to think about partition sizes - they can be changed.

---

### Post by LewRockwell on 2009-06-06
throw a live-run CD in there and give us a screen shot of your gparted

or you could give us the output of:

```
sudo fdisk -l
```

(that's a little "L" and NOT a one)

---

### Post by Sedative on 2009-06-06
I have a dual boot with Vista

result of 

```
 sudo fdisk -l
```




```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd338468

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55060   442267616    7  HPFS/NTFS
/dev/sda2           58977       60801    14658560    7  HPFS/NTFS
/dev/sda3           55061       58976    31455270    5  Extended
/dev/sda5           55061       58809    30113811   83  Linux
/dev/sda6           58810       58976     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by drs305 on 2009-06-06
I'm getting in here rather late, but if you follow the steps in the guide "RecoverLostDiskSpace" linked in my signature line it may help you discover why your have run out of room.

If it helps find the problem please let us know what it was.

---

### Post by Sedative on 2009-06-06
Thanks so much! And nobody is too late if I still haven't found the solution. I'll go to the link (too bad I'm completely clueless about most of this stuff)


For now I am going to uncheck everything except for the important security updates and install those, then install the recommended updates when this is figured out.

EDIT: Oh, come on! Now it's saying I don't even have enough space for that!!


EDIT AGAIN: Now it's saying that I don't have enough space for ONLY the Firefox updates! Something is seriously wrong.

---

### Post by Miljet on 2009-06-06
What is seriously wrong is that you didn't make your / partition large enough for everything you want to have there.

ForestPixie was trying to explain that if you have copied all your pictures fron your Vista partition, there is no reason to do that. You can access the pictures just as easily from the Vista partition as you can from the Ubuntu partition.

If you want to keep that much data in the Ubuntu partition, you will have to make the partition larger.

---

