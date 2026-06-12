---
title: "Need fstab support"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by tansu on 2008-12-28
I tried most of the possible solutions around web. So, I have three harddisks in my system.
The first one is where ubuntu is installed, you can see in the fstab as sda1
Other two are ntfs hardisks and fstab doesn not mention them. They are sdb1 and sdc1 
So should my fstab be to automatically mount these ntfs hardisks.
thanks

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5210c75a-28e7-4bdd-88cb-4278730d800b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4631d8c2-3651-41a5-ad68-70f914ea62f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Michael.Godawski on 2008-12-28
hey, 

can you please post the output of these commands so that we can add the needed entries to your fstab file?

```
sudo fdisk -l 
df -h 
sudo blkid
```

---

### Post by Bucky Ball on 2008-12-28
Go to Synaptics and install:

ntfs-3g

Run that (it will be in one of your menus) to permanently mount your ntfs drives and write them into your /fstab. Easiest. The other way is to manually enter the partition details in fstab which is a lot more involved. This application will also provide reliable read/write support as ntfs is not native to linux.

---

### Post by tansu on 2008-12-28
Thanks. Here are the results:
```
tansu@tansu-desktop:~$ sudo fdisk -l 


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85478547

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1275fa0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc09093fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS
tansu@tansu-desktop:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.7G   65G   4% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  100K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  2.8M  756M   1% /dev
tmpfs                 759M  580K  758M   1% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-9-generic/volatile
tansu@tansu-desktop:~$ sudo blkid
/dev/sda1: UUID="5210c75a-28e7-4bdd-88cb-4278730d800b" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4631d8c2-3651-41a5-ad68-70f914ea62f1" 
/dev/sdb1: UUID="18EE284CEE28248A" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc1: UUID="36B22DD9B22D9E7D" LABEL="New Volume" TYPE="ntfs" 
tansu@tansu-desktop:~$ 

```

---

### Post by tansu on 2008-12-28
> **Bucky Ball said:**
> Go to Synaptics and install:

ntfs-3g

Use that to permanently mount your ntfs drives. Easiest. The other way is to manually enter the partition details in fstab which is a lot more involved.
Well it says already installed, but I couldnt find it..

---

### Post by Bucky Ball on 2008-12-28
I'm on the wrong computer but it is in either Applications or System.

Try in the terminal:

```
sudo ntfs-3g
```

That might run the gui.

---

### Post by tansu on 2008-12-28
> **Bucky Ball said:**
> I'm on the wrong computer but it is in either Applications or System.

Try in the terminal:

```
sudo ntfs-3g
```

That might run the gui.
it says
ntfs-3g: No device is specified.

---

### Post by Michael.Godawski on 2008-12-28
Creating mount points:
```
sudo mkdir /media/ntfs_one
sudo mkdir /media/ntfs_two
```Editing fstab:

Make a backup of fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
```
```
gksudo gedit /etc/fstab
```
Adding the fstab entries for ntfs partitions

```
UUID=18EE284CEE28248A  /media/ntfs_one ntfs ro,umask=0002,nls=utf8    0         0
UUID=36B22DD9B22D9E7D  /media/ntfs_two ntfs ro,umask=0002,nls=utf8    0         0


```

---

### Post by Elfy on 2008-12-28
ntfs-3g is installed default now you mean ntfs-config - installed it has a tool in system tools which can be used to mount ntfs drives - but it's as well to know how to edit fstab.

I went through this for someone earlier today - [http://ubuntuforums.org/showpost.php?p=6448563&postcount=7](http://ubuntuforums.org/showpost.php?p=6448563&postcount=7) no need for the chmod/chown commands

---

### Post by Bucky Ball on 2008-12-28
Got ya. Can't find in the menus?

This is it, I think:

gksudo ntfs-config

---

### Post by sisco311 on 2008-12-28
add this lines to the fstab:
```

UUID=18EE284CEE28248A /media/sdb1 ntfs defaults,umask=002,gid=46 0 0
UUID=36B22DD9B22D9E7D /media/sdc1 ntfs defaults,umask=002,gid=46 0 0
```

where /media/sdb1 and /media/sdc1 are the mount points.

type:
```
sudo mkdir /media/sdb1
sudo mkdir /media/sdc1
```to create them.

and mout the partitions:
```
sudo mount -a
```

(btw you also can use ntfs-config: [http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows"))

EDIT: d'oh, i'm slooooow!!

---

### Post by HavocXphere on 2008-12-28
deleted

---

### Post by tansu on 2008-12-28
well ntfs config comes with nothing. It asks my password but nothing after that.

About the fstab editing, I got these errors after mounting:

Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

It asks me to force, and I did, and it worked..

Is it ok to force to mount?

---

### Post by Dedoimedo on 2008-12-28
Maybe your partitions are already mounted.
Check under /mnt or /media.
Dedoimedo

---

### Post by tansu on 2008-12-28
> **Dedoimedo said:**
> Maybe your partitions are already mounted.
Check under /mnt or /media.
Dedoimedo
No,
after forcing just one of them is mounted but not the normal way...

---

### Post by DariusS on 2008-12-28
> **tansu said:**
> well ntfs config comes with nothing. It asks my password but nothing after that.

About the fstab editing, I got these errors after mounting:

Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

It asks me to force, and I did, and it worked..

Is it ok to force to mount?

I usually get this message when I try to mount a windows partition after not shutting down windows cleanly. I would either force mount or boot back in to windows and do a clean shutdown.

---

### Post by tansu on 2008-12-28
> **DariusS said:**
> I usually get this message when I try to mount a windows partition after not shutting down windows cleanly. I would either force mount or boot back in to windows and do a clean shutdown.
:) ntfs hardisks are zillion years old :) I dont have a windows for some time.
Well finally, forcing to mount seems to be working..
I just need to know is there any harm forcing it? and what is the fstab edit to force..
Thanks a lot

---

### Post by ajgreeny on 2008-12-28
Having now done a forced mount, you shouldn't need to do it again, it ought to be a once only need.

Here is a good page with a lot of info on fstab for you to look at and learn, it's good to know about the options available in fstab and it can come in very useful occasionally.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by albinootje on 2008-12-28
> **Bucky Ball said:**
> Got ya. Can't find in the menus?

This is it, I think:

gksudo ntfs-config

Indeed, you can do :
```

sudo apt-get install ntfs-config
sudo ntfs-config

```
Editing /etc/fstab manually is also possible.

---

### Post by Bucky Ball on 2008-12-28
You could check your fstab now to see if it has been re-written with the correct details. If not, I doubt if they will automatically mount at boot. Reboot. Did they mount?

---

### Post by tansu on 2008-12-28
> **ajgreeny said:**
> Having now done a forced mount, you shouldn't need to do it again, it ought to be a once only need.

Here is a good page with a lot of info on fstab for you to look at and learn, it's good to know about the options available in fstab and it can come in very useful occasionally.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
OK then, thank you..
One more question. You know I forced to mount sdb1 via terminal and it mounted. Now I restarted the system and it is still mounted.. Does it mean is it forcing everytime?

---

### Post by Bucky Ball on 2008-12-28
> **albinootje said:**
> Indeed, you can do :
```

sudo apt-get install ntfs-config
sudo ntfs-config

```Editing /etc/fstab manually is also possible.

I believe that should be:

```
gksudo ntfs-config
```... for launching an app outside the terminal. I can't remember why, read it in my travels. Maybe someone else could chip in with the reason or explanation. :)

---

### Post by ajgreeny on 2008-12-28
> Does it mean is it forcing everytime?
No, it does not mean that.  The terminal command you used will now be relegated to bash history and only used if you choose to again.

---

### Post by tansu on 2008-12-28
Well, thanks to everyone involved.
ntfs-config finally worked after installing :) (damn confusion ntfs-config-3g ) and wewritten fstab. Not it works like charm..
Here is the latest fstab:
```
# Entry for /dev/sdb1 :
UUID=18EE284CEE28248A /media/sdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Entry for /dev/sdc1 :
UUID=36B22DD9B22D9E7D /media/sdc1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

thanks to everyone again..

---

### Post by albinootje on 2008-12-28
> **Bucky Ball said:**
> I believe that should be:

```
gksudo ntfs-config
```... for launching an app outside the terminal. I can't remember why, read it in my travels. Maybe someone else could chip in with the reason or explanation. :)

Depends..
I tested "sudo ntfs-config" before I posted this, and it started.
(Even when I don't have any NTFS partitions, hehe).

"sudo gedit" also works fine, for some applications gksudo is really needed.

---

### Post by Elfy on 2008-12-28
sudo gedit will work but there's the possibility that using sudo with gui apps can cause problems which is why it's best to use gksu or gksudo for GUI apps

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by albinootje on 2008-12-28
> **forestpixie said:**
> sudo gedit will work but there's the possibility that using sudo with gui apps can cause problems which is why it's best to use gksu or gksudo for GUI apps

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanks for the link.

I think that [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) has quite a few very good pages for ubuntu users, and I appreciate the honesty of the author in the security section.

But this link mentions running Firefox as root, without even given an explanation why you would need to run Firefox as root.
That's a hilarious example to promote using gksudo on a page like that.

---

