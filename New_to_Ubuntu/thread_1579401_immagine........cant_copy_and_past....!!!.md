---
title: "immagine........cant copy and past....!!!"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by mountdiat on 2010-09-21
i cant move any thing to any partition
when i install abuntu...i make 5 partitions one of them is root  the others are ex4
please help

---

### Post by LinuxPhreak on 2010-09-21
If I understand you correctly you have made additional partitions in your Ubuntu Installation. And your having trouble copying content to them. 

I don't think you gave enough information but I will try my best to give some advice. 

If you don't see an icon of a hard drive on your desktop this may be your problem. This usually means that it isn't mounted. You can mount it by going to Places > Computer. Then you right click on the hard drive you want to mount and select mount from the menu. 

You can also go to System > Adminstration > Disk Utility and mount it threw threw their. 

Yet another method would be to open up the terminal and type the following. 

```
sudo mount /dev/sda5
``` or replace sda5 with the drive you want to mount. 

Once the drive is mounted you should be able to click on it from the desktop. A window will open up. Then navigate to the other location and copy and paste from that location to the next. 

To copy from the terminal type the following.

```
cp /my/location/file.odt /new/location/file.odt
```

If your trying to copy and paste something from Windows to Ubuntu inside of a dual boot system you will need to install third partie drivers to make Windows reconize the ext4 partitions. You can get it at [Source Forge]("http://sourceforge.net/projects/ext2read/files/Ext2read%20Version%202.2%20%28Latest%29/ext2explore-2.2.71.zip/download")

---

### Post by bradleypariah on 2010-09-21
Also, if you're trying to paste to certain directories, you are not allowed to paste to them without root privileges.  
To open a root-enabled window, open the run command, usually Alt+F2
```
gksudo nautilus
```
Enter your password.
The new window that appears will allow you to cut and paste to your heart's desire.
-BUT!-
Before you do, make sure you've thought about why the partition didn't want to let you do that to begin with.

__________________________________________

Possibilites:
The files you're trying to move are protected.
The directories are not meant to be moved.
The target directories should not have anything in them besides what's in them now.

---

### Post by mountdiat on 2010-09-21
> **bradleypariah said:**
> Also, if you're trying to paste to certain directories, you are not allowed to paste to them without root privileges.  
To open a root-enabled window, open the run command, usually Alt+F2
```
gksudo nautilus
```Enter your password.
The new window that appears will allow you to cut and paste to your heart's desire.
-BUT!-
Before you do, make sure you've thought about why the partition didn't want to let you do that to begin with.

__________________________________________

Possibilites:
The files you're trying to move are protected.
The directories are not meant to be moved.
The target directories should not have anything in them besides what's in them now.
yes they are all empty
is home the only i can modefi ..if yes ....how can i make all partitions home..??

---

### Post by mountdiat on 2010-09-21
the only folder in them is :lost +found;

---

### Post by mountdiat on 2010-09-21
the only folder in them is :lost +found;

---

### Post by LinuxPhreak on 2010-09-21
> **mountdiat said:**
> the only folder in them is :lost +found;

:lost + found you mean .Trash-1000 which usually is a hidden file that stores things you delete on drive.

---

### Post by mountdiat on 2010-09-21
> **LinuxPhreak said:**
> :lost + found you mean .Trash-1000 which usually is a hidden file that stores things you delete on drive.
yes........but how can i make them home?..all these space free:confused:

---

### Post by mountdiat on 2010-09-21
> **mountdiat said:**
> yes........but how can i make them home?..all these space free:confused:
how please?

---

### Post by jtarin on 2010-09-21
Are you saying you _cannot access_ them? If the answer is _yes_ and _you can see them _you will need to change the permissions them. Because at this time you are not the owner or in that group that has permission to change them.

---

