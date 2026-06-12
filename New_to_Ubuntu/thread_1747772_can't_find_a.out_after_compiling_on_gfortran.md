---
title: "can't find a.out after compiling on gfortran"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by jis1980 on 2011-05-03
I have accidentally ereased a.out file while making a program. Aparently gfortran sill compiles gun cant make the output file.

I have tried reinstalling gfortran but it doesn't work and the terminal shows this message:

user@laptop:~/Documentos/amb/programas$ gfortran mean.f a.out
a.out: file not recognized: File truncated
collect2: ld returned 1 exit status

---

### Post by seawolf167 on 2011-05-03
You shouldn't need to specify a.out, as that is the default build name. If you do want to specify a specific name, use the -o switch

```
gfortran mean.f
gfortran -o somename.extension mean.f
```The output will be in your working directory, so you can run it with

```
./a.out
./somename.extension
```

---

