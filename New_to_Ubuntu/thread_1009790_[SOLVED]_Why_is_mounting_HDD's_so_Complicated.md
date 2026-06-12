---
title: "[SOLVED] Why is mounting HDD's so Complicated?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-12-13
Why is there not an auto-mount option available through the GUI?  I want my FAT32 drive and my NTFS drive to mount at boot, so I download Storage Device Manager.  But now when they boot up, all of my files are read-only!  I can't get the permissions to change?

What is the actual reason why this has to be so darned complicated?

Thanks for any help.

---

### Post by tomtom1982 on 2008-12-13
Please type in your console and post output of:

```
sudo fdisk -l
```

Edit:You only have to add the partitions you want to auto-mount into the /etc/fstab.

Which Version are you using? Ubuntu, Kubuntu, Xubuntu...?

On Kubuntu for example you can rightclick the device and set the permissions to "display and changes possible" or something like this (using Kubuntu in German, so I don't know how it is named in english.

You also can set the option "mount automaticly" there.

---

### Post by nhasian on 2008-12-13
Go to: Applications->Add Remove->System Tools

then install: Storage Device Manager.

or you can do it from the terminal:

```
sudo apt-get install pysdm
```

Open Storange Device Manager via System->Administration->Storage Device Manager

Now you can set ext3 and ntfs drives to be mounted at boot.

---

### Post by jynyl on 2008-12-13
This seems to be more difficult than it needs to be.
It is not obvious that extra software needs to be installed.  Surely this should be part of the base install package?

Also, even if "read only" is checked, Dolphin reports permissions are 777 (writable) unless umask is set to 222.

---

### Post by nhasian on 2008-12-13
the additional software just makes it easier for you to use with a GUI, but its not required.  you can make the necessary changes to /etc/fstab yourself if you like

```
sudo vi /etc/fstab
```

but its a lot easier for beginners to use the gui.

---

### Post by drs305 on 2008-12-13
If you decide to try Storage Device Manager (pysdm) here is a HOWTO from the Tutorials & Tips section of the forum:
[Storage Device Manager - Worry-Free Fstab Configuration]("http://ubuntuforums.org/showthread.php?t=872197")

---

### Post by Eric Qel-Droma on 2008-12-13
That's a handy how-to.  However, there are several terms there that I still don't understand.  (I don't know the difference between umask/dmask/fmask etc.)

Anyway, thanks for the tip.

---

### Post by Eric Qel-Droma on 2008-12-13
My fdisk -l results:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d567d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       24320    92952090    f  W95 Ext'd (LBA)
/dev/sda5           12749       19122    51199123+   c  W95 FAT32 (LBA)
/dev/sda6           23840       24320     3863601   82  Linux swap / Solaris
/dev/sda7           19123       23839    37889271   83  Linux

Partition table entries are not in disk order

```

I am currently using the following options on my drives through Storage Device Manager:

sda1:  nls=iso8859-1,umask=000,user
sda5:  umask=000,user

But I don't know what they mean.  They have given me read-write access to the files (I can edit now!), but I can't send things to the trash.  I can only delete.

Thanks for the help.

---

### Post by |{urse on 2008-12-13
The reason this is so "complicated" is because you aren't used to doing it this way. Also it is the aim of the linux operating system to give users FULL control over every aspect of their computer, which means sometimes we have to get down to its level and understand how it works rather than "plug and play" which can also be achieved by installing the appropriate software to do it for you. I, personally am still looking for software that will play video games for me so i don't have to.

---

### Post by drs305 on 2008-12-13
Think of **u**mask as universal, whereas **d**mask sets permissions for **d**irectories and **f**mask sets them only for regular files.

It would probaly be easiest if you posted your fstab and where things are mounted and we can help you set it up. Post 
```
sudo blkid
mount
cat /etc/fstab
```

Permissions are set with umask,dmask and fmask, but they don't make you the *owner* of the files. Depending on the file type, such as fat or ntfs formats, permissions are set at the time of mounting and cannot be changed. There is a good chance you can access the files, but because you aren't the *owner*, you can't delete them. Ownership can be changed with an fstab setting.

Edited: Just read that you *can* delete them but not move them to the trash. Can you delete them as a normal user or do you have to do it as root? Non-linux partitions usually create a trash bin for trash deleted by the user/owner in the partition by the name of .Trash-XXXX with XXXX being your UID.

Added: Here is the ubuntu community documentation on file permisions:
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by Eric Qel-Droma on 2008-12-13
> **|{urse said:**
> The reason this is so "complicated" is because you aren't used to doing it this way. Also it is the aim of the linux operating system to give users FULL control over every aspect of their computer, which means sometimes we have to get down to its level and understand how it works rather than "plug and play" which can also be achieved by installing the appropriate software to do it for you. I, personally am still looking for software that will play video games for me so i don't have to.

Hmm.  Hmm.  It seems to me that one could have "full" control with superior default options, especially since mounting from the "Places" menu actually gives the user read/write capability.

I find your post vaguely insulting and condescending, especially on "Absolute Beginner Talk", and I'm not sure how it's either helpful or relevant.  I don't know how to do something and am asking how to do it, while at the same time I marvel at how annoyingly complicated the initial set-up is when it could obviously be so much easier.  The staggering--to this beginner, anyway--options available are great, in my opinion.  I think a user **should** have full control over his OS.  However, the simple desire to have a HDD available at boot and to have (what seems to me) the obvious useful default settings set to read/write seems neither unreasonable nor lazy.  In fact, one could read my initial question as a **non**-lazy question designed to increase my understanding of Linux, which, after years of DOS/Windows, isn't exactly what I'm used to, you're right about that.

BTW, if there **is** a good reason why this is (apparently) so complicated, I did ask for that in my first post and I'd be happy to hear it.  Again, I want to be productive, but I am still willing to learn.

In any case, if you could avoid lecturing me on what "we" should do as Linux users, I'd really appreciate it.  Thanks.

Eric

---

### Post by Eric Qel-Droma on 2008-12-13
> **drs305 said:**
> Think of **u**mask as universal, whereas **d**mask sets permissions for **d**irectories and **f**mask sets them only for regular files.

Added: Here is the ubuntu community documentation on file permisions:
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

Very helpful.  Thank you very much.

Here are the things for which you asked:

```
eric@eric-desktop:~$ sudo blkid
[sudo] password for eric: 
/dev/sda1: UUID="DAD8FBFED8FBD6AB" LABEL="WIN-NTFS" TYPE="ntfs" 
/dev/sda5: LABEL="SHARE-FAT32" UUID="AED2-903C" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="e1b957b6-ebda-4210-b05d-b048b9026520" 
/dev/sda7: UUID="f71b3b85-3af9-497e-a43d-cea54cc12270" TYPE="ext3" 
eric@eric-desktop:~$ mount
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /media/SHARE-FAT32 type vfat (rw,noexec,nosuid,nodev,umask=000)
/dev/sda1 on /media/WIN-NTFS type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/sda7 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)
eric@eric-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc               proc         defaults                      0  0  
# /dev/sda7
UUID=f71b3b85-3af9-497e-a43d-cea54cc12270  /                   ext3         relatime,errors=remount-ro    0  1  
# /dev/sda6
UUID=e1b957b6-ebda-4210-b05d-b048b9026520  none                swap         sw                            0  0  
/dev/scd0                                  /media/cdrom0       udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/sda5                                  /media/SHARE-FAT32  vfat         umask=000,user                0  0  
/dev/sda1                                  /media/WIN-NTFS     ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda6                                  /media/sda6         swap         defaults                      0  0  
/dev/sda7                                  /media/sda7         ext3         defaults                      0  0  
eric@eric-desktop:~$ 

```

Thanks for your considerate help to this newbie.  It is greatly appreciated.

Eric

---

### Post by drs305 on 2008-12-13
Eric,

Here is how I would redo your fstab for sda1 and sda5.

Make yourself the owner of the mountpoints (not technically necessary for these file formats):
```

sudo chown -R *eric:* /media/WIN-NTFS  /media/SHARE-FAT32

```
Backup fstab and open for editing (use the editor of your choice):
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Replace with:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc               proc         defaults                      0  0  
# /dev/sda7
UUID=f71b3b85-3af9-497e-a43d-cea54cc12270  /                   ext3         relatime,errors=remount-ro    0  1  
# /dev/sda6
UUID=e1b957b6-ebda-4210-b05d-b048b9026520  none                swap         sw                            0  0  
/dev/scd0                                  /media/cdrom0       udf,iso9660  user,noauto,exec,utf8         0  0  
[COLOR="DarkRed"]
# /dev/sda1
UUID=DAD8FBFED8FBD6AB                      /media/WIN-NTFS     ntfs-3g      auto,users,uid=1000,umask=027,utf8    0 0  
# /dev/sda5 
UUID=AED2-903C                             /media/SHARE-FAT32  vfat         auto,users,uid=1000,umask=027,utf8    0  0  
[/COLOR]
/dev/sda6                                  /media/sda6         swap         defaults                      0  0  
/dev/sda7                                  /media/sda7         ext3         defaults                      0  0  

```

Save the file, then unmount (disregard any busy messages) and remount:
```
sudo umount -a
sudo mount -a
```
If successful, you will not get any messages when the second command is run.

I will be glad to answer any questions you have as to what any of this means. I used UUIDs rather than /dev/sdXX as the UUIDs generally will not change whereas the device designation may change, especially if using external devices. I also changed the setting to utf8 from "nls=iso8859-1" but you can replace that if you wish.

Here is an excellent reference on fstab from the ubuntu community:
[Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by egalvan on 2008-12-14
> **Eric Qel-Droma said:**
> Hmm.  Hmm.  It seems to me that one could have "full" control with superior default options, especially since mounting from the "Places" menu actually gives the user read/write capability.


Well, let's see....

Yes, one can gain "full" control with "superior default options" by running as root.
Then the first time you deleted/munged some critical system files,
or some cracker broke into your machine?
Linux helps guard against this. Not eliminate them, mind you, just guard against them.


> I find your post vaguely insulting and condescending, especially on "Absolute Beginner Talk", and I'm not sure how it's either helpful or relevant.

this is your opinion, so I can't comment...


>   I don't know how to do something and am asking how to do it, while at the same time I marvel at how annoyingly complicated the initial set-up is when it could obviously be so much easier.

"so much easier" for whom? for you? for me? "One-size-fits-everybody" is a Microsoft specialty, not often easily found in the *nix world. Choices make things a bit more complicatied.

> The staggering--to this beginner, anyway--options available are great, in my opinion.  I think a user **should** have full control over his OS.

but how about a beginner? Some of *nixes controls are meant to deter 'fumble-fingers'.  Not eliminate them, mind you, just deter them.

>   However, the simple desire to have a HDD available at boot and to have (***_what seems to me)_*** the obvious useful default settings set to read/write seems neither unreasonable nor lazy.

Exactly, to YOU.
 To ME, maybe they are NOT USEFUL. 

Not every user wants (or needs) all drives mounted at boot.
For instance, NTFS is not a native Linux file system, so extra care is taken when allowing writes to it. A bad write can wipe out an entire partition...
(NTFS is not an "open" specification... so it had to be reversed-engineered... not an exact science, but mighty close)

And personally, I use LABEL, rather than UUID, on all hard drives and thumb drives.
Others prefer UUID.
Which is "obvious"?
Which is "useful"?
Is your way better?
Is my way better?

and as being "unreasonable nor lazy"... where does that come from?
I don't see anybody accusing you of this...
GUI's don't always give the fine-grained control, or low-level access, that is needed for some operations under Linux, which is why they are sometimes by-passed for the command line, NOT because they are a "lazy" way to do things.
(also, the command line is almost exactly the same across almost all the Linux distros... the GUI's vary wildly. So again, GUI's are by-passed)

>  In fact, one could read my initial question as a **non**-lazy question designed to increase my understanding of Linux, which, ***after years of DOS/Windows, isn't exactly what I'm used to***, you're right about that.

BTW, if there **is** a good reason why this is (apparently) so complicated, I did ask for that in my first post and I'd be happy to hear it.

One good reason is that you are not used to it...
You seem to forget the years you spent learning and understanding the Microsoft way of doing things... you had to learn to crawl, then walk, then run...
Now you are starting all over again with Linux...
You have to learn to crawl, then walk, then finally run...


 >  Again, **I want to be productive, but I am still willing to learn**.

In any case, if you could **avoid lecturing me on what "we" should do** as Linux users, I'd really appreciate it.  Thanks.
Eric

You want to learn Linux, but you don't want to be lectured about how we should do things the Linux way?

---

