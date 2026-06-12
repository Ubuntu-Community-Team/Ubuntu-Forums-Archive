---
title: "Getting 777 file access with SMB"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by mariourk on 2008-08-27
Here is my situation. We have a few people working with Ubuntu machines. They save their file on an [Xserve](http://en.wikipedia.org/wiki/Xserve) This server is running Samba to share files via the SMB-protocol. The Ubuntu users use this to save and load their files to and from the server. So far, so good.

They use the build-in Nautilus way to connect to the server. When they do this, files are stored with 777 file-acces right. This is a good thing, because our pre-press department can open those files from the server and edit them on their [G5's](http://en.wikipedia.org/wiki/Power_Mac_G5). They have no trouble with file access what-so-ever.

The problem is that the Nautilus way doesn't always work, especially with other programs. OpenOffice Writer, one of the most used programs, for example. Sometimes when the Ubuntu users try op open or save a file to the server, they get a popup window, asking to enter the password for the Guest-acount. Click [here](http://www.winterfell.nl/images/foutmelding.png) for an example. No password is accepted is the right one.

One solution for this is mounting the share the old fashion way, in /etc/fstab. The problem is, when I do that, that all files are stored ar *rwxr-xr-x*. And this is a problem for the G5 users. Suddenly they cannot edit the files anymore, because they have no write-access to the files. Even worse is that the userid's in the Ubuntu workstations and the Xserve are not the same. So, once a file is saved on the server, they cannot edit or delete that file, because they aren't the owner.

Does anyone know a solution to this problem? It's driving me crazy. :(

---

### Post by arch0njw on 2008-08-28
I have run into SMB+OO.org issues before.  So I have to pass on being able to offer any direct response to that.

However, if you mount the share in your fstab, use the "umask=000" option.  I always get confused with that setting, but it is like a negative setting.  That effectively mounts the drive so you will create files with 777 permit.  For example, the following is how I mount my ntfs drive under Kubuntu:

UUID=B0403F13403EDFB0 /media/winxp     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1


HTH

---

