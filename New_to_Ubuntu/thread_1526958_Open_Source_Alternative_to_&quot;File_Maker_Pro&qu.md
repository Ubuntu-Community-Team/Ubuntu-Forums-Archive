---
title: "Open Source Alternative to &quot;File Maker Pro&quot;"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Ceiber Boy on 2010-07-08
In work we use File Maker Pro which is a database program, after months of persuasion i have managed to gain permission to duel boot my machine and install Ubuntu but i need an open source Linux alternative to File Maker Pro, I have have a look around on the internet and have only found people wanting to sell me their products.

if you have any experience of file maker pro or alternatives please respond 

thanks

---

### Post by aysiu on 2010-07-08
Try Glom.

---

### Post by dtfinch on 2010-07-08
There's also Kexi, which I have no recent experience with.

---

### Post by oldfred on 2010-07-08
Several others to try most are in repositories: 

OpenOffice database
MDB Viewer
Part of KDE but can be installed in gnome:
[http://www.kexi-project.org/](http://www.kexi-project.org/)
[http://www.koffice.org/kexi/](http://www.koffice.org/kexi/)
[http://www.knoda.org/](http://www.knoda.org/)
Not in repository:
[http://www.gnome-db.org/](http://www.gnome-db.org/)

---

### Post by Ceiber Boy on 2010-07-09
Thank you everyone for your answers, eventhought I know somewhat about computers I do not know about databases so please for give my simple question and lack of experience.

The way we use file maker pro is to connect and view data remotely on a server, Am I able to do this with any of the above mentioned or any other database programs.

Again many thanks

---

### Post by Miljet on 2010-07-09
[http://www.osalt.com/filemaker](http://www.osalt.com/filemaker)

---

### Post by oldfred on 2010-07-09
What db server and how do you connect? ODBC? Setting up ODBC in windows is not easy and it is a little worse in linux. 

Most of the linux db's are front ends to a server (even if the data "server" is on your machine) as they do not have internal files. Those that do have internal files also connect. But, some only connect to server tables that it creates.

---

### Post by JohnTho on 2012-08-02
I'm just bumping this old thread as I've just started using Ubuntu (12.04) and I'm looking for a way to migrate some Filemaker Pro files to an open-source database. I've installed LibreOffice Base but I now need to find a common file format that Filemaker can export and Base can import.

As I'm a lazy sod at the best of times I really want a format that includes the layout information in addition to the data. As far as I can see the formats exported by my version of Filemaker are:

.tab : tab-separated text
.csv : comma-separated text
(I know these two only contain the data records).

.slk : SYLK
.dbf : DBF
.wk1 : Lotus 1-2-3
.bas : Basic (is that as in the BASIC programming language?)
.mer : Merge
.htm : HTML table files

Can any of these formats be opened/imported by Base? If not can anyone suggest another open-source database application that can handle any of them, or better still open the native .fp5 files?

---

### Post by oldos2er on 2012-08-02
Old thread closed, please start a new thread.

---

