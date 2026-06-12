---
title: "Mounting"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by DarinB on 2009-02-27
i was helped in getting a second drive mounted at boot up, it works great, But it shows on my desktop all the time, i like the feature in nautilus >>> volumes visible <<<< so i can easily get to mounted thumb drives but i would like the secondary drive to not show. 
any ideas????

---

### Post by taurus on 2009-02-27
Instead of mounting your second harddrive to /media/**sdb1** (or whatever the mount point is), maybe you want to mount it to /mnt/sdb1 in /etc/fstab.

---

### Post by DarinB on 2009-02-27
isn't that what you had me do the other day?
should i send you the commands you had me do?

---

### Post by Xiong Chiamiov on 2009-02-27
```

sudo mkdir /mnt/sdb1
sudo vim /etc/fstab
   :%s/media\/sdb1/mnt\/sdb1/g
   :wq

```
Of course, you could do the same with perl, or many other things.  For that matter, you could actually change the line yourself, using gedit or whatever.

---

### Post by taurus on 2009-02-27
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by DarinB on 2009-02-27
darin@darin-desktop:~$ sudo fdisk -l
[sudo] password for darin: 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ae79d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19175   154023156   83  Linux
/dev/sdb2           19176       19457     2265165    5  Extended
/dev/sdb5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf8909d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   83  Linux
darin@darin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=ffcf5658-1b5f-412d-9494-96bbeceeb61e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=62a027e1-7926-46ef-8252-f8d213b5d164 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=3a4f7394-8461-4d90-abf8-7489fecd4825   /media/music   ext3   defaults   0   2
darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             145G   25G  114G  18% /
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  100K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.8M  375M   1% /dev
tmpfs                 378M  232K  378M   1% /dev/shm
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc1              74G   52G   19G  74% /media/music

---

### Post by taurus on 2009-02-27
If you edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and change the mount point from /media/music to /mnt/music for /dev/sdc1, then you won't see an icon on your desktop.

```
UUID=3a4f7394-8461-4d90-abf8-7489fecd4825 **[COLOR="Blue"]/mnt/music[/COLOR]** ext3 defaults 0 2
```
Save it and now you need to create the new mount point.

```
sudo mkdir /mnt/music
```
Reboot and /dev/sdc1 will be now mounted to /mnt/music.

And of course, if you want to be the owner of /mnt/music, just change the ownership of /mnt/music from root to your login name, darin.

```
sudo chown -R darin:darin /mnt/music
ls -la /mnt
df -h
```

---

### Post by DarinB on 2009-02-27
that seems to work now i have to change the directory on my rhythmbox and restart to check thanks again taurus

---

