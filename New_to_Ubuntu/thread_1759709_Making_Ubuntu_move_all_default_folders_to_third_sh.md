---
title: "Making Ubuntu move all default folders to third shared partition"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by shin333 on 2011-05-16
I currently have Ubuntu 10.04 installed. I am dual botting Vista and Ubuntu. I have two seperated partitions for the OS and a third partition that I'm using to share files between the two OS. So far, I've been able to change the default folders (like documents and program files) in Vista into my third shared partition so that my OS partitions contain only my OS and nothing else. I'm trying to do the same with Ubuntu but I have no idea how to do that since I'm completely new to linux. I tried looking it up on the internet and found how to do it on Windows but not on Ubuntu. To be honest, I'm not too sure what keywords I should be using to look up my issue. I'm hoping someone here can help me. I'm trying to get Ubuntu to save all downloads, programs and documents in the third shared partition. Help!

---

### Post by Plueonic on 2011-05-16
It wont be possible to install programs on the shared partition but you could make use of symbolic links to link to folders/files. To do that, middle click and drag&drop a folder on that partition to your home directory > select 'link here' from the context menu.

Edit: To make sure the links work on every boot, you'll have to set a permanent mount point and automatically mount it by adding a line in /etc/fstab. There is a full how to on the [ubuntu wiki]("https://help.ubuntu.com/community/Fstab"), but we could guide you if you post the output of *sudo blkid* or *sudo fdisk -l* from a terminal window.

---

### Post by shin333 on 2011-05-16
shin@shin-laptop:~$ sudo blkid
/dev/sda1: UUID="E858CB9A58CB65C2" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="2C88743C8874071C" TYPE="ntfs" 
/dev/sda4: UUID="7959580231A88130" TYPE="ntfs" 
/dev/sda5: UUID="e2d282f8-d8e3-4130-972d-eb32b6672a27" TYPE="swap" 
/dev/sda6: UUID="9003ba80-4181-4793-82f0-87564d85b97c" TYPE="ext4" 


shin@shin-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d8fa327

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4038    32435202+   7  HPFS/NTFS
/dev/sda2           37390       38913    12241530    7  HPFS/NTFS
/dev/sda3            4039        7907    31075262+   5  Extended
/dev/sda4            7907       37389   236816582+   7  HPFS/NTFS
/dev/sda5            4039        4920     7084633+  82  Linux swap / Solaris
/dev/sda6            4921        7907    23990272   83  Linux


Sorry. I don't understand the purpose of symbolic links. I'm also not sure why I'm not able to install things on the shared partition when I could do it in Vista. Perhaps I'm not explaining it clearly?

---

### Post by Plueonic on 2011-05-16
> **shin333 said:**
> 
Sorry. I don't understand the purpose of symbolic links.
Symbolic links would act similar to shortcuts so making a link of (/media/datapartition/Downloads) in your home directory would save all data put in /home/user/Downloads on /media/datapartition/Downloads. There are alternatives such as setting firefox/any application to save files directly on the partition, so using links are just a suggestion since the home folder is the default place for storing the user data. 
> **shin333 said:**
> 
 I'm also not sure why I'm not able to install things on the shared  partition when I could do it in Vista. Perhaps I'm not explaining it  clearly?
There are two things that gets in the way of installing programs there;
1) Its formatted as ntfs which doesn't follow linux permissions (This also prevents mounting the partition directly as /home/user as there are some files there that need specific properties)
2) Programs are not installed on a central location that is set in the installer as in windows - default C:/Program files/app name/
(For example, the configuration files are stored in /etc while system wide preferences are usually in /usr/share)

---

### Post by shin333 on 2011-05-16
Ah I understand now. I guess I should have made a /home partition. I just thought I could get Ubuntu to install everything on the shared partition. 

I was hoping you could explain the part about the mount point? I'm new to ubuntu and have no idea what that is.

---

### Post by Plueonic on 2011-05-16
Assuming /dev/sda4 is the shared partition;
1) Run*  sudo umount /dev/sda4  *to unmount it if its mounted and make the mount point by running  * sudo mkdir /media/Data * (or any other name you'd prefer)

2) Open /etc/fstab as root,* (gksu gedit /etc/fstab)* and add to a new line;```
/dev/sda4    /media/Data    ntfs defaults,uid=1000,gid=1000    0    0
```[I]or
[/I]```
UUID=7959580231A88130    /media/Data    ntfs defaults,uid=1000,gid=1000    0    0
```To find your uid and gid, use the command*, id. (*1000 is the default for the first user)

3) Run* sudo mount -a *or reboot to apply the changes

Edit: There should be two program called *ntfs-config *and* pysdm* available in the software-center that provides a gui for all that, but I don't know how well it works..Try them if you're having trouble configuring the files manually

---

