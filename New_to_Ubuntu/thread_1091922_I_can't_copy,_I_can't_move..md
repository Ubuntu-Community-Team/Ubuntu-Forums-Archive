---
title: "I can't copy, I can't move."
date: 2009-03-09
forum: New to Ubuntu
---

### Post by mamamac on 2009-03-09
I have 2 hard drives in my desktop, (master and slave) and I want to move downloaded tv shows on my desktop to the slave, but when I drag the file, I get a message saying I dont have "permission"  Step by step, how do I get permission? I'm running 8.1 Intrepid Ibis.  Thanks guys.

---

### Post by taurus on 2009-03-09
What filesystem is your second harddrive and where do you mount it to, mount point?  

Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by markusf21 on 2009-03-09
I think the easiest way is to run Nautilus as root. ( alt+F2, type gksu nautilus) then navigate to the drive and right click it. Go to permissions and change the owner to you, and the group to you. click the box to apply to sub folders. then close nautilus. Don't use root nautilus unless you have to, it a good way to hose your system.

---

### Post by mamamac on 2009-03-09
ok, i figured out what you wanted... i think, and this is what it said.

thanks   
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb12ea965

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9353    75127941   83  Linux
/dev/sda2            9354        9729     3020220    5  Extended
/dev/sda5            9354        9729     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cf66f9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19081   153268101   83  Linux
/dev/sdb2           19082       19457     3020220    5  Extended
/dev/sdb5           19082       19457     3020188+  82  Linux swap / Solaris
robin@tallboy80:~$ 

 sudo f disk -l
[sudo] password for: 
sudo: f: command not found
      :~$ sudo blkid
/dev/sda1: UUID="99d23558-52dc-45f7-a210-e7d2e638c9c2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f078a49d-bb6f-4911-aa6a-32be03f2bec1" 
/dev/sdb1: UUID="ca2d88c9-a75b-4789-9300-b390a1c51e71" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="f59f57d5-73a7-4448-bfc6-a57161cf6886" 
robin@tallboy80:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=99d23558-52dc-45f7-a210-e7d2e638c9c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f078a49d-bb6f-4911-aa6a-32be03f2bec1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
       :~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   29G   39G  43% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  100K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  532K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-13-generic/volatile
:~$

---

### Post by mamamac on 2009-03-09
markusf21, how do i get to permissions? i'm really new at this, and am learning as i go. 
    thanks

---

### Post by taurus on 2009-03-09
The first command is **sudo fdisk -l**.  There should not be a space between f and disk.

---

### Post by mamamac on 2009-03-09
ok,    i thought i put it in just like it was written. sorry, i'm new to this.Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb12ea965

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9353    75127941   83  Linux
/dev/sda2            9354        9729     3020220    5  Extended
/dev/sda5            9354        9729     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cf66f9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19081   153268101   83  Linux
/dev/sdb2           19082       19457     3020220    5  Extended
/dev/sdb5           19082       19457     3020188+  82  Linux swap / Solaris
robin@tallboy80:~$




by the way tad 1073, i copied the commands and rebooted. this was the result...

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

and this...

Cannot mount volume.
Unable to mount the volume
[mntent]: line 9 in etc/fstab is bad
Unprivileged user can not mount NTFS devices ueing external FUSE library
Either mount the volume as root, or rebuild NTFS-3G with intergrated FUSE support
and make it setuid root.

---

### Post by tad1073 on 2009-03-09
open a terminal and type in:
```
sudo gedit /etc/fstab
```then add this to your fstab and that drive will automount when you boot up ubuntu
```
#/dev/sdb1
/dev/sdb1   /your/mountpoint   ext3   user,fmask=0111,dmask=0000   0   0

```it will also give you read/write access to the drve

---

### Post by taurus on 2009-03-09
> **tad1073 said:**
> open a terminal and type in:
```
sudo gedit /etc/fstab
```then add this to your fstab and that drive will automount when you boot up ubuntu
```
#/dev/sdb1
/dev/sdb1   /media/disk   **[COLOR="Red"]ntfs[/COLOR]**   user,fmask=0111,dmask=0000   0   0

```it will also give you read right access to the drve

Bad choice.  His /dev/sdb1 is ext3, not ntfs.

---

### Post by taurus on 2009-03-09
> **mamamac said:**
> ok,    i thought i put it in just like it was written. sorry, i'm new to this.Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb12ea965

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9353    75127941   83  Linux
/dev/sda2            9354        9729     3020220    5  Extended
/dev/sda5            9354        9729     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cf66f9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19081   153268101   83  Linux
/dev/sdb2           19082       19457     3020220    5  Extended
/dev/sdb5           19082       19457     3020188+  82  Linux swap / Solaris
robin@tallboy80:~$

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Save it and exit gedit window.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
By the way, is /dev/sdb1 an old Linux install that you don't need anymore?

---

### Post by tad1073 on 2009-03-09
> **taurus said:**
> Bad choice.  His /dev/sdb1 is ext3, not ntfs.

yeah I just realized that and edited my post

---

### Post by mamamac on 2009-03-09
OK  what is a mount point and how do i create it?

Oh, i almost forgot what started all this.... i still get this message when i drag a file.
The folder "Season 1" cannot be copied because you do not have permissions to create it in the destination.

---

### Post by markusf21 on 2009-03-10
> **mamamac said:**
> markusf21, how do i get to permissions? i'm really new at this, and am learning as i go. 
    thanks

right click on the drive

---

### Post by mamamac on 2009-03-10
ok   I click on the hard drive, and it opens up. I drag the file over to the open drive and place it in an empty space. then the error message pops up telling me this....

"The folder "Season 1" can not be copied because you do not have permissions to create it in the destination"

This is the same situation I started with.
I still dont know how to 'mount' something, or what that even is.
and folks, just because you know what to say dosent mean i know what you mean.I thank you all for wanting to help, but the same situation still remains.  :(   

when i right click on the drive and open the permissions tab, it says 'The permissions of "sbdl" could not be determined'

---

### Post by shazbut on 2009-03-10
Seems the drive is already mounted, but is owned by root and/or does not have write access for your username.  Without seeing your output from:
```
ls -l /media
```
I'd guess you might need either:
```
sudo chmod 777 /media/sdb1
```
or
```
sudo chown username:group /media/sdb1
eg: sudo mamamac:admin /media/sdb1
```
(Assuming /media/sdb1 is the mount point of the 2nd HDD)
See here for more info on what these commands do: [http://en.wikibooks.org/wiki/Guide_to_UNIX/Commands/File_System_Utilities]("http://en.wikibooks.org/wiki/Guide_to_UNIX/Commands/File_System_Utilities")

---

### Post by mamamac on 2009-03-10
ok shazbut, here you go. by the by, the website you recomended cant be found

:~$ ls -l /media
total 8
lrwxrwxrwx  1 root root    6 2009-02-26 08:51 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-02-26 08:51 cdrom0
drwxr-xr-x 20 root root 4096 2009-02-26 00:09 sdb1
robin@tallboy80:~$

or just walk me thru getting access...it's my system

---

### Post by taurus on 2009-03-10
```
sudo chown -R robin:robin /media/sdb1
ls -la /media
```

---

### Post by elliotn on 2009-03-10
Alt+f2 gksudo natilius(mind the spell) always gives me permission

---

### Post by mamamac on 2009-03-10
TAURUS..... we have lift off:D:popcorn::D:P:D

Thank you to all for your patience with a newby 

thank you thank you thank you

---

