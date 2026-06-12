---
title: "file system search and move"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by iceman30ad on 2011-03-09
ok i am trying to do a recursive search from a folder (e-book library) on my drive and move specific files in mass to another folder 
i have no problem  customising a command for terminal currently using nautilus ubuntu 10.10 

feel free to ask any questions if i am not clear...


\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\


find is no longer working right 
error
find: missing argument to `-exec'
command i'm using
find /home/chris/cal1/ -iname ".zip" -exec mv '{}' /home/chris/bookstoprocess/zip/\;

---

### Post by TeoBigusGeekus on 2011-03-10
```
find /path/to/ebooklibrary/ -name "searchpattern" -exec mv /path/to/where/you/want/files/moved/ \;
```

Replace searchpattern with a valid search pattern (dah) for the files you want moved, for example *programming.pdf, etc.

---

### Post by iceman30ad on 2011-03-10
ok what am i doing wrong or not understanding

mv: missing file operand
Try `mv --help' for more information.

---

### Post by ~Plue on 2011-03-10
try[FONT=monospace]
[/FONT]find /path/to/ebooklibrary/ -name "searchpattern" -exec mv  **'{}'**  /path/to/where/you/want/files/moved/ \;

---

### Post by newbuntuxx on 2011-03-10
```
find /path/to/ebooklibrary/ -name "searchpattern" -exec mv '{}' /path/to/where/you/want/files/moved/ \;
```

This is correct. You can also use -iname so that the search is case-insensitive.

---

### Post by rg4w on 2011-03-11
NixiePixel made a good introductory tutorial on this a while back:
[http://www.youtube.com/watch?v=x_R_JSiupzo](http://www.youtube.com/watch?v=x_R_JSiupzo)

---

### Post by TeoBigusGeekus on 2011-03-11
> **~Plue said:**
> try[FONT=monospace]
[/FONT]find /path/to/ebooklibrary/ -name "searchpattern" -exec mv  **'{}'**  /path/to/where/you/want/files/moved/ \;
Oops... Just testing the forums' reflexes... 8-[ Well done everyone... :biggrin:

The above is of course the correct answer...
Sorry.

---

### Post by iceman30ad on 2011-03-11
thank you all  ...
toe you had me to the point if i had understood what the help file was trying to tel me i would have had it...
plue  thank you for finishing it it up and setting me straight

and now all i need is some one local that can it down with me an teach me a few thigs

---

### Post by iceman30ad on 2012-03-31
find is no longer working right 
error
find: missing argument to `-exec'
command i'm using
find /home/chris/cal1/ -iname ".zip" -exec mv '{}' /home/chris/bookstoprocess/zip/ \;

now using 12.04

---

