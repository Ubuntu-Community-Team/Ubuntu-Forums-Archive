---
title: "Transfering files by hard drive, permission issues."
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Shendeair on 2010-12-04
I have Ubuntu (9.10 32-bit) on my current computer.  I am in the process of moving and I wish to transfer all of my documents and media files to a new ubuntu machine (10.10 32-bit) which is already at my new home.  Unfortunately, the two computers are several hundred miles apart so I have no way to network them and I won't be able bring the old computer with me.  The only media I have large enough to fit everything is a separate internal hard drive.

I have struggled with file permissions between separate Ubuntu computers in the past, and I am concerned that I won't be able to access any files which were created on my old computer once I install the disk in the new computer. 

How can I ensure that I will not have this problem?  I partitioned the drive FAT32 (I thought this would be best for sharing), and I have already transferred the files.  When I look at the permissions of the files on this "transfer drive" they all appear to be 'Others - File Access: Read Only'  However, all of the folders which contain the files have  'Others - Folder Access: None' and it won't allow me to change that.  Does this mean I won't be able to open these folders if the drive is physically placed in another computer?

---

### Post by Verbeck on 2010-12-04
you can change the ownership of the files by the following after transferring the files
```
sudo chown -R username:usergroup /path/to/folder
```
it'll change the ownership of all the files in the directory to the user:usergroup specified

---

### Post by gacb on 2011-01-12
Backing up all you files - dejadup is a quick and easy one and restoring them on the new computer should avoid any permission issues.

---

### Post by mikechant on 2011-01-12
If the drive is FAT32 formatted then there are no permissions stored (FAT32 doesn't support them). The only permissions will be those simulated by the mount process.

What this should mean is that if you boot the new machine with the transfer drive attached it should show up in the Ubuntu 'places' menu and then mount automatically with everything accessible when you click on it.

Anyhow, as per above, if have problems you can always access any files using sudo.

---

