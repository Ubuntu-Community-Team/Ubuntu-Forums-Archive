---
title: "I need to transfer files from Linux to Windows over LAN"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by HunterAmacker on 2008-09-28
So, I'm recovering files from an old laptop with a corrupted Windows installation. I'm using a Ubuntu 6.06.1 Live CD to boot, and mounting the hard drive using the following commands:
```
cd /mnt
sudo mkdir windrive
sudo mount -t nfts /dev/hda2 /mnt/windrive -o "umask=022"
```

This works fine, and I access the files I need to recover. The only problem is actually getting the files off the hard drive. I could use a USB drive, but the laptop's performance is incredibly slow and coping the files would take hours. So I'm looking to transfer them over my LAN, specifically to my Windows Vista desktop. 
 And thats where I'm lost. I have no idea how to actually do this. People I've talked to in IRC have suggested installing Samba, but I can't do that for 2 reasons:
1. The laptop is painfully slow, and every time I go to Add/Remove Software, it freezes up until I have to restart.
2. I doubt I'll be able to install anything what-so-ever, since I'm running on a Live CD.


I have tried every version of Ubuntu from 6.06 to 8.04, along with Xubuntu, RIP Linux, Fedora, SystemRescueCD, DSL, and Bart PE, and Ubuntu 6.06 has been the ONLY OS to actually boot. All others freeze while loading. I have VMWare Workstation, just in case I'll need that for anything.

So basically what I'm asking is:
How can I move a lot of files from Linux to Windows without installing anything on the Linux comp?

---

### Post by kevdog on 2008-09-28
How about ftp or ssh?  Ftp is the easiest to set up -- FileZilla on Windows.

Easy actually.

---

### Post by HunterAmacker on 2008-09-28
Ok, but how do I actually do that? I've only used Ubuntu a total of 5 times, and I'm not to familiar with it.

---

### Post by kevdog on 2008-09-28
Where do you want to install the server?  On the Ubuntu or Windows machine?  By default, Ubuntu has a ftp client built in.  None of them have a server built-in.  For Windows you would either need to install the FileZilla server or client application.  Beyond that all you need to know is the local IP address of the server.  On Ubuntu that would be ifconfig and on Windows -- ipconfig.

---

