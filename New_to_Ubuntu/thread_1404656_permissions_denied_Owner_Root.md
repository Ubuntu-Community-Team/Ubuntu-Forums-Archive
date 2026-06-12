---
title: "permissions denied: Owner Root"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by chuckycheese on 2010-02-11
I partitioned an external HDD with file structure ext3/ext4.  I wanted to move my home dir to it as the current part is too small. However, when I try and do anything with the new part I get an error message I can't write to it.  Under properties>permissions owner: root
admin is not owner, can not change?  I have searched, but can't seem to find anything similar, any help would be appreciated.

---

### Post by mechro on 2010-02-11
You have to set up the correct permissions and edit your /etc/fstab file.

Follow this tutorial...

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

or this one...

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ScottinSoCal on 2010-02-11
As soon as you get it mounted under your home folder, all that will go away.

---

### Post by chuckycheese on 2010-02-11
I have tried both sites, the first terminal tells me vol_id is not a command.   the second one is assuming you have to mount both partitions, I added a partition and it will not let me access it.  I changed the references to the new partition and it will mkdir but not in the new part.  Looking again with file browser the new partition shows up as a folder under >media probably because it is a usb drive.  So still no luck  as I said I did check out the forums first before I posted.

---

### Post by abhishek.malhotra35 on 2010-02-11
What is the command that you used to mount the partitions. Try below link:
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount).

Goto to /media. Do a list using ls -l. If the owner and group is root, change the owner of your usb using chown -R <username>:<group> <foldername>.

---

### Post by Miljet on 2010-02-11
What ScottinSoCal was getting at is that the ownership and permissions of a mounted drive is dependent on who owns the mount point where the drive is attached. Usually an external drive is mounted under /media which is owned by root. But you can create a mount point anywhere you want. If you create a mount point in your home directory and mount the drive there, you will own the mount point, and therefore the drive. Do not use sudo to create the mount point though or it will still belong to root, even though it is created in your home directory.

The down side to doing this is that you will be the only one who can mount the drive or access it. So this is not a good idea if you have multiple users.

---

### Post by abhishek.malhotra35 on 2010-02-11
> **Miljet said:**
> The down side to doing this is that you will be the only one who can mount the drive or access it. So this is not a good idea if you have multiple users.

I think this can be solved by creating a common group having all users that require access to this and change group permission of the folder for that group.

---

### Post by samantha_ on 2010-02-11
mount it using /etc/fstab.

what does
```

sudo fdisk -l

```
and 
```

sudo blkid

```
output?

blkid should output your partitions with the UUIDS.
identify the parition that the drive is on. copy the UUID of the partition (the stuff between the brackets)

add this to /etc/fstab (after changing the UUID.)(and adding your ubuntu username)
```
UUID=be35a709-c787-4198-a903-d5fdc80ab2f8  /home/***username***  ext3  relatime,errors=remount-ro  0  1
```

Im assuming you only moved your home directory (/home/username) but not your entire /home. also assuming your using ext3

Now, this part im not sure.
The permissions should work properly, but if they dont, you might want to do
```

sudo chown ***username*** -R /home/***username***
```

---

### Post by chuckycheese on 2010-02-11
ok..... did a mount -l and it shows up as mounted /dev/sdb2
did chown and got  : operation not permitted
soooo, I tried to remount the drive and got  :  only root can do that
nexy
t?

---

### Post by Mustard on 2010-02-11
> **chuckycheese said:**
> ok..... did a mount -l and it shows up as mounted /dev/sdb2
did chown and got  : operation not permitted
soooo, I tried to remount the drive and got  :  only root can do that
nexy
t?

An actual copy and paste of the inputing of the above commands and the resultant output of each command would help greatly.

The errors above look more like user input error atm.  Without seeing whats on your screen, its hard to tell.

---

### Post by amac777 on 2010-02-11
> **Miljet said:**
> 
The down side to doing this is that you will be the only one who can mount the drive or access it. So this is not a good idea if you have multiple users.

Because the drive is ext3, this does not apply. Permissions are fully supported on ext3. If you want a user to have access to a directory on the drive, just create a directory on that drive and set its permissions.

---

### Post by chuckycheese on 2010-02-11
adminstrator@latitude600:~$ cd /media
adminstrator@latitude600:/media$ ls -l
total 38
lrwxrwxrwx 1 root         root             6 2009-12-02 12:20 cdrom -> cdrom0
dr-xr-xr-x 4   4294967295   4294967295   136 2007-07-05 05:43 cdrom0
drwx------ 4 adminstrator adminstrator 32768 1969-12-31 18:00 My Book
drwxr-xr-x 3 root         root          4096 2010-02-11 13:49 _mybook_linux
adminstrator@latitude600:/media$ chown -R administrator:/media/_mybook_linux
chown: missing operand after `administrator:/media/_mybook_linux'
Try `chown --help' for more information.
adminstrator@latitude600:/media$ chown --help
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...
  or:  chown [OPTION]... --reference=RFILE FILE...
Change the owner and/or group of each FILE to OWNER and/or GROUP.
With --reference, change the owner and group of each FILE to those of RFILE.

  -c, --changes          like verbose but report only when a change is made
      --dereference      affect the referent of each symbolic link (this is
                         the default), rather than the symbolic link itself
  -h, --no-dereference   affect each symbolic link instead of any referenced
                         file (useful only on systems that can change the
                         ownership of a symlink)
      --from=CURRENT_OWNER:CURRENT_GROUP
                         change the owner and/or group of each file only if
                         its current owner and/or group match those specified
                         here.  Either may be omitted, in which case a match
                         is not required for the omitted attribute.
      --no-preserve-root  do not treat `/' specially (the default)
      --preserve-root    fail to operate recursively on `/'
  -f, --silent, --quiet  suppress most error messages
      --reference=RFILE  use RFILE's owner and group rather than
                         specifying OWNER:GROUP values
  -R, --recursive        operate on files and directories recursively
  -v, --verbose          output a diagnostic for every file processed

The following options modify how a hierarchy is traversed when the -R
option is also specified.  If more than one is specified, only the final
one takes effect.

  -H                     if a command line argument is a symbolic link
                         to a directory, traverse it
  -L                     traverse every symbolic link to a directory
                         encountered
  -P                     do not traverse any symbolic links (default)

      --help     display this help and exit
      --version  output version information and exit

Owner is unchanged if missing.  Group is unchanged if missing, but changed
to login group if implied by a `:' following a symbolic OWNER.
OWNER and GROUP may be numeric as well as symbolic.

Examples:
  chown root /u        Change the owner of /u to "root".
  chown root:staff /u  Likewise, but also change its group to "staff".
  chown -hR root /u    Change the owner of /u and subfiles to "root".

Report chown bugs to [email]bug-coreutils@gnu.org[/email]
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
Report chown translation bugs to <http://translationproject.org/team/>
adminstrator@latitude600:/media$ chown -R admistrator /media
chown: invalid user: `admistrator'
adminstrator@latitude600:/media$ chown -R administrator /media
chown: invalid user: `administrator'
adminstrator@latitude600:/media$ chown -R adminstrator /media
chown: cannot read directory `/media/_mybook_linux/lost+found': Permission denied
chown: changing ownership of `/media/_mybook_linux': Operation not permitted
chown: changing ownership of `/media/cdrom': Operation not permitted
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VIDEO_TS.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VIDEO_TS.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VIDEO_TS.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_01_0.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_01_0.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_01_1.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_01_0.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_02_0.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_02_0.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_02_1.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_02_0.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_03_0.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_03_0.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_03_1.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_03_2.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_03_0.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_04_0.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_04_0.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_04_1.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_04_2.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_04_0.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_05_0.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_05_0.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_05_1.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_05_2.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_05_0.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_06_0.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_06_0.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_06_1.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_06_2.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_06_3.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_06_0.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_07_0.IFO': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_07_0.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_07_1.VOB': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS/VTS_07_0.BUP': Read-only file system
chown: changing ownership of `/media/cdrom0/VIDEO_TS': Read-only file system
chown: changing ownership of `/media/cdrom0/AUDIO_TS': Read-only file system
chown: changing ownership of `/media/cdrom0': Read-only file system
chown: changing ownership of `/media': Operation not permitted
adminstrator@latitude600:/media$ chown -R adminstrator /_mybook_linux
chown: cannot access `/_mybook_linux': No such file or directory
adminstrator@latitude600:/media$ chown -r adminstrator /media/_mybook_linux
chown: invalid option -- 'r'
Try `chown --help' for more information.
adminstrator@latitude600:/media$ chown -R admimstrator /media/_mybook_linux
chown: invalid user: `admimstrator'
adminstrator@latitude600:/media$ chown -R adminstrator /media/_mybook_linux
chown: cannot read directory `/media/_mybook_linux/lost+found': Permission denied
chown: changing ownership of `/media/_mybook_linux': Operation not permitted
adminstrator@latitude600:/media$ chown --help
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...
  or:  chown [OPTION]... --reference=RFILE FILE...
Change the owner and/or group of each FILE to OWNER and/or GROUP.
With --reference, change the owner and group of each FILE to those of RFILE.

  -c, --changes          like verbose but report only when a change is made
      --dereference      affect the referent of each symbolic link (this is
                         the default), rather than the symbolic link itself
  -h, --no-dereference   affect each symbolic link instead of any referenced
                         file (useful only on systems that can change the
                         ownership of a symlink)
      --from=CURRENT_OWNER:CURRENT_GROUP
                         change the owner and/or group of each file only if
                         its current owner and/or group match those specified
                         here.  Either may be omitted, in which case a match
                         is not required for the omitted attribute.
      --no-preserve-root  do not treat `/' specially (the default)
      --preserve-root    fail to operate recursively on `/'
  -f, --silent, --quiet  suppress most error messages
      --reference=RFILE  use RFILE's owner and group rather than
                         specifying OWNER:GROUP values
  -R, --recursive        operate on files and directories recursively
  -v, --verbose          output a diagnostic for every file processed

The following options modify how a hierarchy is traversed when the -R
option is also specified.  If more than one is specified, only the final
one takes effect.

  -H                     if a command line argument is a symbolic link
                         to a directory, traverse it
  -L                     traverse every symbolic link to a directory
                         encountered
  -P                     do not traverse any symbolic links (default)

      --help     display this help and exit
      --version  output version information and exit

Owner is unchanged if missing.  Group is unchanged if missing, but changed
to login group if implied by a `:' following a symbolic OWNER.
OWNER and GROUP may be numeric as well as symbolic.

Examples:
  chown root /u        Change the owner of /u to "root".
  chown root:staff /u  Likewise, but also change its group to "staff".
  chown -hR root /u    Change the owner of /u and subfiles to "root".

Report chown bugs to [email]bug-coreutils@gnu.org[/email]
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
Report chown translation bugs to <http://translationproject.org/team/>
adminstrator@latitude600:/media$ chown -R adminstrator:adminstrator /_mybook_linux 
chown: cannot access `/_mybook_linux': No such file or directory
adminstrator@latitude600:/media$ chown -R adminstrator:adminstrator /media/_mybook_linux
chown: cannot read directory `/media/_mybook_linux/lost+found': Permission denied
chown: changing ownership of `/media/_mybook_linux': Operation not permitted
adminstrator@latitude600:/media$ ls -l
total 38
lrwxrwxrwx 1 root         root             6 2009-12-02 12:20 cdrom -> cdrom0
dr-xr-xr-x 4   4294967295   4294967295   136 2007-07-05 05:43 cdrom0
drwx------ 4 adminstrator adminstrator 32768 1969-12-31 18:00 My Book
drwxr-xr-x 3 root         root          4096 2010-02-11 13:49 _mybook_linux
adminstrator@latitude600:/media$ chown adminstrator:adminstrator /media/_mybook_linux
chown: changing ownership of `/media/_mybook_linux': Operation not permitted
adminstrator@latitude600:/media$ chown adminstrator /media/_mybook_linix
chown: cannot access `/media/_mybook_linix': No such file or directory
adminstrator@latitude600:/media$ chown adminstrator /media/_mybook_linux
chown: changing ownership of `/media/_mybook_linux': Operation not permitted
adminstrator@latitude600:/media$ mount -l
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/adminstrator/.Private on /home/adminstrator type ecryptfs (ecryptfs_sig=7f21a34cceffbaf3,ecryptfs_fnek_sig=6ebb9397d437cede,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/adminstrator/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adminstrator)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=adminstrator) [DEXTER_S1_D1]
/dev/sdb2 on /media/_mybook_linux type ext2 (rw,nosuid,nodev,uhelper=devkit) [/mybook/linux]
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush) [My Book]
adminstrator@latitude600:/media$ chown -R adminstrator /dev/sdb2
chown: changing ownership of `/dev/sdb2': Operation not permitted
adminstrator@latitude600:/media$ chown -R adminstrator:adminstrator /dev/sdb2
chown: changing ownership of `/dev/sdb2': Operation not permitted
adminstrator@latitude600:/media$ mount -t ext3 /dev/sdb2
mount: only root can do that
adminstrator@latitude600:/media$ cd /
adminstrator@latitude600:/$ sudo fdisk -l
[sudo] password for adminstrator: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61330bae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9074    72886873+   7  HPFS/NTFS
/dev/sda2            9075        9729     5261287+   5  Extended
/dev/sda5            9075        9694     4980118+  83  Linux
/dev/sda6            9695        9729      281106   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           30523       60801   243216067+   c  W95 FAT32 (LBA)
/dev/sdb2               1       30522   245167933+  83  Linux

Partition table entries are not in disk order
adminstrator@latitude600:/$ sudo blkid
/dev/sda1: UUID="8C085B59085B417E" TYPE="ntfs" 
/dev/sda5: UUID="1662cf3d-b81a-4609-98bf-cad89d9e5577" TYPE="ext4" 
/dev/sda6: UUID="f5b78002-83e9-4c00-bd21-7ee67536e045" TYPE="swap" 
/dev/sdb1: LABEL="My Book" UUID="907C-E2E9" TYPE="vfat" 
/dev/sdb2: LABEL="/mybook/linux" UUID="278c5441-2313-4b17-a051-91fd888f7335" TYPE="ext2" 
adminstrator@latitude600:/$ /etc/fstab UUID=278c5441-2313-4b17-a051-91fd888f7335 /home/adminstrator ext2 realtime.errors+remount-ro  O  1
bash: /etc/fstab: Permission denied
adminstrator@latitude600:/$

---

### Post by Mustard on 2010-02-11
Thats great!

Now pause while the mess is deciphered. :D

---

### Post by Mustard on 2010-02-11
I have to say...its just plain scary seeing what you were typing in.

One false move and it could have been reinstall time. :D

A big issue is that you had the syntax wrong for the chown command until very close to the end.  I'm not sure whats going on with trying to change the permissions of a file on a read only media (the CD in the cdrom), that would never work, as you can't write to a CD.

-edit-

Honestly, I'm afraid to touch this one. I'm not sure which tutorial you are working from, nor do I know what step in the tutorial you are up to.

---

### Post by abhishek.malhotra35 on 2010-02-11
I think you are trying to change the permission of _mybook_linux directory.
Do
cd /media
sudo chown adminstrator:adminstrator _mybook_linux
Using sudo you will be asked for password.

If the directory or file is owned by user other than you, you need either root or that user credentials to change permissions.

---

### Post by chuckycheese on 2010-02-11
I started with the first link I was referred to, then the second, then the commands that were posted, then the last link, and finally ended up with the commands from samantha.  I thought I was in the right forum, but I couldn't find one for complete idiots. ;)

---

### Post by chuckycheese on 2010-02-11
adminstrator@latitude600:/$ cd /media
adminstrator@latitude600:/media$ sudo chown _mybook_linux
chown: missing operand after `_mybook_linux'
Try `chown --help' for more information.
adminstrator@latitude600:/media$

oops

adminstrator@latitude600:/media$ sudo chown adminstrator:adminstrator _mybook_linux
adminstrator@latitude600:/media$

---

### Post by Mustard on 2010-02-11
> **abhishek.malhotra35 said:**
> I think you are trying to change the permission of _mybook_linux directory.
Do
cd /media
sudo chown adminstrator:adminstrator _mybook_linux
Using sudo you will be asked for password.

If the directory or file is owned by user other than you, you need either root or that user credentials to change permissions.

Thats not bad..but I think the path to the external partition is 

```
sudo chown adminstrator:adminstrator /media/_mybook_linux
```

the only problem being that it said it didnt exist, which makes me wonder whether its actually mounted atm or even exists atm..has the directory /media/_my_linux been created?

---

### Post by Mustard on 2010-02-11
> **chuckycheese said:**
> adminstrator@latitude600:/$ cd /media
adminstrator@latitude600:/media$ sudo chown _mybook_linux
chown: missing operand after `_mybook_linux'
Try `chown --help' for more information.
adminstrator@latitude600:/media$

yeah..what you are typing and whats on the screen are two different things atm.  We have to get past that problem.

---

### Post by chuckycheese on 2010-02-11
Thanks that last worked once I got it typed in right. Curious, what does "atm" mean?

---

### Post by Mustard on 2010-02-11
> **chuckycheese said:**
> Thanks that last worked once I got it typed in right. Curious, what does "atm" mean?

atm = at the moment

---

### Post by samantha_ on 2010-02-12
> **chuckycheese said:**
> Thanks that last worked once I got it typed in right. Curious, what does "atm" mean?

alright. now that you got it working, Copy your home folder (/home/username) over to the ext3 partition. follow the instructions at my first post in this thread to permantly mount it. (and yes, the post I made was for AFTER you managed to fix the permissions. I decided to take a break before sleeping by watching ghost whisperer, so i didnt get a chance to tell you that.) and please make sure you type the fstab line exactly the way it is written, w/ the specified edits. you might find out you can login to root/recovery mode if you dont. [goodnight]

---

