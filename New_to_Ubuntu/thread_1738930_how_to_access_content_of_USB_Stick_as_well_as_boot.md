---
title: "how to access content of USB Stick as well as boot it live?"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by sp.1990 on 2011-04-25
Hi all

I have booted Ubuntu 10.10 via the USB Stick . How to get the contents of the pen drive in which the OS is booted? i could not find any drive in /mnt ( i saw the contents in read mode in fedora in /mnt/live) . So please help me. 

I need to access the content of the USB stick atlease in Read mode. Read-Write mode will also be preferred

---

### Post by grahammechanical on 2011-04-25
When I want to access the drive that I am booted from I just click on Places. File System is where all the system files are located. To look at the rest of the disc I click on the folder with my user name. Or if I have opened File System I click on the folder called Home, and then I click on the folder with my user name. As I am booted from a hard disc I also access the other partitions on the hard drive. Is your USB stick partitioned? I do not understand why you cannot access all the files and folders on the USB stick in the same way that I am accessing all the files and folders on my hard drive. When you have opened the File Manager you can select View and click on Show Hidden Files. And you will see more folders and files. If this is what you are looking for.

Regards.

---

### Post by sp.1990 on 2011-04-25
> **grahammechanical said:**
> When I want to access the drive that I am booted from I just click on Places. File System is where all the system files are located. To look at the rest of the disc I click on the folder with my user name. Or if I have opened File System I click on the folder called Home, and then I click on the folder with my user name. As I am booted from a hard disc I also access the other partitions on the hard drive. Is your USB stick partitioned? I do not understand why you cannot access all the files and folders on the USB stick in the same way that I am accessing all the files and folders on my hard drive. When you have opened the File Manager you can select View and click on Show Hidden Files. And you will see more folders and files. If this is what you are looking for.

Regards.

Hi..thanks for the reply.. I cant find any file of my booted pen drive in /home/ubuntu/ . where ubuntu is the username when the OS is booted as Live. I can access the files in the drives which i mount. The difficulty i am facing is i cannot access the files present in the same Pen Drive from which i am booting the Ubuntu as Live.

Output which i get is 

ubuntu@ubuntu:~$ ls /home/ubuntu/
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

---

### Post by C.S.Cameron on 2011-04-25
Look in filesystem/cdrom.
Access it using gksu nautilus as the files are read only in 10.10.

---

### Post by sp.1990 on 2011-04-26
Hey thanks a lot ... I found it in filesystem/cdrom.. And i got it .. :)

---

