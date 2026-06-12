---
title: "crazy awk q?"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by carrarin on 2010-09-13
Hello everyone,

is it possible to specify two default "field separator" from the command line?



Thanks

---

### Post by Brandon Williams on 2010-09-15
The field separator is a regular expression, so you can use a character class to specify multiple single-character delimiters (e.g. use -F '[:;]' to specify that both ':' and ';' are delimiters), and you can even use a series of multi-character strings (e.g. -F '(delim1|delim2)').

---

### Post by carrarin on 2010-09-15
Hey dude, thanks -- !!!

---

