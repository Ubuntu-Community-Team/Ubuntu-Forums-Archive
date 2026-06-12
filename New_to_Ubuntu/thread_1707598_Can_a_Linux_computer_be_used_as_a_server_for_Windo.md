---
title: "Can a Linux computer be used as a server for Windows Computers?"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by WA3ERQ Jim on 2011-03-15
My house currently has 3 desktops and 2 laptops.  1 desktop and 1 laptop are purely Ubuntu 10.10.  1 is Ubuntu/Windows 7 and the other 2 are Windows 7 and Vista.

I want to be able to share files between all of my computers and was hoping that I can use the Linux system (desktop) as a server and repository for my backups.  I do not have the server edition of Ubuntu but will change if necessary.  I am still a beginner with Linux which is why I'm still with Ubuntu.  Currently the computer that I want to use as a server is just hooked up to my network and sitting waiting to be used.  Unfortunately, I can't convince the wife to change to Linux plus the majority of her software is purely Windows.  The specs are:

Gateway GM5474
AMD Athlon™64 X2 6000+, 64-bit dual core processor 
[LIST]
[*]Operates at 3.0 GHz
[*]2 x 1024 KB L2 cache
[*]2000 MHz system bus
[/LIST]
2048 MB DDR2, 667 MHz, (PC2-5300) dual channel memory

Thanks

Jim

---

### Post by sanderd17 on 2011-03-15
There is no problem in making partitions available over the network, but you will need to find a good backup sollution that runs on windows.

---

### Post by Hero1969 on 2011-03-15
Sorry for the generic answer, but start doing some research on Samba.

---

### Post by vivek.pandey on 2011-03-15
hi i think you must check this out
[http://linux.about.com/od/ubusrv_doc/a/ubusg30t01.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg30t01.htm)

---

### Post by Paqman on 2011-03-15
> **WA3ERQ Jim said:**
> 
I want to be able to share files between all of my computers and was hoping that I can use the Linux system (desktop) as a server and repository for my backups.

This is no problem. When you're serving files over the network it's not the OS that each machine has installed that matters, but the protocol they use to talk to each other. Linux machines can use Samba to talk to Windows machines in their native SMB/CIFS protocol.

> 
I do not have the server edition of Ubuntu but will change if necessary.

You don't have to. Ubuntu server and desktop use the same software repositories, so there's nothing stopping you from installing server packages onto a desktop (or vice versa)

> 
I am still a beginner with Linux which is why I'm still with Ubuntu.

You might find you'll stick with it anyway. Plenty of very knowledgeable folks use Ubuntu.

---

### Post by _0R10N on 2011-03-15
Well, there's no problem about making an ubuntu pc work as a server, but before going through the installation of any software, you could specify exactly what you want to share through your server: database access? media?

---

### Post by LowSky on 2011-03-15
Most of the world's internet runs on Unix and Linux servers. And with most people connecting using Windows... I think it all works fine.

---

### Post by bodhi.zazen on 2011-03-15
> **LowSky said:**
> Most of the world's internet runs on Unix and Linux servers. And with most people connecting using Windows... I think it all works fine.

This ^^

"Server" is a very generic term, but severs, by definition, means the ability to allow connections from clients.

For file sharing you can use samba. There are several alternate protocols including nfs, http, https, ftp, ssh (scp) to name a few and yes Windows can connect to all of those protocols.

---

### Post by crispy_420 on 2011-03-15
Couldn't one just create a samba server on the Linux/Server box for starters. Then on each Windows machine mount the samba share as a network drive. So in theory any backup tool normally available to Windows users access it all the same since it is a "local" drive as far as it is concerned.

---

### Post by Ghost_Mazal on 2011-03-16
> **crispy_420 said:**
> Couldn't one just create a samba server on the Linux/Server box for starters. Then on each Windows machine mount the samba share as a network drive. So in theory any backup tool normally available to Windows users access it all the same since it is a "local" drive as far as it is concerned.

Yes you can. I've been using Linux Samba shares for backup location and file storage for Windows pc's for many years.

---

### Post by iiiears on 2011-03-16
samba is perfect for files and backup.  Theres a windows version of gnuwin32 rsync if the windows backup file format isn't desirable. 

 Mythbuntu is ready made for a tv tuner card and streaming video/music files.

Best Wishes.

---

