---
title: "Cant access file &gt;.&gt;"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by Liliitha on 2010-04-28
I try to do ls TOSHIBA EXT but it won't let me.  It is named TOSHIBA EXT but whenever I type it in it says Can't find TOSHIBA... Can't find EXT
How do I type the name of this file so that Terminal can know what I am talking about??

---

### Post by roger_1960 on 2010-04-28
Hi

Put it in quotes;
> 
ls "TOSHIBA EXT"

---

### Post by sisco311 on 2010-04-28
```
ls TOSHI #press TAB for auto-complet
```

```
ls "TOSHIBA EXT"
```
or
```
ls TOSHIBA\ EXT
```

The space is a special character (field separator) you have to escape it, see:
```
man bash | less +/QUOTING
```

---

