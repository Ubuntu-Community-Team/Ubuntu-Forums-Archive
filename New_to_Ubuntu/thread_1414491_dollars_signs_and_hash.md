---
title: "dollars signs and hash"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Albert Net on 2010-02-23
I happen to have a look at the file /lib/lsb/init-function.


This is one statement inside it.


```
base=${1##*/}
```
Can someone tell me what does that mean?

---

### Post by DaithiF on 2010-02-23
it says take the variable $1, and strip off from the left hand side everything up to the last forward slash.

so if $1 was /path/to/some/file,
then ${var##*/} would return file

```
man bash
```
for more detail

---

### Post by kaibob on 2010-02-23
The following site contains a good explanation with many examples:

[http://bash-hackers.org/wiki/doku.php/syntax/pe#substring_removal](http://bash-hackers.org/wiki/doku.php/syntax/pe#substring_removal)

---

### Post by Albert Net on 2010-02-24
I got it.

```
man bash | less +/\#\#
```


Thank you very much, DaithiF.


kaibob, that web site is quite comprehensive. I need to spend more time on it.

---

