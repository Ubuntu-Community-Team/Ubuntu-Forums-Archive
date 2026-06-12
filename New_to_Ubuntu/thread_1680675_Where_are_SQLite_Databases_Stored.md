---
title: "Where are SQLite Databases Stored?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Sleestack on 2011-02-02
I installed SQLite from the repositories and I can't locate on the disk where the databases are created. Where is the default sqlite location and where are the database files stored?

---

### Post by Sealbhach on 2011-02-02
Run 

```
sudo updatedb
```

then run

```
locate sqlite
```

As far as I can tell, the databases will mostly be stored in your /home folder.

.

---

### Post by wep940 on 2011-02-02
> **Sealbhach said:**
> Run 
 
```
sudo updatedb
```
 
then run
 
```
locate sqlite
```
 
As far as I can tell, the databases will mostly be stored in your /home folder.
 
.
 
Maybe in a hidden folder?

---

### Post by Sealbhach on 2011-02-02
> **wep940 said:**
> Maybe in a hidden folder?

locate will find them hidden or not. For example, here is a section of the results when I run locate sqlite

```
/home/vaio/.mozilla/firefox/e6h21bwc.default/content-prefs.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/cookies.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/downloads.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/formhistory.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/permissions.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/places.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/places.sqlite-journal
/home/vaio/.mozilla/firefox/e6h21bwc.default/search.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/signons.sqlite
/home/vaio/.mozilla/firefox/e6h21bwc.default/urlclassifier3.sqlite

```

---

### Post by wep940 on 2011-02-03
I've never used locate before, so I didn't know that.  I'll keep locate in mind for the next time I'm driving myself nuts looking for something!

---

