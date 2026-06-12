---
title: "Missing free space"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by ghostat2005 on 2009-01-23
My Operating system : Ubuntu Linux 8.04.1

I have a problem i cant find where my missing free space 

first , i locate my trash by this command 

sudo find / -type d -name *Trash*  

/home/eld/.local/share/Trash

I used this command the empty my trash
rm -rf /home/eld/.local/share/Trash/*

/dev/sda1     ext3     75G   59G   13G  82% /
Filesystem    Type    Size  Used Avail Use% Mounted on
devshm       tmpfs    1.1G     0  1.1G   0% /dev/shm
overflow     tmpfs    1.0M   40K  984K   4% /tmp
udev         tmpfs    1.1G   16K  1.1G   1% /dev
varlock      tmpfs    1.1G     0  1.1G   0% /var/lock
varrun       tmpfs    1.1G   68K  1.1G   1% /var/run

[[IMG]http://img164.imageshack.us/img164/5199/11822522vc7.jpg[/IMG]](http://img164.imageshack.us/my.php?image=11822522vc7.jpg)

[[IMG]http://img104.imageshack.us/img104/3731/58059007yk3.jpg[/IMG]](http://img104.imageshack.us/my.php?image=58059007yk3.jpg)

and still have the same problem

Thanks in advance

---

### Post by Kobalt on 2009-01-23
Did you check hidden files and directories in your /home folder?

---

### Post by squee on 2009-01-23
Press cntrl+H to show hidden files/folders in a window.

---

### Post by deanjm1963 on 2009-01-23
You're not actually missing any space, ext3 reserves 5% for root usage, it goes back to the olden days (before ipods) where hard drives were only 200 or 300 mb (yes mb not gb) and the system kept a little space for itself for updates etc.

---

### Post by ghostat2005 on 2009-01-23
> **squee said:**
> Press cntrl+H to show hidden files/folders in a window.

When I pressed cntl+H no thing happen

---

### Post by Kobalt on 2009-01-23
You use KDE, this key combination is for Gnome. Use your Konqueror or Dolphin "View" menu to display them.

---

### Post by ghostat2005 on 2009-01-23
> **deanjm1963 said:**
> You're not actually missing any space, ext3 reserves 5% for root usage, it goes back to the olden days (before ipods) where hard drives were only 200 or 300 mb (yes mb not gb) and the system kept a little space for itself for updates etc.

Look at pictures

---

### Post by ghostat2005 on 2009-01-23
> **Kobalt said:**
> You use KDE, this key combination is for Gnome. Use your Konqueror or Dolphin "View" menu to display them.

I found a lot of hidden files 

Thanks for all help

Solved

---

