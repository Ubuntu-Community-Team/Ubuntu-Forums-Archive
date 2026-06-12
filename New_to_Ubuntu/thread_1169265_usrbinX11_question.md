---
title: "/usr/bin/X11 question"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by l-x-l on 2009-05-25
Hi all, I have a quick question. Within my /usr/bin/X11 folder, I have a folder also named X11 which is a link to itself. Is this normal? 

The reason I ask is that whenever I scan the folder with my virus scanner in Windows, the scanner gets stuck in a perpetual loop scanning & re-scanning the folder because it is a link of itself.

I once ran a virus scan for the X11 folder for 4 hours. It just kept scanning itself over & over & over again. Eventually I had to stop the scan because it was just looping over & over with no end in sight. Below is a picture of nautilus. Check out the location bar.

[IMG]http://i245.photobucket.com/albums/gg43/labouie/Screenshot-X11-FileBrowser.png[/IMG]

Is it safe to remove the link? Otherwise my virus/spyware scans in Windows never stop running.

---

### Post by mcduck on 2009-05-25
The link is there since some programs may need it. Don't remove it or you'll most likely break your system.

And running a Windows virus scanner on Linux system directories is just a waste of time. You will *never* find anything there. 

Windows viruses don't run on Linux. Because of that you don't need to worry about any virus infecting any new files on your system. And as nothing you ever do on your machine should download files from untrusted sources into anywhere outside your home directory you can be absolutely sure that all the system files are clean. Besides, if they weren't, you still would not be copying those system files to Windows machines.. :D

---

### Post by l-x-l on 2009-05-25
I can do a manual scan of just my Windows partion but my Windows AV (Avira) prefers to do a "complete system" scan of all partitions. If it doesn't do it, it shows that my system has being possibly compromised because the last complete system scan was before I installed Ubuntu.

Again I would prefer not to run my scanner on the Linux partition. But for complete system scans, it scans all partitions automatically. BTW, I use Avira AntiVir Personal Edition. I looked for a way to do a complete system scan without scanning my Linux partition to no avail.

---

### Post by freeman2000 on 2009-05-25
Avira is probably the best AV scanner in the Windows world.  Unknown to most people is that they also have an AV for Linux.  
You might try the Avira forum for more info.  Good luck.

---

### Post by CatKiller on 2009-05-25
It's a **long** time since I last used Windows, but can't you unmount your Linux partition before you start your scan? Using Disk Management or whatever it's called?

---

### Post by l-x-l on 2009-05-25
You are right Catkiller. As a solution, I decided to simply unmount the Linux partition from Windows Vista when scanning. So system scans no longer involve that partition.

Thanks to all for the help & insight.

---

