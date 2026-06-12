---
title: "Samba mount is read only"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by jethro10 on 2006-11-30
Hi,
sorry about this but i'm stuck with samba. I can mount a windows drive, but it appears read only. I need to use fstab as I need it accessible via the command line.

I creat a mount point in my home directory, lets say ~/mountpoint

and in fstab I put:-
//servername/sharename /home/me/mountpoint smbfs username=defaults,password=defaults 0 0

this works but gives read only permissions to ~/mountpoint

the permissions on the folder give an owner as root, not me!
also if I try to give everyone write permissions by ticking the box, it tells me to go away.

If I mount via nautilus, I can write to the drive ok.

It on dapper LTS.

any ideas?

J

---

### Post by jethro10 on 2006-11-30
Sorry, for any inconvenience I fixed it using this thread.

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

which I didn't find by searching here, but by searching google for this :-

fstab smbfs howto

thanks
Jeff

---

