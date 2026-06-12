---
title: "Cifs ACL"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by Pietje on 2006-12-09
I have an strange problem, I have set up Samba shares, and use ACL's for access. Wen I connect from Windows XP to the shares, the acess rights are al working, and the acls are being used when determening access.

However, when I use ubuntu as client, and mount a Samba share using cifs as filesystem, The share seems to be read-ony, I cannot for example drag files into a share where a user has rw (ACL) access. (this does work when I connect to the share from WinXP)

It seems that cifs does not use the ACL access rights, how can I setup CIFS to access this share correctly? It seems that I need XATTR and POSIX support? Ho do I enable this?

Thanks for your help!

---

### Post by Bubbel on 2007-07-24
Did you set the uid and gid in your mount options?
Second thing to test: run smbacls on a file in that folder. What does it show?
Third: install Eiciel for Nautilus GUI access of ACLs and ACL for the ACL support. There's also a Python-pylibacl, but I don't know if that is of any use.

I'm still not there yet, but maybe you have something to wotk with now.

Good luck, Bubbels :-?

---

