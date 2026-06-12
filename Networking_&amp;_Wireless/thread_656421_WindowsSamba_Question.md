---
title: "Windows/Samba Question"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by tcpip4lyfe on 2008-01-02
Im at work right now and Im setting up a samba server.  I am setting up new users and making sure that have access to their folders and it's working fine.  Does anyone know how to keep windows from remembering the login name and password for a user after you've authenticated to a share?  Ask of right now I have to login to test the user and then REBOOT MY WINDOWS MACHINE to get prompted for a new login ID.  I have 55 users to do and Im going to go postal if I hear the windows boot up sound one more time.  I assume it's stored in some sort of network user cache.  Anyone know how to disable this "feature?"

---

### Post by andrewc6l on 2008-01-02
From a command line, try:

net use r: /delete
net use r: \\foo.bar\foo\bar\baz /user:myname mypassword /persistent:no

---

### Post by tcpip4lyfe on 2008-01-03
Thanks!

---

