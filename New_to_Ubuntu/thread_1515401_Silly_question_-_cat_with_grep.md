---
title: "Silly question - cat with grep"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Nunners on 2010-06-22
I've been using linux command line for years, but have never worked out how to do the following:

- i'm trying to find all files (in this case php) with a single word in it... e.g. active (in this case I'm changing the database structure they link to and am trying to find all references to the phrase "active"....

I would use:
```
cat *.php | grep active
```
But that just gives me the lines of code that have active in... when there are 20 plus files, it doesn't help...

Is there a way of getting the output to include the name of the file as well as the line of code?

Simple question, just ain't got a clue how to do it?!!!!

Cheers
Nunners

---

### Post by TRoe on 2010-06-22
grep -H active *.php

---

### Post by konqueror7 on 2010-06-22
> grep -H -n active *.php

with line number...

---

### Post by eriktheblu on 2010-06-22
Am I the only one who pictured a vomiting feline from the title?

---

### Post by TRoe on 2010-06-22
Meowlf!

---

### Post by DaithiF on 2010-06-22
-H is redundant if you are operating on multiple files -- the default behaviour is to include the filename of any matches when searching multiple files.

Since the OP was cat'ing the contents of multiple files into grep, grep was working on a stream of input rather than files in that case.

so in short:
```
grep active *.php

```

> 
Simple question, just ain't got a clue how to do it?!!!!

Nunners, for future reference:
```
man grep
```

---

### Post by Nunners on 2010-06-22
Thanks for all the help guys... I didn't realise using grep on it's own was possible.... shows how bad someone self taught can be!

As for the feline reference... my cat is fine thanks... doesn't like the dog and sometimes gets fur balls... but she's fine! ;)

---

