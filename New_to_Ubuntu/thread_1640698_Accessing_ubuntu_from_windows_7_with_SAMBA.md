---
title: "Accessing ubuntu from windows 7 with SAMBA"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Avidanborisov on 2010-12-08
Hello everyone!
I installed samba on my ubuntu and i need to access it from my windows 7 laptop.
I followed the tutorial how to do it and my hostname really appears on the network.
but when i try to log in i never succeed. I think it has something with the fact that when i try to log in it always log in with my computer domain name like
LAPTOP\username
What to do?

---

### Post by Avidanborisov on 2010-12-08
anyone?

---

### Post by chamber on 2010-12-08
You could try something like, 

net use (drive letter): \\hostname\sharing_folder /user:hostname\username password /PERSISTENT:YES

Stick it into a batch file like,

> @echo off

net use (drive letter): \\hostname\sharing_folder /user:hostname\username password /PERSISTENT:YES

exit

Worked for a Samba share in work to a solaris machine from an xp machine.

---

