---
title: "Sharing Windows XP files"
date: 2005-06-06
forum: Networking &amp; Wireless
---

### Post by terryw on 2005-06-06
I've managed to get Ubuntu running on my laptop and it is connected to a ADSL router which works fine.
Also connected to the router is a PC running Windows XP.
I can see files on the Windows PC from my laptop by going to:
Places
Connect to Server
In "Service type" selecting "Windows Share"
In the "Server" box type computer name of other PC.
Is this the best way to acheive file sharing.

One problem is that if I double click a file.doc file on the shared drive, OpenOffice starts up fine then complains that "path/file.doc does not exist.
File.gif files however start and load fine.

Any help appreciated please.

Regards

Terry

---

### Post by sethmahoney on 2005-06-06
I have the same issue with OpenOffice and filesharing.  I just copy the file over to the machine I'm working on, edit it, then copy it back.

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=terryw]I've managed to get Ubuntu running on my laptop and it is connected to a ADSL router which works fine.
Also connected to the router is a PC running Windows XP.
I can see files on the Windows PC from my laptop by going to:
Places
Connect to Server
In "Service type" selecting "Windows Share"
In the "Server" box type computer name of other PC.
Is this the best way to acheive file sharing.

One problem is that if I double click a file.doc file on the shared drive, OpenOffice starts up fine then complains that "path/file.doc does not exist.
File.gif files however start and load fine.

Any help appreciated please.

Regards

Terry[/QUOTE]
 Short answer: it can't be helped except by copying the file to a local filesystem, editing,t hen copying back.

Long answer: OpenOffice is not a gnome application, so it does not support so-called "GnomeVFS" (virtual file systme) - which is a piece of code enabling URLS of the form sft://..., smb://..., etc - in short, everything more complicated than usual /absolute/path/to/file

---

### Post by terryw on 2005-06-07
Thanks.
Nice to know it's not me being silly.

Terry

---

