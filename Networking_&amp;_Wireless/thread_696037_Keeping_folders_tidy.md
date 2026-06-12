---
title: "Keeping folders tidy"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by csb1227 on 2008-02-13
I've got a folder shared for my network using samba.  in that folder are other folders containing folders and files.  i'd like to prevent just files from being created in the root folder. creating folders in root is fine and creating files in those folders is also ok.  i just want to keep folks from dropping all kinds of files in the root folder.  possible?

I'll try a visualization...

Fileshare
---Folder01
------file01
------file02
---Folder02
 ------file03
------Folder02a
---------file04
---Folder03
---file05

I'd like to prevent files from being put where 'file05' is.

Thanks,
   Scott

p.s.
is there a better way to make illustrations of folder structures?

---

### Post by Ek0nomik on 2008-02-13
> **csb1227 said:**
> I've got a folder shared for my network using samba.  in that folder are other folders containing folders and files.  i'd like to prevent just files from being created in the root folder. creating folders in root is fine and creating files in those folders is also ok.  i just want to keep folks from dropping all kinds of files in the root folder.  possible?

I'll try a visualization...

Fileshare
---Folder01
------file01
------file02
---Folder02
 ------file03
------Folder02a
---------file04
---Folder03
---file05

I'd like to prevent files from being put where 'file05' is.

Thanks,
   Scott

p.s.
is there a better way to make illustrations of folder structures?

Regarding the illustrations, you could draw it and host it as an image.  I think what you did was fine though.

Anyways, I have never used Samba because I use SSH for all my file sharing between Linux to Linux and Linux to Windows, but this may be of some help:

[http://freebooks.by.ru/view/SambaIn24h/ch07-03.htm](http://freebooks.by.ru/view/SambaIn24h/ch07-03.htm)

---

### Post by csb1227 on 2008-02-13
Thanks.  I'm going to check that out now.

---

