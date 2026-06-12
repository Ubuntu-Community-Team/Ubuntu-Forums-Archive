---
title: "Server Backup"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Speshal Crayon on 2009-01-08
For a coursework assignment at school it is required that we find an operating system for a server. I have chosen to look at Ubuntu. The OS we choose must enable the user to set up network security, maintain a backup system and provide remote access. 

I've searched on the main site for how to go about maintaining a backup system but really haven't found anything. Does it automatically do it? Do you need to install software to do it? I don't need too much detail, just some basics so that I'm a little less lost.

I know it sounds a little silly but I don't know the first thing about servers, it isn't actually required that we know anything about them, only for this task. Obviously my lack of knowledge isn't helping though. 

Thanks in advance for any help.

---

### Post by albinootje on 2009-01-08
> **Speshal Crayon said:**
> For a coursework assignment at school it is required that we find an operating system for a server. I have chosen to look at Ubuntu. The OS we choose must enable the user to set up network security, maintain a backup system and provide remote access. 

Check out rsync and rdiff-backup for backups, and ssh for remote access.
[http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)
[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)
[http://en.wikipedia.org/wiki/OpenSSH](http://en.wikipedia.org/wiki/OpenSSH)

Installing them is as easy as :
```

sudo apt-get update
sudo apt-get install rsync rdiff-backup ssh

```

For network security read :
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

GL! :)

---

### Post by Speshal Crayon on 2009-01-08
Thank you! :D

---

### Post by handydan918 on 2009-01-08
> **Speshal Crayon said:**
> For a coursework assignment at school it is required that we find an operating system for a server. I have chosen to look at Ubuntu. The OS we choose must enable the user to set up network security, maintain a backup system and provide remote access. 


Network security=ufw/iptables

backup=rsync+ cron

remote access+ssh/sshd

Enjoy.

---

### Post by scorp123 on 2009-01-08
> **Speshal Crayon said:**
> For a coursework assignment at school it is required that we find an operating system for a server. I have chosen to look at Ubuntu. The OS we choose must enable the user to set up network security, maintain a backup system and provide remote access.  Well ... as this is only for a school assignment I'd suggest this: OpenSolaris 2008.11 .... It basically has all the features you want and that are offered by e.g. Ubuntu too. But it has one really jaw-dropping feature: TimeSlider.

See here:
[http://blogs.sun.com/erwann/entry/time_slider_screencast](http://blogs.sun.com/erwann/entry/time_slider_screencast)

You should still combine it with the other methods mentioned by the others, eg. use "rsync" and copy your files to another medium and/or another computer.

OpenSolaris 2008.11 is open source and can be downloaded for free fom Sun Microsystems: 

[http://www.opensolaris.org/os/](http://www.opensolaris.org/os/)

Don't get me wrong ... I like Ubuntu very much, but I guess for a school assignment it can't be wrong to have some nice ZFS snapshot eyecandy .... ;)

---

