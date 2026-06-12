---
title: "automounting samba share"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by wishartz on 2006-10-26
Can anybody help me with automounting a samba share in Ubuntu.  I know how to do it with Fedora, but I the same procedure does not work in Ubuntu.  I cannot find any solutions to getting this to work on Ubuntu, I can see plenty of posts where people have tried and failed.  I have searched google for sites about automounting samba shares in Ubuntu, but alas, no solution.

This is what I use in Fedora:

I edit the /etc/auto.master file to point to the auto.misc file and a timeout of 30 seconds and then in the auto.misc file I put in the following:

movies       -fstype=cifs,credentials=/etc/smb.auth    ://tyler/movies

and create a file /etc/smb.auth with my username and password and it just works, but not in Ubuntu.

Please help it's driving me crazy.

---

### Post by Iowan on 2006-10-26
See if the 3rd link in my sig helps...:D

---

### Post by wishartz on 2006-10-27
Thanks for your help, but that is not automounting, it is for static mounting, which I already know how to set up.  Automounting is where you edit the /etc/auto.master and /etc/auto.misc files and make sure the autofs service is running.  I cannot seem to find any information about how to do it in Ubuntu.

---

