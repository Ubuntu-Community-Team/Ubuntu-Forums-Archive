---
title: "Backup to USB drive"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by RobHK on 2009-02-11
A major obstacle to moving from Windows for me is backup. 

In Windows I use either Back2Zip or a simple batch file using xcopy. I have tried Googling, but have not really found a simple solution for Linux.

I'm talking about backing up selected areas to a USB hard drive.

Any help most welcome.

---

### Post by skymera on 2009-02-11
I believe TimeVault is backup software that works with Ubuntu.

Might be what you#re looking for:

[https://launchpad.net/timevault](https://launchpad.net/timevault)

---

### Post by Temposs on 2009-02-11
I use a program called Simple Backup, which is in the repositories. It does automated backups and is very customizable.

People also like to use rsync, which is a command-line based backup program. If you want to use that in a GUI, you can get grsync from the repositories.

---

### Post by callan79 on 2009-02-11
> **RobHK said:**
> In Windows I use either Back2Zip or a simple batch file using xcopy. I have tried Googling, but have not really found a simple solution for Linux.


Easy :)

Since you're familiar with xcopy, you should be able to work out the Linux 'cp' command - you'll need the -rvu switch, which means recursive, verbose and only updated files.

```
cp -rvu /home/robhk /media/disk/backups
```

will copy your whole home directory to the USB drive mounted at /media/disk. Of course check where your USB drive really is mounted before using the command :)

Cheers
Callan

---

