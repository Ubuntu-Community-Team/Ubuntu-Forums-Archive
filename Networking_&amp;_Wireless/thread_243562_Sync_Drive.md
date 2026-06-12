---
title: "Sync Drive"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by michellembrodeur on 2006-08-25
What programs can I use to sync to drives across a network.

Thanks all

---

### Post by nephish on 2006-08-25
My favorite way, if you have ssh access, is unison ( and unison-gtk )

i do this every day when i get home from work, sync up the changes in two folders, one on my home system, one on my work system. one click, enter password, it shows the changes, click update. 

easy.
hope this helps.

---

### Post by morikaweb on 2006-08-25
How do I go about setting up a SSH Server?

BTW michelle is my roomate :)

---

### Post by nephish on 2006-08-25
use synaptic, or apt-get 
its either ssh-server, ssh, or openssh or some such.
when it asks you if you want to set up the server, select yes.
then apt-get install unison-gtk

---

### Post by Woei on 2006-08-25
> **michellembrodeur said:**
> What programs can I use to sync to drives across a network.

Thanks all

Probably the most standard tool to mirror directory contents over a network is **rsync**. 
```

 apt-cache show rsync | tail -n12
Description: fast remote file copy program (like rcp)
 rsync is a program that allows files to be copied to and from remote
 machines in much the same way as rcp.  It has many more options than
 rcp, and uses the rsync remote-update protocol to greatly speed up
 file transfers when the destination file already exists.
 .
 The rsync remote-update protocol allows rsync to transfer just the
 differences between two sets of files across the network link.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-standard, kubuntu-standard, edubuntu-standard, xubuntu-standard

```

The options and possibilities of this tool are almost endless, and it has a pretty good manual page. It can be a tad overwhelming for new users, and you can overwrite data if you don't know what you're doing. 

But still, rsync over ssh is the combo most frequently used on Unix systems.

---

