---
title: "SQLite command-line does not open places.sqlite db file"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by nitstorm on 2011-06-04
[B]Problem:
[/B]I want to access the *places.sqlite* db file present in my Mozilla folder.
When I open it with my sqlitebrowser I can access the db, but when I use the command-line to access it I am unable to.
 
```
sqlite .mozilla/firefox/me9d3dsc.default/places.sqlite
Unable to open database ".mozilla/firefox/me9d3dsc.default/places.sqlite": file is encrypted or is not a database

```

It's my first time trying to use sqlite so please bear with me. Thanks :)

---

### Post by yeats on 2011-06-04
From this thread:

[http://ubuntuforums.org/showthread.php?t=799320](http://ubuntuforums.org/showthread.php?t=799320)

You might try:

```
sqlite3 .mozilla/firefox/me9d3dsc.default/places.sqlite
```

(may require you to download an sqlite3 package).

---

### Post by nitstorm on 2011-06-04
Thanks that helped :D Cheers!

---

