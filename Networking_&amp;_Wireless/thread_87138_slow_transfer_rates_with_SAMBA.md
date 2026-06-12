---
title: "slow transfer rates with SAMBA"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by samir85 on 2005-11-07
Hey guys,

I just switched from Gentoo to Ubuntu. 

Anway my computer is in a 100 mbit home network with several windows maschines. So I want to transfer data between my Ubuntu maschine and the other windows computers. Unfortunately the transfer rates are really slow ! (In both way; Linux Computer -> Windows Computer; Windows Computer -> Ubtuntu Computer)

I mean there must be something, when transfering around 1 GB takes almost 1 hour !


I'd appreciate any kind of help


Greets Samir

---

### Post by samir85 on 2005-11-09
* Bump *

---

### Post by mips on 2005-11-09
Here is one suggestion  [http://ubuntuforums.org/showthread.php?t=78386&highlight=slow+samba](http://ubuntuforums.org/showthread.php?t=78386&highlight=slow+samba)

---

### Post by Robo on 2005-11-09
I beleive I had this problem before, and it had to do with PAM authentication/user rights.  Though it was on another distro, it may be a place to start.  Check your logs, it may point you in the right direction.

---

### Post by samir85 on 2005-11-10
First of all thanks for the answers :)

[quote=mips]Here is one suggestion [http://ubuntuforums.org/showthread.p...ght=slow+samba](http://ubuntuforums.org/showthread.p...ght=slow+samba)[/quote]
I think the link you gave me does not cover my problem, because the transfer rates here are constitantly slow and now just the first 6 seconds like in the other thread.

[quote=Robo]I beleive I had this problem before, and it had to do with PAM authentication/user rights. Though it was on another distro, it may be a place to start. Check your logs, it may point you in the right direction.[/quote]
Hey this sounds interesting. Could you carry out this issue a little ?

---

### Post by Robo on 2005-11-10
What I did to prove this theory was to create an ftp server on my linux box, and transfered some large files between the windows box and linux system.  I watched the transfer speeds reach the max for my network.  Once I was able to prove that it was strictly to do with file sharing using samba, I went in and changed the pam setup using webmin, to allow authentication to be "Optional" for the pam_stack.so modules, so it did not matter if the client was authenticated or not.

Hope this helps, it was a long time ago I had to do this, so going by memory :)

---

### Post by BIGtrouble77 on 2005-11-15
[QUOTE=Robo]What I did to prove this theory was to create an ftp server on my linux box, and transfered some large files between the windows box and linux system.  I watched the transfer speeds reach the max for my network.  Once I was able to prove that it was strictly to do with file sharing using samba, I went in and changed the pam setup using webmin, to allow authentication to be "Optional" for the pam_stack.so modules, so it did not matter if the client was authenticated or not.

Hope this helps, it was a long time ago I had to do this, so going by memory :)[/QUOTE]
Do you know where the pam stack settings are? I have the samba module installed, but I couldn't find anything related to pam.

I just want to say my samba network is also deathly slow.  I haven't tried copying to any other linux machines yet, but copy to and from a windows share is a nightmare, it's slower than usb1.

---

### Post by wassim1980 on 2005-12-22
I get this same issue gents, very frustrating as I can download a file from the internet faster than a simultaneous file transfer to a Windows file share on the same network. Any ideas about the PAM recommendations Robo? I can't seem to find anything about that.

---

### Post by Jose Catre-Vandis on 2006-05-20
After recent dapper updates, my fat32 network shares are very slow to load and use across my LAN. ntfs and linux shares are lightning quick. All were same speed previously. Any suggestions?

---

### Post by theh0g on 2006-05-27
*bump*

---

### Post by Jose Catre-Vandis on 2006-06-03
anyone?

---

### Post by kdawgud on 2006-06-05
[QUOTE=Jose Catre-Vandis]After recent dapper updates, my fat32 network shares are very slow to load and use across my LAN. ntfs and linux shares are lightning quick. All were same speed previously. Any suggestions?[/QUOTE]

I'm having a similar problem with dapper.  All network activity is fine except for samba transfers.  (Samba was working fine for me previously under FC3, connecting to the same windows computers I'm trying to do now).   I found if I use smbclient to connect, I can use the -b option to reduce the buffer size and this speeds it up incredibly.  I can't figureout how to do the same thing with smbmount, however.

---

### Post by Jose Catre-Vandis on 2006-06-07
OK, I have half solved this. Now nautilus is browsing network shares properly again, I noticed how fast it was at opening the fat32 share, which is slow under samba.

So I right clicked on the desktop, created a launcher, typed:
> nautilus smb://10.10.10.50/share
in the command box
(where 10.10.10.50 is the IP of the sharing computer and "share" is the shared fat32 folder)
picked an icon, and I now have a speedy route to this share!

This crazy ubuntu world, where last week I couldn't see the network under nautilus, and this week its the quickest way to get at my network shares :-)

---

### Post by scottpreston on 2006-10-26
any fixes here? i get good performance with VNC running in the background, I shut down VNC, poor perf., I bring it up, VERY FAST.

---

