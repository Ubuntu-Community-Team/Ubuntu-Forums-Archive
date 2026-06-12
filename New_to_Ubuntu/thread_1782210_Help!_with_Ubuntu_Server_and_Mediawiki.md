---
title: "Help! with Ubuntu Server and Mediawiki"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by edisonmax on 2011-06-14
Hi, ok heres where i am:

I have installed Ubuntu Server with LAMP, on a virtual machine on VMware Fusion. (VMware is installed on my mac)

Now this is the point where i am stuck; i want to install MediaWiki. I have saved the Mediawiki file to a usb stick.  I have books on Mediawiki and read many webpages, and have read that i need to move or extract the file to a directory but i do not know how to do this. **How do you move a file which is on a usb stick into the correct directory??**


I dont know my way round the BASH linux command line interface either so i dont know how to access the directories, so if someone could tell me how to navigate around BASH (i think thats what its called) that would be excellent.

My inability to move this file into the directory is the missing link in my mission to setup my wiki (at least i think thats all that needs to be done), so any help would be most appreciated.

Thanks.

---

### Post by smurphy_it on 2011-06-14
Once you 'insert' the usb stick in your computer, it should auto-mount.  If it does, it should be a matter of opening the icon for it on your desktop, or open a file / window manager.

Thunar comes to mind.  If you are running gnome, you can just select the "places" from the file menu and look for it there.
Once you accomplish that, it's just a matter of coping it over to your system (into the directory you never supplied).

If the directory is not owned by you, then your file manager won't be much help (unless you run a "root file manager, or launch thunar with super-user priviledges)... Such as 
```
Alt-F2, type gksudo thunar
```

Alternatively, if it didn't mount, you might want to do the rest in the command line.  Which isn't too bad....  A command-line book is in my signature if you want a light read.

Basically open a command line shell (usually terminal), type:
```
mount
```
If your usb drive is there, great.. if not, you'll have to mount it.
```
dmesg | grep -i disk
```
To look for it, and most likely it will be something like /dev/sdb1

Once found, you have to mount it somewhere.. following should work:
```
sudo mkdir /media/FLASH
sudo mount /dev/sdb1 /media/FLASH -o rw,user
```

Replace /dev/sdb1 with whatever your flash drive was detected as.

Find the file you want to copy/move, and use sudo to move it.
example:
```
sudo mv /media/FLASH/some.file.txt /opt/freeware/html/
```

---

### Post by edisonmax on 2011-06-14
With regards to the USB, im pretty sure it has mounted; in the VMware settings box for the virtual machine you can click the USB which i think mounts it because as soon as i have done this the usb disappears from the desktop of my mac.

I have no idea how to view or access the USB 


Also can someone tell me how to access the directories as this may be the nub of the problem, i think i have done it before but i cant remeber how

---

### Post by smurphy_it on 2011-06-15
trying opening a command prompt and typing:
```
mount
dmesg | grep [Dd]isk

```

Then paste your info in here.

---

