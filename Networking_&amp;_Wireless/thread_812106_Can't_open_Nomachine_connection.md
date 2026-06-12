---
title: "Can't open Nomachine connection"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Sawyer_ on 2008-05-29
Been at this problem for a few days now, tried pretty much everything possible, and yet still every time the error details are the same:

NX> 203 NXSSH running with pid: 7668
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.0.0.5 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

This issue came up after I installed the OpenSSL vulnerability updates. I'm running the latest version of NX Free Edition on Ubuntu 8.04, and I'm trying to connect to it from a Windows XP box.

---

### Post by Sawyer_ on 2008-05-29
Also.. when running sudo ./nxserver --status locally,
I get the following:

NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.

---

### Post by Sawyer_ on 2008-06-17
I've also reviewed the sshd_config and set the proper path to the auth keys, and wiped clean all the possible keys found on the system and added new ones.

This very same issue comes up even if I completely remove the whole  NX free edition from the system and re-install it.

Also did a re-install of the viewer on the client computer, but don't know if the keys were still saved on some other location on Windows XP.

Edit:

Oh and SSH seems to be working fine, as I can access the Ubuntu box using putty through SSH.

---

### Post by vancheese on 2009-03-04
Was there any resolution of this issue as I've run into a similar problem.
My issue is that I can connect to a intrepid machine and use Freenx but my hardy machine is refusing authentication

---

### Post by horstkotte on 2011-07-28
I am seeing the same behavior on Maverick. Was there any resolution? :confused:

---

### Post by vancheese on 2011-07-29
I'm on natty and don't seem to have this problem!

---

### Post by promet on 2011-09-12
I am on Natty (11.04) and am having the same issue. It (NoMachine NX) was working like a charm on 10.10. 

I am going to try a fresh install of the latest NoMachine .debs from the NoMachine website, and will report back...

---

### Post by vancheese on 2011-09-14
I've used the closed-source debs and they work fine

---

