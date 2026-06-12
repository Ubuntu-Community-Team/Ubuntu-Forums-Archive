---
title: "Reading files with both ubuntu and win 7"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by pelu_jose on 2011-08-29
Ok here's the deal, im new and just installed ubuntu with minor setbacks, the "/usr/lib/libgconf2-4/... blah blah blah" stuff, and finally managed to install it correctly. But the problem is that after doing that, i forgot to check the folders i wanted to share (on the options the the installer gives you). Now i need some files i have saved in those folders most of them are word docs and stuff and i know i can just use a usb. But it would be easier and it would not occupy double space if i can use those files with win 7 and ubuntu. 
thanks a lot

---

### Post by zirch on 2011-08-29
Are you saying you want to be able to access files regardless of whether you are using Ubuntu or Windows 7?

---

### Post by fdrake on 2011-08-29
> **pelu_jose said:**
> O i forgot to check the folders i wanted to share (on the options the the installer gives you).
sharing on the net, sharing between systems on the same machine? what exactly did you install?

---

### Post by Alwimo on 2011-08-29
Have a windows partition and an ubuntu partition. When in Ubuntu, mount the Windows partition. Save things to the Windows partition.

You can access your files from either Ubuntu or Windows that way.

---

### Post by pelu_jose on 2011-08-29
> **zirch said:**
> Are you saying you want to be able to access files regardless of whether you are using Ubuntu or Windows 7?

yeah thats exactly what i want to do. Is it possible??

---

### Post by oldfred on 2011-08-29
Windows does not like a lot of reading and writing from foreign systems. Especially unclean shutdowns, or any type of hibernation can cause lots of issues Make sure you have a Windows repairCD so you can run chkdsk.

I suggest a separate NTFS "shared" partition. Many Windows users suggest a separate data partition so when you have to reinstall Windows you do not have to restore your data. Backups still required.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by pelu_jose on 2011-08-30
i managed to read (just read) the files but i dont know yet how to edit or write a new one
[http://www.pendrivelinux.com/mounting-a-windows-xp-ntfs-partition-in-linux/](http://www.pendrivelinux.com/mounting-a-windows-xp-ntfs-partition-in-linux/)

---

### Post by zirch on 2011-10-18
If it's in another partition, just mount it and you can access the files.
If it's in the same partition as the root directory, just go to Computer > Filesystem > Host > Users > [your username], and the folders are as you would see in the Users directory in Windows 7.

---

### Post by zirch on 2011-10-18
To access ubuntu files from Windows 7, [http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/](http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/)

---

### Post by Mark Phelps on 2011-10-18
To reiterate what Oldfred said ... if those files you want to write are in your Win7 OS partition, it would be best if you did NOT do that.  Win7 is very touchy about its filesystem being modified from outside (as in when you mount it under Linux) and it's easily corrupted as a result -- often rendering the Win7OS unbootable as a result.

If you're going to WRITE files, then you need to have a separate NTFS Data partition.  Since that partition doesn't boot, you won't risk problems with it writing to it from Ubuntu.

---

