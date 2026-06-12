---
title: "Accessing a data partition"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by mijdrawoh on 2011-08-28
I have a dual boot configuration with Ubuntu 11.04 and another Linux distro on separate SATAs. When I installed Natty, I created a data partition on the Ubuntu SATA in NTFS format for backup of data from the other distro and, I thought, the 11.04 home partition. My problem - I can't find the data partition in Places and can't copy to that partition in 11.04. I can access it from the other distro and copy to it, and it's there in gparted. Is the format preventing me from using that partition in Ubuntu? What actions do I need to take to get access to that partition?

---

### Post by Morbius1 on 2011-08-28
Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```

---

### Post by mijdrawoh on 2011-08-28
The requested data:

murgatroyd@murgatroyd-desktop:~$ sudo blkid -c /dev/null
[sudo] password for murgatroyd: 
/dev/sda1: UUID="2992f38f-4696-43fd-b2b7-6954a7691920" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="31a42aee-7500-43c9-a74c-9e5a36f3be88" TYPE="swap" 
/dev/sda3: LABEL="home" UUID="4bdc45d0-57f8-4753-9b42-19fa28dec5d0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="adata" UUID="2C974A1E4252E4E2" TYPE="ntfs" 
/dev/sdb1: UUID="cd2695c1-654d-4eac-8464-e55949739145" TYPE="ext4" 
/dev/sdb5: UUID="9c5ac52a-b47e-4874-8842-327727a0c667" TYPE="swap" 
/dev/sdb6: UUID="5c6c7618-4e8e-46be-9fe2-43b3c2b68a8e" TYPE="ext4" 
/dev/sdb7: LABEL="datac" UUID="778DCC7C7960038F" TYPE="ntfs" 
murgatroyd@murgatroyd-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=cd2695c1-654d-4eac-8464-e55949739145 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc6 during installation
UUID=5c6c7618-4e8e-46be-9fe2-43b3c2b68a8e /home           ext4    defaults        0       2
# /windows was on /dev/sdc7 during installation
UUID=778DCC7C7960038F /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=8a7bc69b-ac34-4926-bdad-9a584d6d0f53 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=8f5d5852-bdd0-4572-be9d-49aea2848945 none            swap    sw              0       0
# swap was on /dev/sdb4 during installation
UUID=a3dc3bdd-0f34-416a-ba8e-df1274b05edd none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=9c5ac52a-b47e-4874-8842-327727a0c667 none            swap    sw              0       0
murgatroyd@murgatroyd-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb6 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/murgatroyd/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=murgatroyd)
murgatroyd@murgatroyd-desktop:~$

---

### Post by Morbius1 on 2011-08-28
You have 2 ntfs partitions:
> /dev/sda5: LABEL="adata" UUID="2C974A1E4252E4E2" TYPE="ntfs" 
/dev/sdb7: LABEL="datac" UUID="778DCC7C7960038F" TYPE="ntfs" One of which is being auto mounted in fstab:
> UUID=778DCC7C7960038F /windows ntfs defaults,umask=007,gid=46 0 0From the "mount " command it doesn't seem to be mounting however so run the following command:
```
 sudo mount -a
```
Post any errors and then run this command to access the partition:
```
nautilus /windows
```It should open up to that partition.

If you want the other ntfs partition to auto mount then just repeat the same entry in fstab with a different mount point:
```
 sudo mkdir /DataA
```Then add the following to the end of /etc/fstab:
```
UUID=2C974A1E4252E4E2 /DataA ntfs defaults,umask=007,gid=46 0 0

```Then mount the new partition:
```
sudo mount -a
```

---

### Post by mijdrawoh on 2011-08-28
Thanks for your help, Morbius1.

I ran the sudo mount -a command and the nautilus /windows commands without errors and was able to access the windows partition. However, the windows partition still does not appear in Places and I cannot copy to it. Defying logic perhaps, considering it is shown as a swap partition in fstab, the adata partition from the other SATA does appear in Places and I can access it without any problem. Should I recreate the datac (windows) partition and reboot?

---

### Post by oldfred on 2011-08-28
Ignore the comments in fstab, they are just for reference and are the devices when installed, but in your case they all seem to have changed drive number and many are invalid.

You do not seem to be mounting the swap in sda2 or UUID ' 31a....'. But you still are using the swap in sdb5 or UUID ' 9c5...' You do not have to mount both.
All the other swaps you are trying to mount look like old partitions and can just be deleted from fstab.

If you did not copy & paste Morbius1 commands or used your own mount names and was not exactly consistent in using those names(including caps) then you may have issues.

---

### Post by mijdrawoh on 2011-08-28
I copied and pasted the commands, rebooted and checked for datac in Places. It wasn't there; I can only access it through the terminal command. As a side note, when I run the other distro, I can open, read and copy to datac. Should I re-install 11.04?

---

### Post by oldfred on 2011-08-28
Because you are mounting / (root) so you see your partitions if you use Nautilus to open Computer, then file system?

Generally mounts in /media or /home show in the left panel, but often show twice one the actual mount and another that will not work since it is already mounted.

---

### Post by Morbius1 on 2011-08-28
Partitions in fstab never show up in Places - never have.

Run the following command:
```
nautilus /windows
```When nautilus opens Bookmark it: Bookmarks > add Bookmark

As for not being able to copy to it I have no idea. Based on this line in fstab:
>                               UUID=778DCC7C7960038F /windows ntfs defaults,umask=007,gid=46 0 0                      Root and every memeber of the plugdev group ( i.e., gid=46 ) should have write access so you must not be a member of the plugdev group. Add yourself:
```
sudo gpasswd -a your-user-name plugdev
```Then logout and log in again.

---

