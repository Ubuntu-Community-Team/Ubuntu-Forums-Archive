---
title: "OpenVPN"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by dardack on 2008-07-05
Ok so I got OpenVPN working (almost all thanks to UbuntuForums user post by: bunnynuts).  Although I had to sudo -s to build the keys.  My problem is I have to sudo -s to get into the key directory to run the server.conf file against those keys.  Is there a more secure way?  I do run it in daemon mode and then exit ssh.

Second, in order to copy the client/ca files to my windows laptop i had to chmod a+rw those keys so I could copy them to my keys directory in windows.  However, now i want to make those files unreadable/unwritable, any way to do that?  Also, I did set up a password that's is over 15 characters long in order to use the keys, and when I open the keys they look encrypted, but if someone were to hack me, I don't want them able to copy those files off m laptop.

I must say I love the VPN i can now access my video library when I travel for work.

---

