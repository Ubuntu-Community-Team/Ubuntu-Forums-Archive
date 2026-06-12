---
title: "direct lan connection b/w windows and linux"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by crhumber on 2007-07-05
I'm trying to set up a direct connection via crossover cable between my linux machine and my old windows machine in order to transfer files.  I've read a bunch of forum posts about this topic and similar topics related to samba, but I still can't get it to work.  I have samba set up and the computers can ping each other just fine, but I can't get to where I can see my windows files.  I do have sharing turned on the windows machine.  Please help!

---

### Post by t4thfavor on 2007-07-05
set up a file share on the windows box, have a user that has a password as well as access to the share.

press alt+F2 then type "smb://ipToWindowsBox" then it will ask for credentials. Type them in and it will work.

You must ensure that "Simple file sharing" is off on the windows box or you will only be able to connect as guest.

---

### Post by crhumber on 2007-07-06
Thanks a bunch.  I finally got it to work somewhat...I had forgotten to adjust the settings on my windows firewall.  One problem still remains though.  When I try to open folders on my windows machine from ubuntu I am sometimes asked for a username and password...but I never set it up so that I had to login.  The strange thing is that it doesn't always ask for a password.  For example,  this morning I was able to open up 'My Pictures' but now it asks me for a username and password.  Any ideas??  Thanks!

---

