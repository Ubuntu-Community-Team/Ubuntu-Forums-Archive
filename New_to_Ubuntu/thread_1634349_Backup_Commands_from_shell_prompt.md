---
title: "Backup Commands from shell prompt"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by openick on 2010-11-30
I have 10.04 LTS in a netbook, during a package add process, a series of files were deleted one after another before I interupted the process, so the netbook does not start. 

I have connected a seagate external drive for backup.

In the command prompt 

root@username:~# ls //dev/disk/by-path shows:

pci-0000-00-1d.7-usb-0:1:1.0-scsi-0:0:0:0
pci-0000-00-1d.7-usb-0:1:1.0-scsi-0:0:0:0-part1

ls //dev/disk/by-id shows

usb-Seagate-FreeAgent_Go_2GE3C6B-0:0
usb-Seagate-FreeAgent_Go_2GE3C6B-0:0-part1

ls //dev/disk/by-label shows

FreeAgent\x20Drive ( yes, with a reverse slash)

ls //dev/disk/FreeAgentx29Drive merely returns
//dev/disk/FreeAgentx20Drive

What is the syntax for copying the contents of the Ubuntu hard disk folder by folder? I tried 

cp //home/username/filename //dev/disk/FreeAgent\x20Drive

The command is accepted,I tried the mv command with the same syntax for another file, that command was also accpeted, but when I connected the Drive to another ubuntu computer and examined the contents, I did not find the files. 
Am I making an error in the command?

Thank you.

---

### Post by cariboo on 2010-11-30
Where is the disk mounted when you connect it. If it's auto-mounted, it should show up in /media. You may need to be root, to move the files to the external drive, depending on ownership.

---

### Post by openick on 2010-12-01
Thank You.

The system does not load the desktop, goes as far as command prompt root@computername:~#  ls /media  shows names of usb drives that were once connected. The disk does not show up.

This after a reboot.

Now what do I do?

---

