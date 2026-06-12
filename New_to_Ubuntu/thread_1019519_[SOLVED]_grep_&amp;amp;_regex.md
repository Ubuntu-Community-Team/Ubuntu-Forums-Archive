---
title: "[SOLVED] grep &amp;amp; regex"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by FearlessPc on 2008-12-23
Hello

I'm trying to look at all the processes excluding "root"

```
ps -ef | grep '[^root]'
```

and "root" always shows in the output
I tried grep with -G and -E with no luck

also tried 
```
grep '[^root]' /etc/passwd
```
no luck

What I'm doing wrong ?

---

### Post by mister_pink on 2008-12-23
Excluding root? For a start you want the -v option then - to get lines that do not match. Then lose the square brackets.

ps -ef | grep -v '^root'

---

### Post by FearlessPc on 2008-12-23
Thanks working great.

But why [^x] didn't work ? 
all the guides i looked in (3) says "The ^ inside square brackets negates the expression".

---

### Post by mister_pink on 2008-12-23
I'm by no means an expert, but the only use I know of for a ^ is as an anchor - meaning what follows must start the line. Square brackets create a character set, so for example [root] matches the letters 'r', 'o' or 't'. I suspect that in this context ^ reverses that, meaning [^root] matches single character except r o and t.

Again though, not entirely certain. Theres lots of sites about regex though

---

### Post by mbsullivan on 2008-12-23
> know of for a ^ is as an anchor - meaning what follows must start the line. Square brackets create a character set, so for example [root] matches the letters 'r', 'o' or 't'. I suspect that in this context ^ reverses that, meaning [^root] matches single character except r o and t.

This is correct. Therefore, if you wanted a grep that will be equivalent to the version that works:

```
ps -ef | grep -v '^root' 
```

You would have to use something like the following:

```
ps -ef | grep '^[^r][^o][^o][^t]' 
```

This says: "print lines that begin with any four characters except an r followed by an o followed by an o followed by a t".

You can use () to group characters, such that this should also work:

```
ps -ef | grep '^[^(root)]' 
```

Due to its simplicity, I think the -v option is preferred.

Mike

---

### Post by FearlessPc on 2008-12-24
Thank you both for the solutions & clarification, my mistake was not grouping "root" together and the -v option is much more simpler in this case.

---

