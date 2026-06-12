---
title: "SMB mounts don't show up on the desktop"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Wolverine222 on 2007-06-21
Hello there,

I'm trying to migrate the workstations in the company from Win to Ubuntu. One of the critical points is the use of network shares, that are already working. But since the openoffice suite has a problem handling smb:/ addresses, and also as a matter of commodity for the users, i decided to automount the shares locally, in the fstab.

Now here's my problem, in the fstab i have some shares which are password protected and some shares that are available to guests. ALL the shares mount perfectly, but only the password protected ones appear on the desktop....

the fstab lines are:

# Unprotected shares
//servername/share1 /mnt/servername/share1 smb guest 0 0
# Protected shares
//servername/share2 /mnt/servername/share2 smb username=<user>,password=<pass> 0 0

any ideas are welcome

(all machines are using Ubuntu 7.04 with all the updates)

---

### Post by dmizer on 2007-06-21
mount your shares in /media/servername/shareX

then they will appear on your desktop.

for more information, see the second link in my sig.

---

### Post by Wolverine222 on 2007-06-22
ok, that worked.

Still i find it mighty strange that when i mount somewhere else only the protected ones appear...

thanks

---

### Post by dmizer on 2007-06-22
frankly, i'm surprised that any appeared on the desktop at all.  so, yes ... strange.

but i don't have much experience with feisty yet so i can't say too much.

---

