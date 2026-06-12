---
title: "Unrecognized Hard drive"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by Thunderbird1988 on 2010-04-22
Hello,

I have installed Xubuntu. The problem is thaat I have two hard drives, but Xubuntu recognises only one of them. I can reach the other and it is also not listed in the System Monitor under the File Systems Tab.

Does anyone knows how to reach the second drive? There are files on it I like to have access to.

Thunderbird1988

---

### Post by cariboo on 2010-04-23
I have used Xubuntu in a while, so the instructions may not be exact. Open a terminal and type:

```
sudo fdisk -l
```

the output should look something like this:

```
fdisk -l
[sudo] password for me: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9629a182

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1217        1459     1951897+  82  Linux swap / Solaris
/dev/sdb3            1460       30401   232476584    5  Extended
/dev/sdb5            1460       15197   110350453+  83  Linux
/dev/sdb6           16414       30401   112358578+  83  Linux
```

I my example Ubuntu is on my second hard drive /dev/sdb, your system will probably be different, but your second hard drive should be the same /dev/sdbX, you can manually mount a partition by in the same termianl typing:

```
sudo mount /dev/sdb1 /mnt
```

The above commands mounts the first partition on the second drive in /mnt, you should now be able to access your files on /mnt.

---

### Post by Thunderbird1988 on 2010-04-23
Hello,

Thank you for your reply.

I have perfromed your instructions. But it seems it didn´t work. I shall post the items in the terminal. They are in Dutch trough, if you'd like me to translate something. Please ask.

```
[sudo] password for hein: 

Schijf /dev/sda: 30.6 GB, 30606151680 bytes
255 koppen, 63 sectoren/spoor, 3720 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x000bcf51

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        3582    28772383+  83  Linux
/dev/sda2            3583        3720     1108485    5  Uitgebreid
/dev/sda5            3583        3720     1108453+  82  Linux wisselgeheugen

Schijf /dev/sdb: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xd491d491

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1               1       14946   120053713+  8e  Linux LVM
hein@Computer-Hein:~$ sudo mount /dev/sdb1 /mnt
mount: onbekende bestandssysteemsoort 'LVM2_member' (translation: unknown filesystemsort 'LVM2_member')
```Can you tell me what went wrong?

---

### Post by srs5694 on 2010-04-23
The fdisk command in this case is diagnostic only; it's not supposed to fix anything. What it reveals is that your first disk (the 30GB one) is partitioned in a fairly conventional way, with Linux swap and Linux filesystem partitions. The second (122GB) disk, though, is set up with a Linux Logical Volume Management (LVM) partition, which is an advanced filesystem management tool. It's unclear how your system is configured -- it might or might not already be using the LVM partition. The following commands will provide more information:

```

df -h
sudo vgdisplay

```

Post the output of both commands and somebody should be able to interpret them and advise you on how to proceed. (There may be multiple ways to proceed, so don't be surprised if you get conflicting advice.)

---

### Post by Thunderbird1988 on 2010-04-24
Thank you for your reply.

Here is the output of both commands:

```
hein@Computer-Hein:~$ df -h
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda1              28G  2,8G   23G  11% /
udev                  186M  216K  186M   1% /dev
none                  186M     0  186M   0% /dev/shm
none                  186M   84K  186M   1% /var/run
none                  186M     0  186M   0% /var/lock
none                  186M     0  186M   0% /lib/init/rw
hein@Computer-Hein:~$ sudo vgdisplay
[sudo] password for hein: 
sudo: vgdisplay: command not found
```

---

### Post by srs5694 on 2010-04-24
OK, your situation is this: You've installed Ubuntu on /dev/sda1 (your 30GB hard disk's main partition), and your second (~122GB) drive is currently unused. It's got a partition that's marked as an LVM partition, but you don't have any LVM tools installed, so that LVM marking is presumably either in error or is a holdover from a previous installation or use of the disk in another computer. Since you say that the drive has files you want to access, I'll assume that the LVM flag is correct and the disk was previously used in another Linux installation. You'll need to install the lvm2 package to access the LVM. You can type "sudo apt-get install lvm2" or use Synaptic to do the job. With this done, you can try the vgdisplay command again. You may need to use the vgimport command to make the volume group accessible. (The vgdisplay command will show the volume group name early in its output, on a line labeled "VG name". Pass that name to vgimport.) You should then see logical volume(s) appear in the /dev/mapper directory, as in /dev/mapper/vg01-home, /dev/mapper/vg01-foo, and so on. You can treat these filenames as if they were partitions to mount them with mount, as in:

```

sudo mount /dev/mapper/vg01-home /mnt/home
sudo mount /dev/mapper/vg01-foo /mnt/foo

```

The precise filenames will be unique to your system, and you'll have to have mount point(s) prepared (that is, create /mnt/home, /mnt/foo, or whatever directories you plan to use). If you want to use these directories in the long term, you'll want to create /etc/fstab entries for them, as in:

```

/dev/mapper/vg01-home   /home    xfs  allocsize=512m      0  2
/dev/mapper/vg01-foo   /mnt/foo  reiserfs  defaults      0  0

```

Precisely what goes in /etc/fstab depends to some extent on what's in those partitions. For instance, you may need to adjust the filesystem type codes (xfs and reiserfs in these examples) and of course the mount points. The first of these examples mounts /dev/mapper/vg01-home at /home, which results in it replacing whatever your current /home directory contains. You might or might not want to do this, depending on what's in your logical volumes and what's in your current /home directory.

---

