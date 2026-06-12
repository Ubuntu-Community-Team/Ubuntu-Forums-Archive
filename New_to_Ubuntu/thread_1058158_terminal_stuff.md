---
title: "terminal stuff"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by brandon82 on 2009-02-02
can anyone tell me how to print only the number of files in my cwd from terminal? Also, how can I narrow down what files are being printed in terminal? (ex. if I do ls -l, i get all visible, but say I only want to view recent files?)

---

### Post by utnubuuser on 2009-02-02
have you checked "man ls"?

check this one out:> [http://linux.about.com/od/commands/l/blcmdl1_ls.htm](http://linux.about.com/od/commands/l/blcmdl1_ls.htm)

---

### Post by andrew.46 on 2009-02-03
Hi brandon,

> **brandon82 said:**
> can anyone tell me how to print only the number of files in my cwd from terminal? 

I guess the easiest way would be to use both ls and wc:

```
ls -1 | wc -l
```

This would not include hidden files though, so you could also consider:

```
ls -1a | wc -l
```

> Also, how can I narrow down what files are being printed in terminal? (ex. if I do ls -l, i get all visible, but say I only want to view recent files?)

Depends what you mean by 'recent files'. If you mean files that were, for example, modified in the last 24 hours I would tend to use find:

```
find $PWD -mtime -1 
```

Hopefully this is what you mean :-).

Andrew

---

### Post by billgoldberg on 2009-02-03
> **brandon82 said:**
> can anyone tell me how to print only the number of files in my cwd from terminal? Also, how can I narrow down what files are being printed in terminal? (ex. if I do ls -l, i get all visible, but say I only want to view recent files?)

I suggest you start reading up:

[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

---

### Post by brandon82 on 2009-02-04
that was exactly what I was needing to do. Thank you!

prob. solved.

---

