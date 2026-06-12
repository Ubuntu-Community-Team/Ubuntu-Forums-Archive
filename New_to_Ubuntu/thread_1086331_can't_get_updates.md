---
title: "can't get updates"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by gidrdunv11 on 2009-03-03
Howdy, thanks for taking a look. 

I get this message when I try to update.

'E:Type 'http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz' is not known on line 48 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I probably didn't install wine correctly in the how to. Don't know where to go from here.

What aught I do.

J

---

### Post by adult swim on 2009-03-03
run this
```
gksudo gedit /etc/apt/sources.list
``` and delete the line that says [http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz](http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz)
then save and close the file, you should be able to update.

---

### Post by gidrdunv11 on 2009-03-03
Like a charm!

Thanks.

---

