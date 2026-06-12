---
title: "permissions will not allow access to files I moved"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by larryweeks on 2008-12-15
I backed up files and replaced them, manually, this was a directory copy. I cannot use them as it says they are root:root
I try to change permissions and am not allowed. I try to change permissions from a startup and cannot get any editor to work, says that it cannot initialize video or some such.
I have tried every way I know and searched out. None are working. 
I know that it should give me root but will not. It worked initially when I loaded the system. I do not want to have to remove all of this. Even my backup home directory which I keep on a second drive acts the same and shows the same permissions. What Next??

---

### Post by Pconfig on 2008-12-15
Open op gnome-terminal
The cd to you backup directory
Then use this command

sudo chown YOUR_USERNAME DIRECTORY -R

That should get you started

---

### Post by Coreigh on 2008-12-15
to restore file ownership
```

sudo chown -R username.username /pathto/folder

```

Be sure you are only changing ownership on files that are yours. In other words if they were in your home folder.

it is even safer to do this file by file instead of by whole folders.

---

### Post by larryweeks on 2008-12-15
The  directory is this /home/larry/websites
websites is the directory I need to change it is showing root:root

Somehow it will not do that I have tried all the commands. 

But i finally got it the command is as follows...sudo chown root:larry websites -R

Thanks for the help

---

### Post by Paqman on 2008-12-15
> **larryweeks said:**
> 
But i finally got it the command is as follows...sudo chown root:larry websites -R


If your username is larry then you should probably do:
```
sudo chown -R larry:larry /home/larry/websites
```

Why? Well you want the file to be owned by the user larry, as well as the group larry (each user is a little one-person group by themselves)

By default the user who owns a file can do anything to it, while the group members can only read the file. Setting chown root:larry will allow you to read the file no problem, but chown larry:larry gives you full access.

---

### Post by Achetar on 2008-12-15
Another thing. Never copy files that require permissions to work properly to and from an NTFS or FAT/FAT32 partition. The files will lose all permission settings. For backups use an ext2/3/4, reiser3/4, or XFS partition.

---

