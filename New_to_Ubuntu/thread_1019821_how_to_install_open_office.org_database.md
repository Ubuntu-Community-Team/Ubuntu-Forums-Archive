---
title: "how to install open office.org database?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-12-23
Been using open office.org for a couple of months.  I have version 2.4.1.  My installation of open office has:

presentation manager
spreadsheet
word processor

Just learned that a database application, "Open Office.org Base", is also available.  How do I obtain the database application?  Do I need to re-install Open Office?

---

### Post by djbushido on 2008-12-23
do
```
sudo apt-get install openoffice
```
This should install "base" as well

---

### Post by taurus on 2008-12-23
Go into System -> Administration -> Synaptic Package Manager -> Quick Search and type in openoffice.  Then, install the openoffice.org-base if that is what you want.

---

### Post by kestrel1 on 2008-12-23
You could always download & install OO.org 3. Just remove 2.4.1 first & follow the instructions here to install OO.org 3:
[http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/](http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/)

---

### Post by samden on 2008-12-23
Or just type in:
sudo apt-get openoffice.org-base

It seems your options are endless! I suspect however that if you really want to do a lot of database work it may be worth your while trying OO.o 3.0 as I understand there has been a lot of improvement in base since version 2. I haven't actually tried 3.0 for myself though, and 2.4 works fine too.

---

### Post by raymondvillain on 2008-12-23
Thanks for all the help.  I went to Synaptics package manager and installed OO.o Base and it works.

Does anybody know if one can use this to open a Microsoft Access database?  Long ago I created a simple database in Access and it is saved as a *.mdb file.

Thanks again.

---

### Post by kestrel1 on 2008-12-23
No OO.org Base won't open MS office Access databases. Shame really, but it never has & probably never will.

---

### Post by abn91c on 2008-12-23
> **raymondvillain said:**
> Thanks for all the help.  I went to Synaptics package manager and installed OO.o Base and it works.

Does anybody know if one can use this to open a Microsoft Access database?  Long ago I created a simple database in Access and it is saved as a *.mdb file.

Thanks again.
you probably will need to upgrade to 3.0 for that

---

### Post by kestrel1 on 2008-12-24
OO 3.0 doesn't open MDB files as far as I can tell. Just had a look & there is no reference to MDB.

Having said that I just did a quick net search. Have a look at this:
[http://dba.openoffice.org/drivers/mdb/index.html](http://dba.openoffice.org/drivers/mdb/index.html)
It may help

---

### Post by djbushido on 2008-12-24
Might also want to look at [this]("http://sourceforge.net/projects/mdbtools/"). Currently you have to compile it, and I haven't tested it, but could be what you want.

---

### Post by raymondvillain on 2008-12-24
I'm going to mark this issue closed.  What I found out is this.  OO.org version 3.0 can open Microsoft Access (version of 1997) *.mdb files.  My queries got imported as tables, which is a waste, but at least the tables came through intact.  But I had to upgrade from version 2.4 to version 3.0 in order to do all that.

Thanks again for help, all.

---

