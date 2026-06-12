---
title: "Stupid Samba Question"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by Drunky on 2008-07-09
This may be a tragically stupid question...

Say I have two computers, one running Ubuntu and the other running XP, and I want to set up Samba to connect between them.  This is a simplification, the problem is actually much more complicated.

I want the XP computer to be able to read and write data from and to the Linux machine.  When I formatted the second drive in my Linux machine I should probably use NTFS.

Okay, here's the question:  If I formatted the second drive on the Ubuntu computer as ext3 then Samba will let XP see the drive but XP will not recognize the file system, correct?

Thank you in advance for your experience and pity.

Drunky

---

### Post by heidfirst on 2008-07-09
Hi,

The filesystem on the linux box should not matter to the windows XP machine, Samba will hide the actual file system from it.

My linux server uses JFS for the file system and my network has Windows XP home and pro machines that access it, and the rest of the family have not complained about any problems using the samba shares that it provides.

Hope this helps

Gordon

---

### Post by superprash2003 on 2008-07-09
right.. you could use any filesystem it would work via samba

---

### Post by dmizer on 2008-07-09
samba does not control the filesystem, samba only controls the transfer protocol.  samba simply tells the ubuntu filesystem what needs to be written to the disk.  so really, it doesn't matter WHAT file system you've formatted your drives in on either windows or ubuntu.

the only time that drive formats become a problem is when both xp and ubuntu reside on the same disk, or in the same computer.  so when you're booted in windows, it cannot see the ubuntu file system.

---

### Post by Drunky on 2008-07-09
thanks for the replies

---

