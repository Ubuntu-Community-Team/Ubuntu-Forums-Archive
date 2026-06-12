---
title: "Map home folder to Windows server share"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Goosemoose on 2007-11-14
Hi,

I'm running setting up about 300 edubuntu machines for our school and am working on getting them to play nicely with our existing windows domain. I have the systems authenticating against the domain controller at login which was the most important part.

I'd like some direction on the next step which is mapping the /home/domain/user folder to their current windows documents folder. All students when logging into the domain xp machines have their my docs mapped to a folder on the server based on their member group. So there 4 places for students to be //server/2008/user //server/2009/user and so on. 

What do I need to do so that when a student logs into the ubuntu machines their home folder is actually on the server? That way as the students roam from machine to machine, whether windows or ubuntu, all their docs will be there. A few guys in the #edubuntu irc channel suggested using the pam-mount package but there seems to be little documentation on it. Do I just mount it in the fstab folder?

Any help would be greatly appreciated!

Thanks

---

### Post by Goosemoose on 2007-11-15
Nobody has any ideas?

---

### Post by farruinn on 2007-11-15
I think pam_mount is probably your best bet. Otherwise I think you'd have to enter a line for each user into fstab on every machine. Did you try the man page for lib_pam and looking through /etc/security/pam_mount.conf? I haven't used this myself, but there does appear to be a fair amount of information there.

Good luck!

---

### Post by farruinn on 2007-11-19
I don't know how this would work for smb, but I just remembered that at my college we used an NFS mount for /home. So maybe you can mount \\Server\2008 to /home/domain? Since you have their windows documents folders in 4 places on \\Server it may not be so simple, but I thought I'd mention it since I just remembered this.

It would seem to me that this is possibly a common task administrators would face deploying edubuntu on any decent scale in a school (using an existing Windows domain with hundreds of edubuntu clients). Perhaps it's something the edubuntu team should investigate streamlining.

---

