---
title: "can't copy file to pen drive"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by saintj0n on 2010-09-19
Hello
I am trying to copy a spreadsheet file to a usb pen drive and Linux is not letting me do so.  When I drag the file to /mnt/USB, it says:

Error opening file '/mnt/USB/091810pack935roster.xls': Permission denied

On the spreadsheet file, I went into properties and changed the permissions to read and write for all users. Do I need to change permissions somehow on my mounted fs?

---

### Post by garvinrick4 on 2010-09-19
rick@rick-laptop:~$ cd /media
rick@rick-laptop:/media$ ls
adata   lucid  maverick  net      redhat  usb
BACKUP  lynx   meerkat   netbook  SYSTEM  usb_
rick@rick-laptop:/media$ ls -la
total 80
drwxr-xr-x 14 root root  4096 2010-09-19 19:42 .
drwxr-xr-x 24 root root  4096 2010-09-02 22:59 ..
drwx------  1 rick rick 24576 2010-09-18 21:14 adata
drwx------ 12 rick rick  8192 1969-12-31 16:00 BACKUP
drwxr-xr-x  3 root root  4096 2010-07-06 14:27 lucid
drwxr-xr-x  2 root root  4096 2010-07-22 13:47 lynx
drwxr-xr-x  2 root root  4096 2010-06-25 15:32 maverick
drwxr-xr-x  2 root root  4096 2010-06-25 15:31 meerkat
drwxr-xr-x  2 root root  4096 2010-09-05 23:16 net
drwxr-xr-x  2 root root  4096 2010-08-07 03:41 netbook
drwxrwxrwx  2 root root  4096 2010-06-25 15:33 redhat
drwxr-xr-x  2 root root  4096 2010-07-06 14:30 SYSTEM
drwxr-xr-x  2 root root  4096 2010-07-30 19:29 usb

rick@rick-laptop:/media$ 
adata is usb external
BACKUP is a pendrive

Run same commands see what your permissions are? Post here

---

### Post by llamabr on 2010-09-20
You don't have permission.  Run it with sudo, or else do it correctly by changing the settings in /etc/fstab

---

### Post by mikechant on 2010-09-20
It looks like you manually mounted it under /mnt/USB, is that right? Did you actually add an entry to fstab, or type a 'mount' command?
Normally for USB sticks you don't do any of that, just plug it in and it should automount under /media with the correct permissions.

---

### Post by saintj0n on 2010-09-20
I typed ls -la and got:

root@daddy-desktop:/mnt/USB# ls -la
total 8
drwxr-xr-x 2 root root 4096 1969-12-31 19:00 .
drwxr-xr-x 3 root root 4096 2010-09-19 11:44 ..

How come I can't see the drive in the Places>Computer space?
Also, how do you change the permissions to allow me to write files (preferably in a GUI)?

---

### Post by saintj0n on 2010-09-20
> **mikechant said:**
> It looks like you manually mounted it under /mnt/USB, is that right? Did you actually add an entry to fstab, or type a 'mount' command?
Normally for USB sticks you don't do any of that, just plug it in and it should automount under /media with the correct permissions.

I checked /media.  It is not there for whatever reason. I did add an entry to fstab:

/dev/sdc        /mnt/USB        auto noauto,owner,kuzu 0 0

/dev/sdc is my pendrive.  I did a dmesg|grep sd and found it there.

---

### Post by sandyd on 2010-09-20
> **saintj0n said:**
> I checked /media.  It is not there for whatever reason. I did add an entry to fstab:

/dev/sdc        /mnt/USB        auto noauto,owner,kuzu 0 0

/dev/sdc is my pendrive.  I did a dmesg|grep sd and found it there.
change it to
/dev/sdc        /mnt/USB        auto noauto,users 0 0

---

### Post by suneetha on 2011-03-02
i tried to copy a ppt file to pendrive but i getting warning as
"read-only mode".how to change its permissions?

---

