---
title: "Question about directory sharing..."
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Lord Xadar on 2007-12-18
Well well well... this is what I want to do but haven't had success doing:

I want to "share" a single folder (my _~/Public_ folder)... what do I mean?
Well, PC1 has the folder, and I only need other PCs in my network to get full read/write access to it.

What have I done so far:
System > Administration > Shared folders
Installed SMB and NFS
Added the folder
unticked "Read Only"

The other PCs can read the the files in the share but can't write or delete them, nor create files in the share.

made a chmod 777 of the share... well... now the other PCs can create files... but new files created in the share by my user on PC1 still have write rights only for proprietary and not "group and others".

I remember this was easier in earlier versions of ubuntu...
(what does ticking/unticking "Read Only" does so far?)
It seems that local rights have more priority than "samba rights"...

---

### Post by HermanAB on 2007-12-18
You only need either SMB or NFS, not both.

Since you have it mostly working you already have a fair idea, but you really should go to Samba.org and read the Official Howto.  Samba is extremely complex.  You will find the Official Howto very useful.

Cheers,

Herman

---

### Post by Lord Xadar on 2007-12-18
I know that I won't need NFS, said only to tell precisely what I've done (the Shared Folders "Wizard" asked me to install those).

Ok, Samba is complex, I know that too (or I wouldn't be here asking ;-) )... it's just... stupid that unticking the "read only" checkbox doesn't make the folder writable... isn't that a bug?

---

### Post by Lord Xadar on 2007-12-19
[SIZE="1"]Bump...[/SIZE]

---

