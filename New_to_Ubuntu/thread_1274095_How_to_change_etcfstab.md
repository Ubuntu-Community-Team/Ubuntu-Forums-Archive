---
title: "How to change /etc/fstab"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by donescamillo on 2009-09-24
Hi,

I wanted to have my NTFS partitions auto-mounted so I installed the NTFS configuration tool and used it.
Since then I read in a book (Ubuntu Linux Bible) that what gets auto-mounted at boot time is stored in /etc/fstab.
To change fstab I run Nautilus from terminal:
sudo nautilus

This let me change fstab and save it back. The original fstab looked like this:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /media/HDD ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sdb5 /media/HDD2 ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda6 /media/Mime ntfs-3g defaults,locale=en_AU.UTF-8 0 0

I only changed the name of dev/sda5 from HDD to WinXP just to see what will happen andrestarted the PC.
As a result dev/sda5 did not mount at all. Why?
Does that mean that these entries are stored in some other place somewhere and if they do not correspond with fstab they are ignored?
Can I manually change the fstab file at all?

Thank you
donescamillo

---

### Post by Hallvor on 2009-09-24
> **donescamillo said:**
> Hi,

I wanted to have my NTFS partitions auto-mounted so I installed the NTFS configuration tool and used it.
Since then I read in a book (Ubuntu Linux Bible) that what gets auto-mounted at boot time is stored in /etc/fstab.
To change fstab I run Nautilus from terminal:
sudo nautilus

This let me change fstab and save it back. The original fstab looked like this:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /media/HDD ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sdb5 /media/HDD2 ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda6 /media/Mime ntfs-3g defaults,locale=en_AU.UTF-8 0 0

I only changed the name of dev/sda5 from HDD to WinXP just to see what will happen andrestarted the PC.
As a result dev/sda5 did not mount at all. Why?
Does that mean that these entries are stored in some other place somewhere and if they do not correspond with fstab they are ignored?
Can I manually change the fstab file at all?

Thank you
donescamillo


I think it may be failing because there is no directory called /media/WinXP

Assuming this is how the entry in fstab looks like now:
```
/dev/sdb5 /media/WinXP ntfs-3g defaults,locale=en_AU.UTF-8 0 0
```

It should be OK if you open a terminal and type ```
sudo mkdir /media/WinXP
``` That makes a directory called /media/WinXP that fstab can use for mount.

Reboot and test if it works.

---

### Post by utnubuuser on 2009-09-24
To use Nautilus as super user, try the command "gksu nautilus".  Using "sudo" for graphical applications can have unexpected results.

---

### Post by theozzlives on 2009-09-24
It's best not to run Nautilus as root to often, or for to long. try:
```
gksu gedit /etc/fstab
```

---

### Post by ^_Pepe_^ on 2009-09-24
...and, you don't have to restart your PC to 'simulate' the boot mount process.

You just have to open a terminal and type:

```
sudo mount -a
```

and also you can see if any error is displayed

Regards,
^_Pepe_^
[I guess this is my 1st contribution, can I bump my linux level up from 2/10 to 3/10? :P]

---

### Post by Cheezespread on 2009-09-24
The defaults in fstab relate to these as I remember :
>  **rw, exec, auto, nouser**

So as ^_Pepe_^ suggested , you can check if the device is mounted at all with the ```
sudo mount -a 
``` command.

Else , i would suggest to edit that fstab entry to add this :


```
/dev/sda5 /media/WinXP ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
```

---

### Post by donescamillo on 2009-09-24
Thank you for you replies. I created a WinXP folder and it worked. Apparently the NTFS config tool not only edits the sftab file, it also creates a mounting folder

regards,
donescamillo

---

