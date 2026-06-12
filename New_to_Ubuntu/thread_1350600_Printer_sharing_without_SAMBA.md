---
title: "Printer sharing without SAMBA"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-09
Hello friend

Is SAMBA necessary for printer sharing on home network?Printer is connected to pc not
running Ubuntu but Vista.Thanks

---

### Post by audiomick on 2009-12-09
If your printer is connected to a Vista machine, then samba is likely to be the easiest way to share it, although I am guessing a bit.

---

### Post by halitech on 2009-12-09
you would need to do the sharing from the Vista computer if that is the one the printer is connected to, in which case you wouldn't need samba.

---

### Post by oldsoundguy on 2009-12-09
Why?

Samba is easy to install from the repositories and it works.  You need it to install the DRIVERS for the printer(s) that are hung off of Windows machines.

I have 7 computers (2 Windows XP and 5 of various Linux builds) and 7 printers on my home net (some very specialized).  MOST of the printers are hung off of an XP box that I use as a print server as well as a photo processing station.

All computers can access all printers (that have divers in cups .. two do NOT).

I use Samba on the Linux machines.

(and the real trick for network sharing is to make SURE all computers and printers are in the same workgroup.  I use the Linux default (change the windows default to workgroup instead of MSHOME) as it is just easier that way.)

---

### Post by manny43 on 2009-12-09
Samba has the workgroup name set by default as WORKGROUP but the workgroup name that i'm
currently using is not workgroup or mshome.I'm wondering if workgroup is mandatory for Ubuntu
or i can use the workgroup name currently in use in my home network which is not mshome nor
workgroup?

---

### Post by cariboo on 2009-12-09
Yes all the systems have to be in the same workgroup. Press Alt-F2 and type gconf-editor, then navigate to system-smb, right-click workgroup and select edit key, and enter your workgroup name. Click File-->Quit and your done.

---

