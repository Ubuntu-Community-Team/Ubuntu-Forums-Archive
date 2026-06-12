---
title: "MDB Import in Kexi - not working."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by longtom on 2009-02-09
Hi,

I am trying to import an *mdb file into kexi, which is supposed to be possible.

However, every time I do attempt this, kexi goes with me through the initial screens.  When it comes to the point where the business is to be done, kexi just gracefully leaves the scene and I'm back on the desktop.

Any suggestions are welcome to get kexi to do the next step.

Greetings

longtom

---

### Post by longtom on 2009-02-09
Alright, this is what I get from the terminal:


```

kexi
kbuildsycoca running...
KCrash: Application 'kexi' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
cango@cango-desktop:~$ ICE default IO error handler doing an exit(), pid = 8610, errno = 11

```

Maybe that will tell somebody something.

lt

---

### Post by longtom on 2009-02-09
bump

---

### Post by longtom on 2009-02-09
last - desperate BUMB

---

### Post by Terl on 2009-02-09
You may have better luck through here:  [Kexi site]("http://www.kexi-project.org/wiki/wikiview/index.php@KexiFAQ.html") as this is more of a Kexi issue.

As for the import, what are you trying to import.  As I understand from reading their FAQ some things are not fully implemented yet, as in:

> Q4.1: Is reading/writing of Microsoft Access .mdb/.mde files available? If so, how feature-rich is this module? 
A4.1: Currently, importing table schemas and data is supported using import driver (MS Access data types are carefully mapped to Kexi data types) from .mdb/.mde files. Importing queries, forms, reports and web pages is not yet supported. 
For Linux/Unix operating systems the import driver is available as separate package - find "MS Access import plugin for Kexi" item for your distribution on the Packages page. On Windows the driver is bundled in the installation package. See MDBDriver for more info, including a list of MS Access versions that are supported. 


---

### Post by longtom on 2009-02-09
Yeah - you have a point there.

I'll try there - however, I don't have to high expectations.  So double boot it'll stay for some time coming....

Thanks for reacting

lt

---

### Post by Terl on 2009-02-09
Have you tried open office's database?  I believe it will open mdb files as it is.  I have used it a little (I design databases at work in MS Access) and find it is very much like access.  If you want to try it, it is available via synaptic (It is not in the default install, you have to get the database part later).

---

### Post by longtom on 2009-02-10
No joy.

I tried that first.  All I see is 3 lines of gibberish.  But any suggestions are still very welcome - I'm not prepared to give in just now.

lt

---

### Post by Terl on 2009-02-10
What are you trying to do?  You say "import mdb" but are you just trying to import the tables, queries, forms?  What version of Access is the database in now?  It sounds as if you are trying to convert the whole database from access into another program (kexi or OO Base).  I have not tried it myself but it is doubtful you can do that and have it all work.  

I would try pulling in tables first and see how that goes.  I am at work right now and cannot test/try anything right now.  I would first try importing one table at least and see how it goes.  I would also use Open Office's database program as it is more compatible with access from what I have read.

And I agree with you, never give in...make the computer do what it is told (hee hee)

---

### Post by pndragon on 2009-02-10
I recently had a similar problem.

I desperately needed to rebuild an Access db after I accidentally overwrote my windows partition (small loss, the only real reason to keep it was an Access db which I had backed up onto a flash drive)

Kexi ultimately proved to be unsatisfactory and I ended up installing mdbtools:
```
sudo aptitude install mdbtools-gmdb
```
and saving the tables from my .mdb as .cvs and importing them into a completely new OO.org Base db.

I had to rewrite the queries and rebuild the forms but that wasn't really as bad as it sounds and not much different from doing it the first time in Access.

Jim

---

### Post by longtom on 2009-02-11
> **Terl said:**
> What are you trying to do?  

Good question.  I'm trying to find out what is possible...

> It sounds as if you are trying to convert the whole database from access into another program (kexi or OO Base).  I have not tried it myself but it is doubtful you can do that and have it all work.

I must admit - in my own, unknowing way, I was kind of hoping that.  

> I would try pulling in tables first and see how that goes.  I am at work right now and cannot test/try anything right now.  I would first try importing one table at least and see how it goes.  I would also use Open Office's database program as it is more compatible with access from what I have read.

Sounds sensible in the big sceme of things.  
Here on the floor, however, I am only the creator of the database.  Others punch in the data - in Access (2000 btw) -  and I can't see them moving from Windows to Ubuntu in a flash, to be realistic.
I was kind of hoping I could service the database from within Ubuntu with Open Source software.

I think I have to kiss that one good bye for the time being and make my peace with VirtualBox.
I'm busy allocating more space to my Ubuntu partition in order to do so.

> And I agree with you, never give in...make the computer do what it is told (hee hee)

In the movies they kick it and it works...I'm not there....yet...:P

Thanks

longtom

---

### Post by Terl on 2009-02-11
I develop and maintain loads of Access databases here as part of my job.  Access can be rather finicky at times, as you know, and Open Office, good as it is, is not 100% compatible.  Any changes you were to make via open office could make for a terrible mess.

Unfortunately Access and other programs from that wonderful company do not play nice with others and sadly you are probably stuck maintaining it via access itself.  My opinion is that, if these are mission critical databases you should just leave it to Windows and access.  Maybe play with a copy of the database to see what you could work out, but I think, unless you want to migrate it to a MySQL database or move everyone to OpenOffice (there is a windows version).

---

### Post by j0rd on 2009-10-07
> **longtom said:**
> Alright, this is what I get from the terminal:


```

kexi
kbuildsycoca running...
KCrash: Application 'kexi' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
cango@cango-desktop:~$ ICE default IO error handler doing an exit(), pid = 8610, errno = 11

```

Maybe that will tell somebody something.

lt

Read the line:
Could not find 'drkonqi' executable.

This is because koffice-libs it not installed on your ubuntu install. This is a problem with the Kexi package for ubuntu and not Kexi itself.

You might also need to add /usr/lib/kde4/libexec into your path afterwards to make sure Kexi can find drkonqi.

---

