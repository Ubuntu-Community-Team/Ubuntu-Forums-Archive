---
title: "open office question?"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by werty2010 on 2011-02-22
recently i started taking lessons on ms access and was looking for a linux equivalent
i looked for openoffice and found 2 :the complete suite(Base) and Database.
are they the same thing? which one should i install?
since im not experienced with these kind of programs, should i install any extra packages that i might need later?
what is the difference between openoffice and libre office?

---

### Post by Vaphell on 2011-02-22
open office and libreoffice is pretty much the same thing at the moment. LO is a fork of OO - people were unhappy with how Oracle handles things (Oracle controls OO) so they created their own version. That happened not too long ago, so there are no significant differences yet. Libre Office will replace Open Office as the main office suite in Natty Narwhal (11.04)

I think that Base is the equivalent of Access but don't expect feature parity and 100% compatibility. That is main problem with such lessons - usually they teach a particular piece of software, not principles/technology that piece of software uses/follows. Every spreadsheet works pretty much the same, yet 90% of people are completely lost when not in front of Excel or Word.

---

### Post by werty2010 on 2011-02-22
ok thanks but should i install the whole suite or just "Database"
any extra packages i might need for later use?

---

### Post by slooksterpsv on 2011-02-22
> **werty2010 said:**
> ok thanks but should i install the whole suite or just "Database"
any extra packages i might need for later use?

I say just get the whole thing, besides Base, the only other item(s) you'd be missing are Formula and... maybe that's it is just the forumula program. Drawing, Presentation, Spreadsheet, and Word Processor are installed by default. So tech. you'll already have the full suite.

---

### Post by grahammechanical on 2011-02-22
If you install through the Ubuntu Software Centre you can install the word processor without the database. If you select to install the database the Ubuntu Software Centre will install other parts of the suite of programs. You will find that to use Base you will need Writer installed (I think). The Centre will take care of that for you. There is a core component of Open Office that always has to be installed for all the parts of the suite of programs use that core component.

Just click on the part that you want and see what other parts come with it.

Regards.

---

### Post by SeijiSensei on 2011-02-22
Every time I've tried Base, I've found it annoying and disappointing.  There really isn't anything I've found that can compete with Access.

With ODBC drivers, you can use Access as a front-end for SQL databases in MySQL or PostgreSQL.  So you get the reliability benefits of SQL on Linux and the ease-of-use benefits of Microsoft Access.

---

### Post by oldfred on 2011-02-22
MS Access is one thing not well recreated in Linux.

I saved all these but each has issues and none work like Access, Kexi seemed the closest:

Databases:
OpenOffice database
MDB Viewer
Glom - design is loosely based on FileMaker Pro
[http://www.glom.org/wiki/index.php?title=Main_Page](http://www.glom.org/wiki/index.php?title=Main_Page)
[http://www.kexi-project.org/](http://www.kexi-project.org/)
[http://www.koffice.org/kexi/](http://www.koffice.org/kexi/)
[http://www.knoda.org/](http://www.knoda.org/)
[http://www.gnome-db.org/](http://www.gnome-db.org/)
[http://www.0d.be/projects/gaby/](http://www.0d.be/projects/gaby/)
Microsoft Access in Wine - some success
[http://ubuntuforums.org/showthread.php?t=1113065](http://ubuntuforums.org/showthread.php?t=1113065)
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

I am just using python and sqlite, but that is a lot lower level than the somewhat simple ways Access lets you work with data.

---

### Post by werty2010 on 2011-02-23
i just went for the full suite
the only thing i need to know now is what other extra packages i need to have compatibility with access?

---

### Post by Hagar Delest on 2011-02-23
Some hints here also: [Open Access 2003 database in OpenOffice.org?](http://user.services.openoffice.org/en/forum/viewtopic.php?f=13&t=36898)

---

