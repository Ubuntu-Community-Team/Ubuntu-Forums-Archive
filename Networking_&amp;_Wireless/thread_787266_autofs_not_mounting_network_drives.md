---
title: "autofs not mounting network drives"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Ancientmtk on 2008-05-08
I have a server running on redhat ws3 and a new ubuntu 8 client that im trying to get to mount server drives.  The ubuntu box can ping the server and i can manually mount the server drives by doing

mount server:/export/disk1 /shared

but when i utilize autofs, its not working.
The daemon.log file says something about "automount: failed to mount /shared/.Trash" or something along that line.

What is wrong here, the autofs or maybe the config files?

---

### Post by njparton on 2008-05-09
Try using NFS instead:
 
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html)
 
(this still applies for 8.04).

---

### Post by Ancientmtk on 2008-05-09
I can't use NFS because i need the mount to time out after a 3min mark.  I think only autofs can handle this right?

---

### Post by njparton on 2008-05-09
I don't know to be honest, possibly but you'd have to do some research into it.

---

### Post by mal on 2008-05-12
I'm having the same issues.  I have a machine with Ubuntu Hardy and have a network drive exported from another machine running Gutsy.  When I try to access the automount share, I get "no such file or directory" and get an automount "failed to mount" message in syslog.

This seems to have only developed in the last few days after some Hardy upgrades.  It seemed to be working when I first set it up a week or so ago.

I also get various "failed to mount ... /.Trash" messages in syslog when autofs is restarted.  However, this seems to be subject to a bug in launchpad that is in the process of being fixed.  I don't think any of the current bug reports really cover our situation.  If there seems to be other people with the same problem, I might raise a bug report on this matter.

Regards,

Mal

---

