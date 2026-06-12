---
title: "Sorting all files by date of creation into a text file?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by honeybear on 2011-07-04
Hi, 

the file is /tmp/listoffiles.txt
that contains:
```
/home/user/document1.doc
/home/user/document2.doc
/home/user/documentx.doc
/home/user/documenty.doc
...
```

```
date -r "$each" +%Y%m%d-%H%M%S 
``` allows to give the date and time of creation. 

sort allow to sort file by alphabetical.

So how could the content of /tmp/listoffiles.txt be ordered by ascending way? 

Regards

---

### Post by AlphaLexman on 2011-07-04
Unix / Linux files do NOT store the creation time... only changed, modified and accessed times.

However *.doc files do save creation times as do *odt files. So I will look for a solution and post back!

---

### Post by honeybear on 2011-07-05
> **AlphaLexman said:**
> Unix / Linux files do NOT store the creation time... only changed, modified and accessed times.

However *.doc files do save creation times as do *odt files. So I will look for a solution and post back!

then

ok for date -r 
it is fine for me

---

### Post by AlphaLexman on 2011-07-06
> **honeybear said:**
> sort allow to sort file by alphabetical.
Your **title** requests sort by **date**, but your text [above] requests sort by **alphabetical**, which do you want?

**EDIT:** To sort by size only...
```
ls -1Shrs 
```

To sort alphabetically...
```
ls -sh
```

---

### Post by honeybear on 2011-07-07
> **AlphaLexman said:**
> Your **title** requests sort by **date**, but your text [above] requests sort by **alphabetical**, which do you want?

**EDIT:** To sort by size only...
```
ls -1Shrs 
```

To sort alphabetically...
```
ls -sh
```

to sort by date of creation/modifi/or close to... would be fine

---

### Post by Vaphell on 2011-07-07
```
while read f; do echo $( date -r "$f" +%Y%m%d-%H%M%S ) "$f"; done < /tmp/listoffiles.txt | sort | cut -c17- > /tmp/sortedlist.txt 
```
it creates temporary records (date file), sorts them, dumps date part, writes to file

if you want to sort ls results by time use -t switch and optionally --time=atime/access/use/ctime to define which timestamp to use.
more about ls: **ls --help**

---

