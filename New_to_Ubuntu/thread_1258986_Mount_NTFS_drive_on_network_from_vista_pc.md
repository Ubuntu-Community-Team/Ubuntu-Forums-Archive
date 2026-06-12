---
title: "Mount NTFS drive on network from vista pc"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by ekraus on 2009-09-05
I have a  laptop running vista.
I just loaded ubuntu on an old pc  so I am new to the operating system.
On it is a 40GB drive that is dual partitioned with XP and ubuntu there is also another 250GB drive that has NTFS partitions.
I want to be able to use my backup software to write files on the NTFS partitions residing on the ubuntu pc.
I could use some help.
Thanks in advance

---

### Post by yeats on 2009-09-05
I don't have much help for you, but I will say that getting Vista to play nicely over the network with my Samba share hosted on an Ubuntu box has been, er.... unpleasant.  I had to do a lot of research, as Vista adds new layers of complexity to Windows networking, which used to be pretty straightforward :-).

As for setting up your Ubuntu machine with Samba, there are many good sites out there with (relatively) easy-to-follow instructions.

---

### Post by ekraus on 2009-09-05
So let me get this strait. I need Samba on the Ubuntu machine to be able to mount the NTFS drives on it from another machine.
By the way they are all mounted on the Ubuntu machine.

---

### Post by yeats on 2009-09-05
> **ekraus said:**
> So let me get this strait. I need Samba on the Ubuntu machine to be able to mount the NTFS drives on it from another machine.
By the way they are all mounted on the Ubuntu machine.

Yes, that's right - the package is *samba* in Synaptic.  Samba is configured by files in the /etc/samba directory, especially the smb.conf file.  I don't know of a GUI-based way to set Samba up, but there may be one.

---

