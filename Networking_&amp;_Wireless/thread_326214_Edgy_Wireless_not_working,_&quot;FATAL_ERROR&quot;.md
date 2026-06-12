---
title: "Edgy Wireless not working, &quot;FATAL ERROR&quot;"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by 101linux_mike101 on 2006-12-27
Thanks to "STEVE.K" I have hopefully wrote a better post that will hopefully help me fix my problem. ;) 

I get the error [B]FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
[/B] when trying to run sudo modprobe ndiswrapper when trying to install wireless.

My card (INPROCOMM IPN2220 Wireless LAN Card) worked perfectly in Dapper without a hitch, I've tried the following steps with a clean install of Edgy.

the exact steps I took are here: 
[B]
admin1@admin1-laptop:~$ cd Desktop
admin1@admin1-laptop:~/Desktop$ sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_i386.deb
Password:
(Reading database ... 88204 files and directories currently installed.)
Preparing to replace ndiswrapper-utils 1.8-0ubuntu2 (using ndiswrapper-utils_1.8-0ubuntu2_i386.deb) ...
Unpacking replacement ndiswrapper-utils ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

admin1@admin1-laptop:~/Desktop$ sudo ndiswrapper -i neti2220.inf
neti2220 is already installed. Use -e to remove it
admin1@admin1-laptop:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument[/B]

When I run "iwconfig" I get:

[B]lo        no wireless extensions.

sit0      no wireless extensions.[/B]

So really confused I really want to continue to use Ubuntu. The problem and solution seems to be outlined here in launchpad [https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983) but i'm very noob so please any responses please write in clear noob:p 

_Please note that I have no internet connection on my ubuntu partition only on my XP partition. _

 Thanks in advance,

Mike

---

### Post by c.dric on 2006-12-27
<original erased>

sorry.

i should have read the post entirely before replying :[

---

### Post by 101linux_mike101 on 2007-01-01
*Bump* I really need help with this, I'm not experienced enough to trail and error - and the times I did resulted in a re installation of Ubuntu.

---

### Post by bgoody on 2007-01-01
Hi.  What is the output of 

sudo ndiswrapper -l

Brian

---

### Post by encho on 2007-01-02
I think you are using 2 versions of ndiswrapper. At least that was happening to me. There are 1.1 and 1.8. Open synaptic and remove 1.1 or use ndiswrapper-1.8 at command line.

---

### Post by Vox754 on 2007-02-13
Remove "ndiswrapper" from synaptic, and get the latest stable version from SourceForge.net.
It is a .tar.gz file, which you need to extract and compile. It is not difficult.

Look here
[http://ubuntuforums.org/showthread.php?t=324967](http://ubuntuforums.org/showthread.php?t=324967)
[http://ubuntuforums.org/showthread.php?t=339802&highlight=inprocomm](http://ubuntuforums.org/showthread.php?t=339802&highlight=inprocomm)

Look for your hardware here
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

