---
title: "Samba weirdness"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by joechummer on 2008-06-11
I have 4 computers in my network:  My main desktop and our file server (both running Ubuntu Hardy), an EeePC running Xandros, and a WinXP laptop.  All of the PCs in the network can see each other's samba shares, except that my desktop can only see the share on the file server and no one else's.  The other PCs can see my desktop's share.  What's weird is that my desktop is using an exact duplicate of the smb.conf file that the file server is using.  Is there a samba setting that I'm overlooking that would make my desktop ignore any non-Ubuntu machines?

---

### Post by superprash2003 on 2008-06-12
could you post the smb.conf file here

---

### Post by joechummer on 2008-06-13
I think I fixed the issue.

Although I could see the Windows laptop on the network, it didn't have an entry in my etc/hosts file for some reason.  I added it in, and voila!  Share shows up.  Thought I'd added everything on the network already, but I guess I'd missed that one.

With the EeePC, I checked the smb.conf and noticed that Xandros had automatically set the share to have the "force user = <username>" parameter, which forces remote users to log in as that user.  I commented that out, and it works like a charm.

---

