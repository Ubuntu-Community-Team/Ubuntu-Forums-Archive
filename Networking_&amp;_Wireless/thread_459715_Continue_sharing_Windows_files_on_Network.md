---
title: "Continue sharing Windows files on Network?"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by reggierabbit on 2007-05-30
Hi,

I just installed Kubuntu Feisty on my computer with Windows XP, so i am dual booting. I had files being shared on Windows across the network. Is there any way i can continue sharing those fies when im in Kubuntu?

Another question is, can you share files from Kubuntu on the network to Windows computers?

BTW: All of the computers on my network are running Windows XP

Thanks

---

### Post by benanzo on 2007-05-31
Yes.  You need to have a look at *samba*.  That is the package that implements the SMB protocol for sharing files/printers with Windows machines.

---

### Post by reggierabbit on 2007-06-05
It says you need to put the files in home to share them , can i stop this from blocking me?

---

### Post by benanzo on 2007-06-07
Yeah.  You can share whatever files on your system you want.  Read through the */etc/samba/smb.conf* file.  That is where you designate all the options and and set your shared folders.  There is a lot of good information in there.

---

