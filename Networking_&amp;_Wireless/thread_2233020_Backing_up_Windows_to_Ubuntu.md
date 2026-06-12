---
title: "Backing up Windows to Ubuntu"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by dmac2 on 2014-07-05
How can I back up my windows 8.1 computer to my recently made Ubuntu server? I probably should have asked this in the ultimate beginners section, but this is really more specified than that, so I came here. I have tried samba, and I have a working folder on the server, but I can't back up to it through my back up software. I tried FTP, but that has got me nowhere, except for the fact that I noticed that I can use FTP to move Minecraft server files over using WinSCP. Can someone please explain to me in most simple terms how to back up my computer?

---

### Post by TheFu on 2014-07-05
First, don't use old-style FTP. Use sftp instead. WinSCP is good.

2nd, if you have samba working, then the issue is on the Windows side.  Not all Windows backup software will work over a network. I don't have Win8, but Win7 Home backup software DOES NOT SUPPORT NETWORK DRIVES.  The "professional" version does.

There are lots of backup software alternatives for Windows.  I suspect most people use a commercial solution, since that seems to be required in the Windows world.
I make an image-based backup of Windows every quarter to avoid loosing too many patches - partimage, clonezilla are examples. These really can't be automated since booting off alternate media is required. For normal data files, which I minimize on Windows, rsync works for me.

Sorry - I haven't explained anything. For backing up Linux, I'm your guy (duplicity, rdiff-backup, tar, rsync, and 20 others). Not so much for Windows.  I find that images are the only real method without high-end ($50+) commercial software on Windows.

---

### Post by dmac2 on 2014-07-05
Well, I do have to say that this sort of thing requires a knowledge base of Windows AND linux, so that means that it is really hard to find the right person. People are mostly Windows users, Linux users, or people who use Windows and want to dabble a bit in Linux, like me. (And probably many sub categories of people who do not fit in those three categories)

---

### Post by TheFu on 2014-07-05
> **dmac2 said:**
> Well, I do have to say that this sort of thing requires a knowledge base of Windows AND linux, so that means that it is really hard to find the right person. People are mostly Windows users, Linux users, or people who use Windows and want to dabble a bit in Linux, like me. (And probably many sub categories of people who do not fit in those three categories)

There are lots and lots of people here with both sorts of knowledge.  I'm just lucky and haven't needed to know much Windows since 2007. I still use it daily, but in extremely specific ways for 2-3 specific purposes. Everything else happens on Linux.

So ... from windows, you need to find a program that will create backups to network storage. Samba = CIFS, but any tool that can write to sftp would be a bonus.  I've played with Duplicity on Windows, but found the time to backup abusive - over 12 hrs for 20G of data.

What backup program are you using today and which version of Windows8 are you running (home/pro/ent/ult/basic)?
What sort of networking do you have?  wifi would be the worst, 100base-tx next and 1000base-tx would be nice.

---

### Post by mooreted on 2014-07-05
Not enough information. 

How did you setup Samba?
Is Samba set to the same workgroup as the Windows machine?
Are you using a firewall?
Are the Windows and Linux machines on the same network subnet?
Can you ping the Windows machine from the Linux server?
Can you ping the Linux server from the Windows machine?

Here is an overview that might help:

[http://www.liberiangeek.net/2012/11/enable-file-sharing-between-windows-8-and-ubuntu-12-10/?PageSpeed=noscript](http://www.liberiangeek.net/2012/11/enable-file-sharing-between-windows-8-and-ubuntu-12-10/?PageSpeed=noscript)

---

### Post by dmac2 on 2014-07-06
1. By using some online guide. I can access the folder set up by samba fine, I just can't back up to it. (I'm using ascomp's Backup Maker. It supports FTP.)
2. I would think so, if I can access it.
3. No, not as I know.
4. What?
5. ? How would I do this?
6. ? How would I do this as well?
7. I was able to do the windows 8 part of the guide, but I'm using Ubuntu server version, so there is no gui that I can tell of.
8. I'm not on wifi- I have both computers connected to the router through ethernet cables and I get ~20-30 Mbps download, ~2 or 3 Mbps upload.
9. I'm on Windows 8.1 home, I think. I got this computer as a gift a year or two ago, so I really don't quite know. The only upgrade package Windows tells me is available is windows 8 pro.

---

