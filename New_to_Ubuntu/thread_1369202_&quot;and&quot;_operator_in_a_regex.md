---
title: "&quot;and&quot; operator in a regex?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by minsf on 2009-12-31
anyone knows how to do "and" of two regular expressions?

that is, if you want lines which have aaa or bbb, you can use
```
egrep  'aaa|bbb' fileName
```
but what if you want all lines that have both aaa AND bbb?

of course i can apply two filters:
```
grep aaa fileName | grep bbb
```

but is there a way to do it in one regex?

thanks, i'm kinda noob with regexes...

---

### Post by lloyd_b on 2009-12-31
[Here's a thread]("http://archives.devshed.com/forums/unix-linux-135/logical-and-with-regular-expression-2422963.html") (from another forum) on the subject.  Basically, doing it with 'grep' is kinda tricky - you're better off with 'awk' and it's "&&" logical AND operator.

Lloyd B.

---

### Post by minsf on 2010-01-01
thanks lloyd

---

