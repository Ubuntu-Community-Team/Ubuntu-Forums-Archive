---
title: "pain with vsftpd"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by bsh on 2007-11-11
i have set up vsftpd after a long period of problems... but now it seems to be working, expect for one annoying thing.
i have set up a local unprivileged user which is allowed to connect to the ftp server. my username is also allowed, unrestricted.
i can log in with my username anytime, it works great.
the other user can log in when i start the vsftpd server, and works for a while. but after a period of time (1-2 days), when i (or someone else) is trying to connect, it doesn't accept the password anymoer.
then i used to log in via ssh as a superuser, and change the password for this account TO THE SAME password, and right after that, it's possible to login again and accepts the very same password that it didn't accept before.
this is strange.
what could this be?

---

