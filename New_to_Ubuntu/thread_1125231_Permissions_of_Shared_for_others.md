---
title: "Permissions of Shared for others"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Arthurgibbs on 2009-04-14
Ok i wanted to make my old pc a shared file server for my house.
the idea was it would wake on lan and host a ftp client and a shared network file space for local machines..

as i was networking with windows machines i partitioned my drive into 2 parts 10 gigs for linux and aplications and stuff in a jornaling file system,, the other 50 gigs were in a fat 32 partion on the mount /shared...

after installing file sharing it did not let me do it as it did not have the relivant permitions.. the permisions were  RWXRWX---
so i went to the terminal found the directory and typed chmod -R a=rwx that failed so i did sudo chmod -R a=rwx   this also failed
chown also failed

how so i change the permitions so that it is rwxrwxrwx,,,so that everyone on the network and use it how they like.....
$/shared is the path of the directory....

ps also how do i enable wake on lan in ubuntu.

---

### Post by davetv on 2009-04-14
chmod 777 * -R 

should do it

---

### Post by Iowan on 2009-04-14
> **Arthurgibbs said:**
> ps also how do i enable wake on lan in ubuntu.[Here]("http://ubuntuforums.org/showthread.php?t=234588") is a How-To.
[Another]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=603620") that *might* be useful.

---

### Post by Arthurgibbs on 2009-04-16
chmod 777 -r fails just like chmod A-rwx -r failed...

as they are the same...

terminal repiles with "operation not permited" even with sudo" Even logged in as root....


DRWXRWX--- 4 Root Plugdev 32750 1984 01 01 01 00 Shared


is the directory in question

---

### Post by Paddy Landau on 2009-04-16
Please show us the **exact** command that you typed (with sudo), and the **exact** message that it gave, in full.

---

