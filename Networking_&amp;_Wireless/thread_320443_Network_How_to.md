---
title: "Network How to?"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by racertj5 on 2006-12-17
Heres my setup so far I have a desktop running windows xp in one room of my house with a cable modem and router connecting it to a network. It is a linksys wireless router.  one of the computers connected to it is connected with a linksys wireless card in my room.  I just put an old computer in here with xubuntu edgy on it. both computers in my room have a netgear wired network card in them with a crossover cable connecting them both.  the internet now works on both computers.  Heres my problem.  I  want all the files on my xp desktop to be accessible via xubuntu and vice versa.  I also want to be able to access the shared files on the linksys network on the ubuntu box as well as the printer that is on another computer on the linksys network.

---

### Post by racertj5 on 2006-12-17
Ok I installed samba and NFS on the xubuntu box.  I now see my linux computer in workgroup computers on my XP box but can't get in. whats next?

---

### Post by racertj5 on 2006-12-19
I cant figure this out please help

---

### Post by dwasifar on 2006-12-19
> **racertj5 said:**
> I cant figure this out please help
Did you set up a samba password file on the ubuntu machine?  You have to specify what users can connect via samba to your ubuntu box, and what password they should use when they connect.

---

### Post by Iowan on 2006-12-20
Have you seen this one?
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

