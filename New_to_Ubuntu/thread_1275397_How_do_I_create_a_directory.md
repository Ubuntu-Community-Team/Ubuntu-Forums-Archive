---
title: "How do I create a directory"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by myolbug on 2009-09-25
I am trying to install World of Warcraft from the DVD ROM and quite frankly, I am stumped.  I am running Jaunty and I have the newest version of WINE and I am trying to follow this [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")
But I don't know how to create a directory, to say, the desktop, as is stated here
> Start the installation by opening a terminal and running these commands:

 cd /<path-to-directory>/
 wine Installer.exe

Replace <path-to-directory/> with the right path to the directory where you copied all the files above. 

Help?

---

### Post by afroman10496 on 2009-09-25
use the ```
mkdir
``` command to create one in the folder your're in.
to move to the one to your desktop, use ```
cd ~/Desktop
``` and then ```
ls
``` to the one your in. then use ```
cd
``` to the one you want listed in the ```
ls
``` command

---

### Post by NoaHall on 2009-09-25
In mine, it would be "/home/noah/Desktop"

In yours, it would be your username in place of mine.

---

### Post by myolbug on 2009-09-25
Nothing

---

### Post by myolbug on 2009-09-25
This is what I get:

> randy@randy-desktop:~$ mkdir
mkdir: missing operand
Try `mkdir --help' for more information.
randy@randy-desktop:~$ 




---

### Post by NoaHall on 2009-09-25
You can't just use mkdir. You have to use 
```
 mkdir /home/$YOURUSERNAME/$NEWFOLDERNAME 
```

---

### Post by myolbug on 2009-09-25
I get this
> randy@randy-desktop:~$ mkdir /home/$randy/$WowInstall
mkdir: cannot create directory `/home//': File exists



---

### Post by MJWitter on 2009-09-25
Hi, you need to type:
> mkdir (name of folder to be created)

---

### Post by NoaHall on 2009-09-25
No no no xD

The "$" is just there to show it's a variable.

so it'd be ```
 mkdir /home/randy/WowInstall
```

---

### Post by myolbug on 2009-09-25
Okay,
I am trying to follow the instructions on the previously linked page.  This is what I am getting thus far.

randy@randy-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
randy@randy-desktop:~$  winecfg
randy@randy-desktop:~$ cd home/randy/WowInstall
bash: cd: home/randy/WowInstall: No such file or directory
randy@randy-desktop:~$ mkdir home/randy/WowInstall
mkdir: cannot create directory `home/randy/WowInstall': No such file or directory
randy@randy-desktop:~$ mkdir /home/randy/WowInstall
mkdir: cannot create directory `/home/randy/WowInstall': File exists
randy@randy-desktop:~$ sudo umount /dev/cdrom
[sudo] password for randy: 
Sorry, try again.
[sudo] password for randy: 
umount: /dev/cdrom: not mounted
randy@randy-desktop:~$  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

randy@randy-desktop:~$ sudo mount /dev/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
randy@randy-desktop:~$ sudo ls /dev/cdrom
/dev/cdrom
randy@randy-desktop:~$  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: /dev/sr0 already mounted or /media/cdrom0/ busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom0
randy@randy-desktop:~$ sudo umount /dev/cdrom
randy@randy-desktop:~$  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

randy@randy-desktop:~$ wine installer.exe
wine: could not load L"C:\\windows\\system32\\installer.exe": Module not found
randy@randy-desktop:~$

---

### Post by myolbug on 2009-09-26
I can't get this to work, The guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

In it it tells me to do this:

 > sudo umount /dev/cdrom
  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/ and 

I get this message:
> [I]randy@randy-desktop:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/I]

Now what?  I am trying to do this step by step and I can't get it to work.

---

