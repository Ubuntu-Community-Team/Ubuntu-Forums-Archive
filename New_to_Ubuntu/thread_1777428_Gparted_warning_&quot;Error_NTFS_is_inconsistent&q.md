---
title: "Gparted warning &quot;Error: NTFS is inconsistent&quot;, problems with Windows partition"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by unapendeza on 2011-06-07
Hello, I am very new to linux, I made the switch from Windows Vista to Ubuntu 10.10 on my desktop only in February and in April I partitioned my laptop which now dual boots Ubuntu 11.04 and Windows 7. I am having issues with the Windows partition and I have a few general questions regarding Gparted.

I opened up Gparted this morning for the first time since installing it so I could change the boot flag on a USB drive and I noticed that /dev/sda2 (the Windows partiton) had a warning sign next to it. I right clicked it and selected information and the warning message tells me that the filesystem check failed and NTFS is inconsistent. Could someone explain to me in depth what this means and how to run chkdsk /f on Windows? This is a screenshot of Gparted.

[IMG]http://img860.imageshack.us/img860/7411/screenshot9fd.png[/IMG]


Side note: I noticed that Windows 7 created or this computer came  installed with a Windows recovery partition which I want to get rid of  because if I ever need to restore Windows I would prefer to do it manually because I have all of my files backed up on my desktop and this recovery drive is taking up too much space. Also, I would like to make my Ubuntu partition larger and I'm not sure how to go about this.

---

### Post by Mark Phelps on 2011-06-07
If you're asking can you run CHKDSK on the Windows filesystem from inside Ubuntu -- the answer is NO.  You have to boot into Windows and run it there.

If Win7 is still bootable, one way to do it is to open Computer, right-click on the drive, Select Properties --> Tools and click on the button to check the drive for errors.

If this is the OS partition, it will ask to schedule a check on reboot.  Tell it Yes (or OK, forget which).

---

### Post by jtarin on 2011-06-07
When changing any partition information/size for Windows you should always boot twice into Windows before anything else if possible.

 **_From the Win 7 Help application_**:
```
Check your hard disk for errors

You can solve some computer problems and improve the performance of your computer by making sure that your hard disk has no errors.

Click to open Computer.

Right-click the hard disk that you want to check, and then click Properties.

Click the Tools tab, and then, under Error-checking, click Check now.  If you are prompted for an administrator password or confirmation, type the password or provide confirmation.

To automatically repair problems with files and folders that the scan detects, select Automatically fix file system errors. Otherwise, the disk check will report problems but not fix them.

To perform a thorough disk check, select Scan for and attempt recovery of bad sectors. This scan attempts to find and repair physical errors on the hard disk itself, and it can take much longer to complete. 

To check for both file errors and physical errors, select both Automatically fix file system errors and Scan for and attempt recovery of bad sectors.

Click Start.

Depending on the size of your hard disk, this might take several minutes. For best results, don't use your computer for any other tasks while it is checking for errors.

Note
If you select Automatically fix file system errors for a disk that is in use (for example, the partition that contains Windows), you'll be prompted to reschedule the disk check for the next time you restart your computer.

```

---

