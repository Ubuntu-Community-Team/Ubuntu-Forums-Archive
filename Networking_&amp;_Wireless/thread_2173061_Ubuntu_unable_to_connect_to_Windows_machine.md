---
title: "Ubuntu unable to connect to Windows machine"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by Norrolith on 2013-09-07
Greetings everyone.
I have been trying to network with a window machine for a while.
I beilieved my problem was with Samba not working, but when I got GKSU it worked fine.
unlike the Network. at present, I can access the internet through the network.
The window machine is able to access everything I have set as a share.
Ubuntu however, can see all the computers on the Windows network, but if I click on one
it says "opening "(computer name)" you can stop this operation by clicking cancel"
after a while it give me "unable to access location- failed to retreive share list from server :connection timed out"
I could not find anything on using samba to connect to a windows server.

---

### Post by carlwsnyder on 2013-09-07
You don't use SAMBA to connect to a Windows Server, but you DO have to log in to the Windows Server on an open account to access the shared files.  Have you enabled a Guest account on the Windows server?  Is your Windows networking work group name the same as your Linux work group name?

---

### Post by Norrolith on 2013-09-08
We never set up a workgroup name.  It has never been an issue. Our previous Ubuntu computer connected via Samba.
I looked through Windows network settings and the only thing I saw was reducing the encryption level.

---

### Post by Norrolith on 2013-09-14
like I said before have tried lowering the encryption level but to no avail.
Please some nice somebody drop by this dusty thread and help me

---

