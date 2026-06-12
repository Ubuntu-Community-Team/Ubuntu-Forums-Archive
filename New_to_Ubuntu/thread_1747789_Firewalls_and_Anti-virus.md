---
title: "Firewalls and Anti-virus"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Solstice Bahai on 2011-05-03
Before I forget guys, any advice regarding firewall and anti-virus/anti-spyware for Ubuntu? Especially as I'm now using 11.04 Natty? and also, as I have lost the recovery disk for this Netbook (therefore can't go back to Windows for this pc,even if I wanted to!!) Not that I want to, I really want to get the hang of Linux
Thanks for your time:D

---

### Post by ~Plue on 2011-05-03
The wiki could help you with that
[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Also [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by 3rdalbum on 2011-05-03
Welcome to Linux.

As for antiviruses, you don't need one. Linux doesn't have any viruses at the moment. In fact, it hasn't had any real viruses for years.

If you are transferring files to and from Windows computers, you might want to scan those files with KlamAV (available from Software Center), but don't worry - Windows viruses don't affect Linux, and don't bother trying to scan your whole Linux hard disk for viruses.

Firewalls are also not terribly necessary. By default, Ubuntu won't listen for incoming connections anyhow. If you use a router or ADSL modem, chances are that it's already doing firewall duties for you. If you are purposely running services that listen for incoming connections and you DON'T want them to be accessible from remote computers (for instance, you're running a test web server), then you can configure the inbuilt Linux firewall using the "gUFW" tool in Software Center.

But don't bother enabling the firewall unless you've installed or configured something to listen for incoming connections.

---

### Post by KL_72_TR on 2011-05-03
It is funny but I use ClamAV to scan what I have in Windows HDD. So far on Linux never found anything dirty.
What is most needed is the firewall.

---

### Post by Wolligog on 2011-05-03
You can get UFW firewall from the software centre,  i use it.  as for antivirus, i tried klam on meerkat, then installed bit defender instead but i never ever used it,  i'm on 11:04 natty  narwahl now and only have UFW, probably gonna install an antivirus, i would hate for complacency to be my downfall but tbh it's really not needed for linux

---

### Post by speedwell68 on 2011-05-03
I do run an antivirus on my Linux boxes, just to be sure that I am not going to pass anything nasty on to any Windows users that I interact with.  I have found the odd thing, usually in my Thunderbird junk folder.  It is better to be safe than sorry.  If I did accidently infect a windows using friend then it would be me that would sort it out anyway.  ClamAV is quite good, it is in the Ubuntu repositories, AVG and Avast are available for Linux too.

---

