---
title: "Samba Configuration"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by anindya23 on 2008-08-12
After configuration samba when i want to access share folder from windows it gives me the following message.

> \\Server\BACKUP\ is not accessible.You might not have permission to use this network resource.Contract to the administrator of this server to find out if you have access permission.
Multiple connections to a server or shared resource by the same user,using more than one user name,are not allowed.Disconnect all previous connections to the server or shared resource and try again

what i have to do to avoid this problem?

---

### Post by linux6994 on 2008-08-12
How are you trying to access the remote share? Is it via nautilus or dolphin?  When using samba outbound we us smbfs, ensure that you have it installed via Synaptic.

---

### Post by hderham on 2008-09-12
I have had the same problem, probably because my full name is stored in the system by Linux.  So, my full name is John Smith, which I was using as my account name on Windoze.  My account on Linux is js, account password jspw.  When I made an account on Windoze with username js and password jspw so there was a perfect match between account name and password on both boxes/operating systems, it connected to the private shares perfectly, provided I had logged in to Windoze as js.

---

### Post by gregphil on 2008-09-12
Your username/password only matters if the Windows shares are authenticated (non-anonymous or non-guest) shares.  The browsing of shared authenticated files from Windows machines is broken right now in ubuntu 8.04.1, see:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

Ignore the bug titles, the bug applies to all authenticated Windows shares.

Search for some of my other recent Samba posts for a work-around if you need to be using authenticated Windows shares.

Sorry.....

---

### Post by superprash2003 on 2008-09-13
please post your smb.conf file here

---

