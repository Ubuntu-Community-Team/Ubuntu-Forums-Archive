---
title: "Mounting Nexstar LX NAS in Hardy?"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Shinobi326 on 2008-04-25
When I was running 7.10 I had an entry in my /etc/fstab to mount my Nexstar NAS fileshare:

//192.168.1.xxx/public /mnt/nas_disk smbfs defaults,rwx,uid=1000,auto 0 0

I just did a fresh install of Hardy Heron, I installed samba from the repositories, I created the folder /mnt/nas_disk, then I edited my FSTAB file but it's not working.  It keeps asking me for a password and I've tried changing smbfs to cifs but I keep getting the following
 ```
Password: 
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

I've seen some other threads saying that the Nexstar LX is not compatible with CIFS.  So if that is the case, how do I get this to work?

---

