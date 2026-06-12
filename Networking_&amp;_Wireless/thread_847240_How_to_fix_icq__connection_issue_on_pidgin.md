---
title: "How to fix icq  connection issue on pidgin"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by skoda1203 on 2008-07-02
non-availability of icq in pidgin is fixed by new version 2.4.3. It is possible to fix older versions by midifiing library /usr/lib/purple-2/liboscar.so.0.0.0, 


**Installation of hexa editor**:

sudo apt-get install khexedit

**Backup of library:**

cp /usr/lib/purple-2/liboscar.so.0.0.0 /usr/lib/purple-2/liboscar.so.0.0.0.20080701

**Changing rights:**

sudo chmod o+w /usr/lib/purple-2/liboscar.so.0.0.0

**Modifiing library:(ALT+F2)**

sudo khexedit /usr/lib/purple-2/liboscar.so.0.0.0

**In chain:**

0a 01 66 c7 45 b2 14 00 66 c7 45 b4 34 00 66 c7

**Replace:**

0a for 0b

**Changing rights:**

sudo chmod o-w /usr/lib/purple-2/liboscar.so.0.0.0


Tested in Pidgin 2.4.1 on Ubuntu 8.04 and Pidgin 2.4.2 on Debian Lenny.
Hope this helps 
Cooco

---

### Post by jpeddicord on 2008-07-02
Moved to Networking & Wireless from Tutorials & Tips:

[LIST]
[*]Patches what looks to be a versioning issue, could cause compatibility problems with protocol
[*]Patched library could cause package update issue
[/LIST]

---

