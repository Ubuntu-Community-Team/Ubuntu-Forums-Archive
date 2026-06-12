---
title: "Mount folder on localnetwork"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Xaziva on 2008-05-02
I want to mount smb://boden/pfilm/ as /home/jonathan/boden
How do I do?

---

### Post by Paris Heng on 2008-05-03
> **Xaziva said:**
> I want to mount smb://boden/pfilm/ as /home/jonathan/boden
How do I do?

Please someone reply to this, i also want to know.

---

### Post by lswest on 2008-05-03
go to places-->connect to server  then choose from the drop down "custom location" and add the path there ("smb://[server]/[share]") - ah, didn't see you want to mount it as a home folder :S hmm...you could probably mount it then edit the path to your home folder using gconf-editor.  not 100% sure that will work though.

---

### Post by Xaziva on 2008-05-03
Anyone?

---

### Post by Paris Heng on 2008-05-03
> **Xaziva said:**
> Anyone?

I try ask in other forum for u, nobody reply yet.

---

### Post by Paris Heng on 2008-05-04
First create the directory /home/jonathan/boden on the local machine.

Then read the man page for mount
[http://linuxcommand.org/man_pages/mount8.html](http://linuxcommand.org/man_pages/mount8.html)
[http://linuxcommand.org/man_pages/smbmount8.html](http://linuxcommand.org/man_pages/smbmount8.html)
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)
[http://linux.die.net/man/8/smbmount](http://linux.die.net/man/8/smbmount)

mount -t cifs //server/share /mnt --verbose -o user=username

mount -t smbfs

Also see man pages for
ssh
ftp

:guitar:

-----------------------------
[Paris Heng @ Wifi-Linux]("http://parisheng.110mb.com/")

---

