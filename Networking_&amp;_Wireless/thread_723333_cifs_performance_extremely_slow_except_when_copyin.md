---
title: "cifs performance extremely slow except when copying with multiple separate threads"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by watricky on 2008-03-13
I have an odd problem on my LAN. Using cifs, I get extremely poor performance when transferring files from any of our servers to my desktop. The odd thing is that if I do 2 copy operations simultaneously it goes lightning fast.

For example:

Average copy speed for 1 large file (ie, >350MB) is about 600KB/s, peaking at about 1MB/s

Average copy speed for 2 large files is about 10.5MB/s EACH, peaking at about 12MB/s. 3 large files have a similar boost however reaching about 7MB/s each so I believe this is at the limit of the network/disk capability.

I've mounted the files by adding cifs entries into my /etc/fstab

Except for having different mount points, credentials files and server shares, all the entries are as follows with identical options:

//backupbox2/Backups /media/backups2 cifs ro,noperm,soft,uid=brendan,user,credentials=/home/brendan/.backup2cred 0 0

By running cp twice simultaneously in separate konsoles, surrounded by "date", I can get some real numbers.
Here are my results:
Simultaneous:
File1 - 731977728 bytes - 62s
File2 - 731201536 bytes - 53s

One after the other:
File1 - 731977728 bytes - 10m, 59s
File2 - 731201536 bytes - 8m, 16s

It doesn't matter if I'm copying the 2 files from a Windows 2003 server or a Linux (CentOS 4) server and it doesn't matter even if I'm copying 1 file from each simultaneously, I get a mega speed boost by just copying an extra file. I can even copy the same file to 2 different folders simultaneously and get the same speed boost.

My desktop and the server are constantly under load however the symptoms are prevalent even when I know there's very little load on the server.

When using smbfs I do not have this problem. A colleague of mine is using Gentoo and has the same problem with cifs but also not with smbfs. I suspect it may either be a bug in cifs or perhaps our /etc/fstab mount entries.

Anyone heard of this problem before?

---

### Post by HermanAB on 2008-03-13
You'll have to run tcpdump and see what is going on.  It is quite possible that you have an authentication problem slowing things down.

Cheers,

Herman

---

