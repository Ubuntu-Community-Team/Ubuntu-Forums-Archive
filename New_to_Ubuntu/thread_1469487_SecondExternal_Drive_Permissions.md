---
title: "Second/External Drive Permissions"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by rampageoberon on 2010-05-02
Hello,

I have two hard drives on my machine, one EXT4 and the other NTFS.

When using Hardy, mounting the second hard drive (NTFS) once logging in would do so with full read/write/execute permissions to all users (owner root).

With Lucid, mounting the second drive (NTFS) once logging in gives full read/write/execute access only to my main user. Now I also have alternate logins that I have created on the machine, which can not access any of the content on the drive.

In essence, the selective permissions ability is nicer in Lucid, but how can I give alternate users read permissions at the least? "chmod -R 755 /path/to/drive" doesn't work as permissions just stay at 700.

Please help.

Thanks,

---

### Post by warfacegod on 2010-05-02
Try using Users & Groups and adding those users to either your usergroup or to root's.

---

### Post by rampageoberon on 2010-05-02
> **warfacegod said:**
> Try using Users & Groups and adding those users to either your usergroup or to root's.

Thanks for the reply.

The addition to my usergroup won't work as permissions remain at 700, so even the group doesn't have read permissions, no am I able to give the required permissions.

Thanks,

---

### Post by warfacegod on 2010-05-02
I'd suggest "chown"ing the drive but I don't think that works on NTFS.

---

### Post by rampageoberon on 2010-05-02
> **warfacegod said:**
> I'd suggest "chown"ing the drive but I don't think that works on NTFS.

Nope that can't work as then the main user looses access. Need multiple users to have access unfortunately.

Thanks,

---

### Post by kubug on 2010-06-21
I got the same issue here. Multiple users and external drive, that which ever user is logged in can see, but once switched to other user, is not available no more. 

It's NTFS as well since it needs to be interchangeable to with windows. 

Anybody got any ideas?

---

### Post by rampageoberon on 2010-07-03
i like the idea about selective user privilages on ntfs drives - but haven't had the time to review properly during mount.

What you can do (what used to hapen on hardy where mounted with 777 perms):
[LIST=1]
[*]Use 'blkid /dev/<id>' to identify drive UUID
[*]Create a directory to mount drive - 'mkdir /mount/point'
[*]then insert the following entry into /etc/fstab - UUID=<UUID> /mount/point ntfs-3g rw,defaults 0 0
[/LIST]

This will mount as root owner with 777 perms. Hope that helps.

---

### Post by kubug on 2010-07-04
Hi rampageoberon,

Thanks for that suggestion. I already tried doing it that way. The problem with that is that it becomes a permanent mount, and as soon as you remove the external it will not reconnect until you reboot the computer with it attached.

Still looking for a solution right now.I would simply like that all users can access the temporary mounts.

---

### Post by jtarin on 2010-07-04
Try [here]("http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/") for everything you always wanted to know about NTFS-3G permissions, but were afraid to ask. :)

[And here for mounting.]("http://www.tuxera.com/community/ntfs-3g-faq/#plugandplay")

NTFS-config is a great tool...you can find it in the repository.

---

