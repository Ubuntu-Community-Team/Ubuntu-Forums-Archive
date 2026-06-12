---
title: "Protection for pen drive against viruses.."
date: 2009-08-23
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-23
I have used to insert USB drives in my ubuntu machine and in windows,so is there any script to delete viruses in my pendrive.And also when i insert USB drive in ubuntu the drive mounts automatically,if there is virus in my pendrive will it cause any problem to UBUNTU..

---

### Post by Penguin Guy on 2009-08-23
> **getyourkarthick said:**
> is there any script to delete viruses in my pendrive.
Yes, search for [COLOR="Green"]virus[/COLOR] in synaptic ([COLOR="Green"]System -> Administration -> Synaptic Package Manager[/COLOR]).

> **getyourkarthick said:**
> if there is virus in my pendrive will it cause any problem to UBUNTU..
No.

---

### Post by MelDJ on 2009-08-23
ubuntu wont be harmed if its a windows virus. maybe install an antivirus to scan windows drives?

---

### Post by karthick87 on 2009-08-23
I have installed CLAMAV antivirus..

---

### Post by MelDJ on 2009-08-23
that should be sufficient.. just be alert:lolflag:

---

### Post by karthick87 on 2009-08-23
will clamav detect spyware?

---

### Post by MelDJ on 2009-08-23
according to their website yes.

---

### Post by jimmy the saint on 2009-08-23
A good thing to do in Windows would be to disable autorun.  That way when you insert the pen-drive, malware that takes advantage of auto-run will not be able to infect your machine.  Even if a virus somehow gets on to your pendrive, you will have to interact with it in order for it to do much.  It isn't a perfect solution, but it closes one door to attack.

---

### Post by hackerseraph on 2009-08-23
> **jimmy the saint said:**
> A good thing to do in Windows would be to disable autorun.  That way when you insert the pen-drive, malware that takes advantage of auto-run will not be able to infect your machine.  Even if a virus somehow gets on to your pendrive, you will have to interact with it in order for it to do much.  It isn't a perfect solution, but it closes one door to attack.

Yeah, disabling autorun is a good idea because thats how conficker virus infects thumbdrives and other removeable media. I would also recommend not only running clamav (and updating with sudo freshclam) but also run some kind of realtime scanning software on your windows partition. like avg.

Clamav, although a great virus tool, is a not a realtime scanner, so remember that you will have to actively scan the thumb drive.

I personally use clamav because I share files with my windows buddies and I dont want to infect them incase I download an infected file and I am unware of it, but being on ubuntu, i dont worry about viruses as I would on a windows or mac machine.

---

### Post by Arisha on 2010-03-15
What about viruses I use firewall such as Protemac Netmine. I have Leopard and use it for protects against viruses.It&#8217;s helps me a lot.

---

### Post by karthick87 on 2010-03-15
What is Leopard?

---

### Post by mastablasta on 2010-03-15
MacOS from Apple i believe. has nothing to do with linux and has probably even less viruses than linux. although lately their numbers are increasing.

---

### Post by mike555 on 2010-03-15
You could get a USB drive with a built-in switch to make it read-only .like ;
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820183232&Tpk=ridata%20slider](http://www.newegg.com/Product/Product.aspx?Item=N82E16820183232&Tpk=ridata%20slider)

---

### Post by mastablasta on 2010-03-15
from Clam AV site:
[LIST]
[*]command-line scanner
[*]fast, multi-threaded daemon with support for on-access scanning
[*]milter interface for sendmail
[*]advanced database updater with support for scripted updates and digital signatures
[*]virus scanner C library
[*]**on-access scanning (Linux® and FreeBSD®)**
[*]virus database updated multiple times per day (see home page for total number of signatures)
[*]built-in support for various archive formats, including Zip, RAR, Tar, Gzip, Bzip2, OLE2, Cabinet, CHM, BinHex, SIS and others
[*]built-in support for almost all mail file formats
[*]built-in support for ELF executables and Portable Executable files compressed with UPX, FSG, Petite, NsPack, wwpack32, MEW, Upack and obfuscated with SUE, Y0da Cryptor and others
[/LIST] 
By the way i think Avira Antivir has a antivirus for linux i also saw some others companies offering it. is that looking only for Windows viruses?

---

### Post by karthick87 on 2010-03-27
Is there anyway to protect it from autorun virus?Clamav doesn't detect autorun virus...

---

