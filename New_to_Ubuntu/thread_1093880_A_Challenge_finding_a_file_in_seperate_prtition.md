---
title: "A Challenge finding a file in seperate prtition"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by zabien1970 on 2009-03-12
OK, Here's my situation, I recently repartitioned my HD (in 8.04) and saved my /home, In the process I lost my desktop so I just installed 8.10. I can now go in Places>Removable Media and see the partitions and if I open one I can see my old desktop, home, videos files, etc...
  Now for my problem, I went to file my taxes with turbotax and they want a figure from last years taxes, their help section says to look for a .pdf file from last year, how do I search these partitions for this file?

(I still haven't figured out how to tie my /home partition to my new install)

---

### Post by lindsay7 on 2009-03-12
Unless you saved your return last year as a .pdf (adobe Reader) file. It will not be there anyway.  You can go to computer and find you old partition folders and files. there is a search icon at the top, click on that and enter    *.pdf    and press enter. Do so will find all the files that end in .pdf.  If you find what you want, you should be able to click on it and it will open.

Good luck, I hope you saved it as a pdf file.

---

### Post by Elfy on 2009-03-12
Maybe something like

```
find /path/toold/home -type f -iname **.pdf* -print
```

---

