---
title: "shorten a non searchable pdf file"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by jtmedin on 2009-10-22
Have a pdf file that is non searchable. Would like to delete all but the first few pages. Think each page is a picture. Anyone got any ideas? TIA

---

### Post by XCan on 2009-10-22
I would use pdftk for it
```
 pdftk A=your.pdf cat A1-10 output new.pdf 
```
this should give you the first 10 pages saved to a new pdf.

Alternatively you could print to file and only print out the pages you want.

---

### Post by Daveski on 2009-10-22
What about printing just the pages you want - then choose print to file and select PDF?

---

