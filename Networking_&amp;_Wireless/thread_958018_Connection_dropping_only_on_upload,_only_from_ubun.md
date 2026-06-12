---
title: "Connection dropping only on upload, only from ubuntu"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by kirilisa on 2008-10-24
Hi folks,
I have a mystery problem. As of last week, I cannot upload to my shared hosting account at Hostgator. Whether I am using GUI FTP, command line FTP/SCP, the browser via Cpanel, Joomla, etc. I am unable to upload/save files to my hosting account at Hostgator.

The weird things? It happens ONLY from my home, ONLY with regards to Hostgator, ONLY when uploading, and ONLY on Ubuntu. If I use Filezilla from the Windows boot partition of my laptop, it's fine. If I upload to any other (non-Hostgator) sites, it's fine. Downloading from anywhere (including hostgator) is fine. If I do it from my Ubuntu machine at work, it's fine.

I aksed Hostgator and they say they haven't changed anything. I have not changed anything on my ADSL modem, my wireless router, or my Ubuntu machine in the last few weeks. Indeed, I have tried it from home here with all 3 Ubuntu machines we have and it fails from all. 

Hostgator said to edit /etc/resolv.conf to put in nameservers 208.67.222.222.and 208.67.220.220. I did, it didn't help. Ubuntu version is 8.04 by the way. One of the machines here is wired to the ADSL modem and the other two are wireless. Makes no difference.

Any thoughts? I'm totally baffled and distressed.

---

### Post by rushtovijay on 2009-08-28
Any solution to the above problem? I experience the same problem in ubuntu 8.04, 9.04 or any other linux box for that matter, tested on red hat also.

However from windows (ie, firefox or chrome) it works just fine. 

Hosting Account at GoDaddy

Don't know if it is a setup problem @ GoDaddy. If so how does it work from windows ?

---

### Post by rushtovijay on 2009-08-28
Solved. This problem is related to [_[COLOR="Olive"]ftp stalls when uploading file[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=7861319#post7861319")

---

