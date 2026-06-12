---
title: "Try to mount NFS share from Suse server - failed - not host:dir-format"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by AndreasMeier on 2005-06-12
Hi all,

I'm trying to mount a NFS share on my Suse 9.1-Server.

I changed recently on my client from Debian Sarge to Kubuntu Hoary.
In Sarge the mount of the NFS was working well.

Now when I try to "mount -t nfs //IP-Adress/folder /mountpoint -o username=andreas

I'm receiving an error message : folder not in host:dir-format

and I'm not finding any answer to this problem which relates to Ubuntu.


Has anyone of you the same problem or perhaps a hint or solution for me ?

Thanks in advance,
Kind regards,
Andreas

---

### Post by Amarack on 2005-06-12
The command should look more like:
mount -t nfs IP-Adress:/pathto/folder /mountpoint

I don't think the username is an option for nfs, it looks like that command was what you would need if instead of nfs you were doing smbfs.

---

### Post by AndreasMeier on 2005-06-12
Thanks for your answer, but its not working.
I tried "mount -t nfs 192.168.0.2:/data /data"
but then my bash prompt did not return  :?: 
Is the ":" in the middle correct ?
But without I'm receiving the same error message as posted.

Regards
Andreas

---

### Post by alastair on 2005-06-12
You have the NFS client (common) package installed?

nfs-common

The service is started?

/etc/init.d/nfs-common restart

You can use the "showmount" command to list exported filesystems on a server i.e.

showmount -e <servername>

e.g.
showmount -e 192.168.0.2

Check the system log i.e. in another terminal do :

tail -f /var/log/syslog

(and check the server log as well)

Then, in a different terminal :

mount -t nfs 192.168.0.2:/data /data

---

### Post by tflovik on 2005-06-12
What i had to do to mount NFS from Ubuntu/Kubuntu Hoary was to install portmap.
Then it worked.

---

### Post by AndreasMeier on 2005-06-12
Thanks to all,

Portmap and NFS-common was installed, NFS-common was stopping and restarting after command /etc/init.d/nfs-common restart.
showmount works also and finally also the mount-command was working.
Dont know exactly what went different but anyways...

Thanks to all
Regards,
Andreas

---

