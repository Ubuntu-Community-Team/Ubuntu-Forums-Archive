---
title: "Samba Dependency Error (Gutsy -- new install)"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by leenwebb on 2007-12-30
Hi all,
I just installed Gutsy and am trying to set up Samba.  Nothing fancy, just a totally generic Samba install.  

Here's what I already have installed (came with 'ubuntu-desktop') :
samba-common [3.0.6a-1ubuntu2.3]
smbclient [3.0.6a-1ubuntu2.3]

When I try to share a folder, it says, "Hey, you don't have Samba installed."  So I tried 

sudo apt-get install samba

which fails.  It seems that the package 'samba' depends on samba-common 3.0.6a-1ubuntu2.2 .  Since I have 2.3, it won't install.  I can't remove the existing versions of smbclient and samba-common, because 'ubuntu-desktop' depends on them, and I am not a command-line kind of person (if I can help it). 

(If it makes any difference: here's no 'samba' entry in my /etc/init.d, or in /etc/rc2.d.  I assumed that meant that I didn't have it installed at all, but maybe it means that the initial installation with the rest of ubuntu-desktop burped in some way?)

Any ideas?

Thanks,
Eileen

---

### Post by (((X))) on 2007-12-30
To set up samba goto System->administration->shared folders..or so, you will be asked to install samba...

Try this, if samba still not working:
code:
$ sudo /etc/init.d/samba reload

---

### Post by leenwebb on 2007-12-31
As I said in my original message:

Samba can not install.  There is a dependency issue -- Gutsy installed samba-common 2.3, and installing Samba requires 2.2. 

Similarly, there is no Samba entry in /etc/init.d , so I can't restart it.

---

### Post by (((X))) on 2007-12-31
really strange, I succesfilly installed ubuntu 7.10 with samba about 10 times without issues.

---

### Post by leenwebb on 2007-12-31
Mine doesn't seem to work.  I'd reinstall the whole OS, except that since I'm starting with a LAMP server, I'd have to install the ubuntu-desktop on top, and I don't have an internet connection that can handle that again.

Does anyone know how to fix a broken samba dependency?

---

### Post by kegobeer on 2007-12-31
Have you updated the list recently?  sudo apt-get update

The reason I ask - I just looked at the Synaptic Package Manager and saw that samba, samba-common, and smbclient are at 3.0.26a-lubuntu2.3.

---

### Post by (((X))) on 2008-01-01
No updating or upgrading need! Samba should just work:-\"

---

### Post by leenwebb on 2008-01-02
Thanks, kegobeer!  I actually had done an update, but it must have missed a file (I do have the crappiest internet  connection this side of the Atlantic).  I did it again, and voila!  I can update samba!  Thanks!

---

