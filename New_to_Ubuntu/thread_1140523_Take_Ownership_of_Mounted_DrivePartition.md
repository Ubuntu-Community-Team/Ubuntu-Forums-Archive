---
title: "Take Ownership of Mounted Drive/Partition?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by dmaxel on 2009-04-27
I've been having some problems taking ownership of a newly added hard drive. Here is all the information I can provide:

[LIST]
[*]The computer is running Ubuntu 8.10 Desktop Edition, and is meant to become a home server with Samba.
[*]Samba is working without any problems.
[*]The drives have been configured to mount automatically.
[*]I am unable to write any files onto the drive, which is made of a single FAT32 partition.
[*]It appears we don't have permission to write files.
[*]When right-clicking the drive --> Properties --> Permissions, it says "The permissions of 'Hard_Drive_Name' cannot be determined."
[*]I have tried to use sudo chown -R USERNAME:USERNAME /media/Hard_Drive_Name, but an error shows up saying: chown: changing ownership of '/media/Hard_Drive_Name': Operation Not Permitted
[/LIST]
I do hope that's all the information needed for my situation. I am also not sure if the ownership should belong to just the username the machine will run on, or if it should add every user accessing it over Samba.

---

### Post by miwaypet on 2009-04-27
Sounds to me like it does not find your name as owner of the drive. 

Is the drive listed in /etc/fstab

If so, unmount the drive. Then:

Open terminal: **sudo mount-a**

Then: **sudo chown -R <yourname>:<youname> /HardDrive**

Then: **sudo chmod -R 755 /HardDrive**

Should help. You may have left off the last one. Important for rw permissions for everyone.

---

### Post by ptn107 on 2009-04-27
I don't think you can mess with Linux permissions on a drive that is formatted 'fat32'.  You may have to format the drive ext3 before you can 'chown' it.

---

### Post by dmaxel on 2009-04-27
> **miwaypet said:**
> Sounds to me like it does not find your name as owner of the drive. 

Is the drive listed in /etc/fstab

If so, unmount the drive. Then:

Open terminal: **sudo mount-a**

Then: **sudo chown -R <yourname>:<youname> /HardDrive**

Then: **sudo chmod -R 755 /HardDrive**

Should help. You may have left off the last one. Important for rw permissions for everyone.
Amazingly enough, we ran into problems mounting when we tried to set it up that it mounts automatically. Now it won't let me unmount without having to change the /etc/fstab file again, and removing the lines.
> **ptn107 said:**
> I don't think you can mess with Linux permissions on a drive that is formatted 'fat32'.  You may have to format the drive ext3 before you can 'chown' it.So which would still be better when using the drives to host files that Windows machines access through Samba, fat32 or ext3?

---

### Post by Didius Falco on 2009-04-27
Here you go:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

That will have you using your drive in no time. 

Bookmark this page, too. It's like having an expert on 24 hour call.

[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

I hope this helps...

---

### Post by miwaypet on 2009-04-27
Take a look at this post by [Tombutu]("http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/").

May be better to format to ext3.

---

### Post by Miljet on 2009-04-27
I'll answer your last question first. If you have any Windows machines, they will not be able to read EXT3. Most people use NTFS for shared files with Windows. If, on the other hand, all machines are Linux, EXT3 is the way to go.

I have been playing around with a similar situation as I learn. One thing I learned is that permissions are set when the drive is mounted.

I wound up creating a blank directory in my home directory and mounted the drive there. Bingo! All files are accessible for read and write. In other words, the new disk is at /home/jack/files.

---

