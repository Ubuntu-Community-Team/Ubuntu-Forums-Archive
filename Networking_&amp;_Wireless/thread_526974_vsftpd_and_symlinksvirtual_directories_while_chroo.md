---
title: "vsftpd and symlinks/virtual directories while chrooted?"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by baersaerk on 2007-08-16
Ok, this is what i want to happen,

user1 and user2 has a link to user1_2 in their homefolder,
user1 and user3 has a link to user1_3 in their homefolder, and so on...

lets say we got a filesystem as such:
/var/ftp/homes/user1
/var/ftp/homes/user2
/var/ftp/homes/user3
/var/ftp/shared_folders/user1_2
/var/ftp/shared_folders/user1_3

since i want to chroot the user i can't use symlinks.

all the users are virtual users if that matters...

If you got a solution, please share it

---

### Post by Vinno on 2008-01-18
Yeah, you can do it by using mount --bind. I wrote some info about this since it keeps coming up [http://www.vinno.net/linux/server/chroot-mount-trick](http://www.vinno.net/linux/server/chroot-mount-trick)

---

