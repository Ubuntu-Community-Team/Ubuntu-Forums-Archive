---
title: "How to access /home files using a Live CD?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2009-01-30
So I managed to screw up my Windows XP Pro 64-bit installation, and I ended up deleting its partition.  On a tangent, I thought it was highly ironic that on my HDD I had 4 partitions, one NTFS and three used by Ubuntu (swap, /, /home), and I had to use GParted to recreate the primary partition with NTFS because Windows' partition manager was informing me that I had reached the disk's "partition limit" and couldn't make another partition.  I have since reinstalled the O/S but as this was the boot partition my boot manager is now gone.

Since I wanted to try Jaunty Jackalope on the computer (and try EXT4) I was going to move my data to my second hard drive from my /home partition.  There isn't a lot of it, so I thought it would be easy.  Only when booting from the Live CD I can't access the data because I don't have permissions to do so.  

So how do I get permissions to copy my data?  Alternately, how do I recreate my Grub bootloader so I can boot to Ubuntu again, copy my data over, and then wipe it out and install Jaunty using the EXT4 file system?

Thanks!

---

### Post by taurus on 2009-01-30
Open a terminal from the LiveCD and run nautilus with root privilege.  That would let you move all your files to another harddrive.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

And if you want to reinstall GRUB to MBR again, here is a link.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Nixie Pixel on 2009-01-31
Thank you!  I would "Thank" you but the function doesn't seem to be working at the moment.  :D

---

### Post by elpix on 2009-02-02
I have a similar problem, I was doing an upgrade from 7.10 to 8.04 only it didnt work, after login nothing happens.
I want to do a new install, but before that ( a bit late...)
Im tryng to retrieve my data, so I am using a live CD, I can read the partition but certain files( My baby daughter pictures!!!) are locked.
the gksu nautilus  command doesnt seem to do the trick (it opens a  file browser window).
Can anybody help.
And another question, if I install over my old ubuntu, on the same partition where intallation and data are housed, will my files be preserved_
Thank you

---

### Post by taurus on 2009-02-02
> **elpix said:**
> I have a similar problem, I was doing an upgrade from 7.10 to 8.04 only it didnt work, after login nothing happens.
I want to do a new install, but before that ( a bit late...)
Im tryng to retrieve my data, so I am using a live CD, I can read the partition but certain files( My baby daughter pictures!!!) are locked.
the gksu nautilus  command doesnt seem to do the trick (it opens a  file browser window).
Can anybody help.
And another question, if I install over my old ubuntu, on the same partition where intallation and data are housed, will my files be preserved_
Thank you

Yes, **gksudo nautilus** will open a file browser window (with root privilege) so you have to navigate to where your photos are on the harddrive, assuming you have already mounted it.  Even if those photos are locked (they own by user 1000, your original user when you installed Ubuntu, while Ubuntu LiveCD is ubuntu), you should still can access them from the LiveCD unless you changed the permissions so nobody can view them except you, the only user from the machine.

---

### Post by elpix on 2009-02-02
Thank you Taurus, but the problem I have is that Nautilus only navigates to either

root ( of the CD)
Desktop (CD)
File system (cd also), and
Trash

but cant seem to open 

disk

 where my data is, that I can see in another file browser and in desktop, it doesnt show when i get to home/ubuntu/desktop though

Sorry for the inexperience and the lack of terminal skills

---

### Post by taurus on 2009-02-02
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
df -h
```
That should be a lower case letter L, not number 1.

---

### Post by elpix on 2009-02-05
Taurus,
Thanks for the reply, sorry I didnt get back to you sooner,
Below are the results from

sudo fdisk -l
df -h
 
hope it helps you help me.
Appreciate it.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317        7874    52665344    7  HPFS/NTFS
/dev/sda4            7875        9730    14901696+   f  W95 Ext'd (LBA)
/dev/sda5            9403        9730     2620416   82  Linux swap / Solaris
/dev/sda6            7875        9402    12273628+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 501M   16M  486M   4% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 501M   16M  486M   4% /lib/modules/2.6.22-14-generic/volatile
varrun                501M   96K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  116K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
tmpfs                 501M   12K  501M   1% /tmp
/dev/sda6              12G   11G  713M  94% /media/disk
ubuntu@ubuntu:~$

---

### Post by drs305 on 2009-02-05
elpix,

It appears *disk* is already mounted on /media. You should be able to access the contents with:
```
gksudo nautilus /media/disk
```

If you are on the LiveCD and it isn't mounted:
```

sudo mkdir /media/sda6  # or disk, or another mount point name
sudo mount /dev/sda6 /media/sda6
gksudo nautilus /media/sda6

```

---

### Post by nitrofurano on 2009-03-17
well i do 'sudo nautilus --no-desktop' ....

---

### Post by presence1960 on 2009-03-17
> **elpix said:**
> Thank you Taurus, but the problem I have is that Nautilus only navigates to either

root ( of the CD)
Desktop (CD)
File system (cd also), and
Trash

but cant seem to open 

disk

 where my data is, that I can see in another file browser and in desktop, it doesnt show when i get to home/ubuntu/desktop though

Sorry for the inexperience and the lack of terminal skills
mount the disk BEFORE you open nautilus

---

