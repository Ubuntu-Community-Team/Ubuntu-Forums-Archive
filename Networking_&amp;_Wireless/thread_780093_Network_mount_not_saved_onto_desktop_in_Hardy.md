---
title: "Network mount not saved onto desktop in Hardy"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by InSearchOf on 2008-05-03
Yup... did the upgrade from 7.10 to 8.04 the other night, and it seems to have been ayyy ookay, except from some minor issues. One of these issues is the topic of this thread. When I mount a network share in Nautilus (either by browsing or using Places -> Connect to Server) the netwok share is mounted and it appears on my desktop. Nice. Problem is after restarting... the network share is then gone, not saved, disappeared etc... I have to do the mounting all over again. This was not an issue in 7.10 (or maybe it was? i cannot recall having to fix it). So - any ideas on how to fix this? (oh.. yes, i have tried to "bookmark" in the Connect to Server window, but no luck there)

Thanks,
.isof :-D

---

### Post by Norst on 2008-05-03
To have a nfs share mount at startup add it to your fstab.

I found out how here:
[http://www.faqs.org/docs/linux_network/x-087-2-nfs.mountd.html]("http://www.faqs.org/docs/linux_network/x-087-2-nfs.mountd.html")

Hope this helps,
Norst

---

### Post by InSearchOf on 2008-05-05
Thanks, but not sure if I did the right thing here... I'm a bit blank in the world of linux... 

Anyway, I added this to etc/fstab:
---------------
#nfs
192.168.0.102:/dilldall /mnt/nfs nfs rw,hard,intr 0 0
---------------

Still no network share after boot. The share I am accessing is a Samba-share on a Ubuntu 8.04 OS. I am still able to mount it by browsing in Nautilus. No problem doing that.
If i try to mount in terminal i get this errormsg:
-----------------------
sudo mount 192.168.0.102:/dilldall
mount: wrong fs type, bad option, bad superblock on 192.168.0.102:/dilldall,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
------------------------

I'm pretty clueless what to do next...
.isof

---

### Post by richbl on 2008-05-07
> **InSearchOf said:**
> Yup... did the upgrade from 7.10 to 8.04 the other night, and it seems to have been ayyy ookay, except from some minor issues. One of these issues is the topic of this thread. When I mount a network share in Nautilus (either by browsing or using Places -> Connect to Server) the netwok share is mounted and it appears on my desktop. Nice. Problem is after restarting... the network share is then gone, not saved, disappeared etc... I have to do the mounting all over again. This was not an issue in 7.10 (or maybe it was? i cannot recall having to fix it). So - any ideas on how to fix this? (oh.. yes, i have tried to "bookmark" in the Connect to Server window, but no luck there)

Thanks,
.isof :-D

I know to what you're referring. In prior releases, a mount created from Places/Connect to Server would persist across sessions. 

Interestingly, this is no longer the case. Furthermore, it appears that when I create a mount point via Places/Connect to Server, it actually creates two links on the Desktop. 

Oddly, I also get an error message each time I follow this procedure: "The specified location is not mounted." Yet, the mount point is, in fact, created.

Sounds suspiciously bug-like to me.

---

### Post by richbl on 2008-05-07
> **richbl said:**
> I know to what you're referring. In prior releases, a mount created from Places/Connect to Server would persist across sessions. 

Interestingly, this is no longer the case. Furthermore, it appears that when I create a mount point via Places/Connect to Server, it actually creates two links on the Desktop. 

Oddly, I also get an error message each time I follow this procedure: "The specified location is not mounted." Yet, the mount point is, in fact, created.

Sounds suspiciously bug-like to me.

Indeed, this is a known bug (#216104). I've added my observations for completeness.

Fingers crossed for a fix sometime soon.

---

