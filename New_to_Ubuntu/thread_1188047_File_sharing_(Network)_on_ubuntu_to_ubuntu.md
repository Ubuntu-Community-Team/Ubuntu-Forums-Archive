---
title: "File sharing (Network) on ubuntu to ubuntu"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-15
I know Samba is so windows and ubuntu can talk,
but how do I setup networking and file sharing between other ubuntu computers?

I just put the family on ubuntu, and need to share some things =)

Also how do I share media?

---

### Post by zerhacke on 2009-06-15
If you have SAMBA running on one linux host, you can connect to it with a linux client using the smbfs package.  If you want it to mount automagically every time they start up their linux client, you'll need to edit /etc/fstab

---

### Post by Celauran on 2009-06-15
Depends how the network is set up. Samba might still be a viable option. Have you looked at NFS?

---

### Post by zerhacke on 2009-06-15
NFS is another solution, yes, but if he's already familiar with SAMBA there's no real reason to switch.

---

### Post by superprash2003 on 2009-06-15
nfs is usually for a linux only network.. samba is used when both linux and windows machines are on the network.. samba works linux to linux as well

---

### Post by Iowan on 2009-06-15
How familiar are you with Samba - Used it, set it up, or heard about it? Are there Windows computers to be considered, or is it Ubuntu-only (your post makes it sound like sharing will be between Ubuntu machines only).  [Here]("http://ubuntuforums.org/showthread.php?t=249889") is a recommended How-To for NFS, and [another]("https://help.ubuntu.com/community/SettingUpNFSHowTo") somewhat more involved one.  [https://help.ubuntu.com](https://help.ubuntu.com) is a good source for other help pages in case you'd rather try a different sharing method.

---

### Post by SoftwareExplorer on 2009-06-15
Right click on a folder you want to share and click sharing options. Check share this folder. (and guest access makes it so you don't have to use a password) If you haven't shared files before on the computer it will install Samba. If this happens, you may be logged out and you'll have to log in. Other times, it just works.

Once that is done click create share.

On the computer that you want to get the files from, go to Places -> Network.

---

### Post by scrooge_74 on 2009-06-15
NFS is extra easy to set up, even more than SAMBA, you basically only need to know the IP of the other machine.  

You can also log using ssh conections from one PC to the other

---

### Post by SoftwareExplorer on 2009-06-15
> **scrooge_74 said:**
> NFS is extra easy to set up, even more than SAMBA, you basically only need to know the IP of the other machine.  

You can also log using ssh conections from one PC to the other

When I looked at [this guide]("http://ubuntuforums.org/showthread.php?t=249889"), I was like, that looks complicated, I'll use samba with its nice GUI. Sounds like NFS can do some interesting things thought.

---

### Post by scrooge_74 on 2009-06-15
Yep, that is a good guide, I have followed it in the past.  Remember it also contains security advice, the moment you are sharing something is open to others to see or to try to see it.

The way to go should be NFS, which is the linux way of doing it (which is more secure), SAMBA is a solution, but not the best in this case.

---

### Post by nandemonai on 2009-06-15
ssh / scp / sshfs are also viable secure alternatives.

---

### Post by Gp. on 2009-06-21
> **SoftwareExplorer said:**
> Right click on a folder you want to share and click sharing options. Check share this folder. (and guest access makes it so you don't have to use a password) If you haven't shared files before on the computer it will install Samba. If this happens, you may be logged out and you'll have to log in. Other times, it just works.

Once that is done click create share.

On the computer that you want to get the files from, go to Places -> Network.

There is no sharing options...option lol
There used to be but it's gone now.
Is there a package I need?
Samba is already installed.

***EDIT***
Found it.
Related to this
[http://ubuntuforums.org/showthread.php?p=7495412#post7495412](http://ubuntuforums.org/showthread.php?p=7495412#post7495412)

---

