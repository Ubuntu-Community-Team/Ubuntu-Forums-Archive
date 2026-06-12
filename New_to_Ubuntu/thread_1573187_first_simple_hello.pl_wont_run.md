---
title: "first simple hello.pl wont run"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by geomarsh on 2010-09-12
I installed ubuntu to be able to write scripts on my lap top but my simplest scripts wont run.  "command not found".  I can use bash or ksh and write, save and chmod.  It all looks right to me but they wont run.  Perl -v looks normal.  Suggestions anyone?

---

### Post by spjackson on 2010-09-12
> **geomarsh said:**
> I installed ubuntu to be able to write scripts on my lap top but my simplest scripts wont run.  "command not found".  I can use bash or ksh and write, save and chmod.  It all looks right to me but they wont run.  Perl -v looks normal.  Suggestions anyone?
It sounds like it's not in your path. If it is in your current working directory, then do ./hello.pl , otherwise use the full path to your script.

---

