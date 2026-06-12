---
title: "Mounting samba shares"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by incoming429 on 2007-06-10
Hi!

I have some problems when using samba shares on my laptop. I mount the shares from /etc/fstab and when the connection is ok, everything works flawlessly. The problem is, when the laptop gets disconnected (for example losing wireless signal or not being connected at boot), the smb connections are "frozen", for example, if I do "ls /media/mounted_share", it waits for a few minutes and then reports I/O failure. The only way to get it back to work is making sure nothing is trying to access the mounts, umount them and mount -a. This also happens when booting without connection to the file server. I just have to umount the non-mounted shares and mount them manually. And it gets even worse as I have symlinks to the shares on my gnome desktop. The desktop just freezes and the shares can't be umounted until it timeouts, which does take some time.

Does any of you know a way to make this more painful, for example to make it work like windows does (when disconnected the shares are just inaccessible)?

Thanks!
Michal

---

### Post by spd106 on 2007-06-12
Are you using smbfs or cifs to mount the smb shares?

I have heard that cifs is better, though I don't use either myself, so I'm sorry if that doesn't help.

---

### Post by incoming429 on 2007-06-14
Hey,
yeah I heard that as well. I played with both of them with the same results. Cifs (at least on my system) has an additional problem that Ubuntu doesn't umount it properly when rebooting/shutting down. It always shows some messages about share not responding (even when mounted/connected properly), waits for a few minutes and then reboots. So I use the less-evil smbfs :-)

Michal

---

### Post by dmizer on 2007-06-14
incoming429, please try the second link in my sig.

to solve your shutdown problem, take a look at the last page.  i posted a link to a fix for the cifs vfs: server not responding in post #282.  if you test it for me and find that it fixes the problem, i'll link to it on the first page of my howto.

---

### Post by incoming429 on 2007-06-14
Hey dmizer,

I just tested with that init script and my laptop now reboots properly with cifs shares mounted.
Thanks,
Michal

---

