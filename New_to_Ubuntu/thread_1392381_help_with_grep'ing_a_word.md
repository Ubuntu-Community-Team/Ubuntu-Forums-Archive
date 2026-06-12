---
title: "help with grep'ing a word"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by DJPlayer on 2010-01-28
trying to grep a particular word and a get count for the # of times it occurs.  Probably wanna test the results to make sure it's absolutely correct.

grr.. starting to drive me nutz..](*,)

---

### Post by diesch on 2010-01-28
```
grep -c some_word some_file
```

---

### Post by baddog144 on 2010-01-28
> **diesch said:**
> ```
grep -c some_word some_file
```

Unfortunately, this only counts the lines the word appears on, rather than the number of times the word appears :(

---

### Post by DJPlayer on 2010-01-28
> **diesch said:**
> ```
grep -c some_word some_file
```

that only gives me the matching number of lines the words occurs in.  I need a count of the physical times a specific word appears in a file.

---

### Post by baddog144 on 2010-01-28
I've come up with a slightly hacky script:
```

awk '$1=$1' RS= OFS="\n" file | grep word | wc -l

```
Hope this works for you :D

---

### Post by diesch on 2010-01-28
> **DJPlayer said:**
> that only gives me the matching number of lines the words occurs in.  

I thought that's what you want

> **DJPlayer said:**
> 
I need a count of the physical times a specific word appears in a file.

```
grep -o some_word some_file|wc -l
```

---

### Post by DJPlayer on 2010-01-28
> **baddog144 said:**
> I've come up with a slightly hacky script:
```

awk '$1=$1' RS= OFS="\n" file | grep word | wc -l

```
Hope this works for you :D

nope.. awk syntax error

was thinking of using tr and grep

---

### Post by baddog144 on 2010-01-28
> **DJPlayer said:**
> nope.. awk syntax error

was thinking of using tr and grep

Huh? Works here. Oh well, as said earlier:
```

grep -o word file | wc -l

```

---

### Post by DJPlayer on 2010-01-28
actually I think I got it now.. problem was that I was missing my -o .. thanx.

---

### Post by baddog144 on 2010-01-28
EDIT: Never mind, you got it :P

---

### Post by diesch on 2010-01-28
```
$ grep -o as test.dat|wc -l
4
$ cat test.dat
as as as
as

```

---

