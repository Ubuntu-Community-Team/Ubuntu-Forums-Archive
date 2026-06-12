---
title: "environment variable question"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by pmd333 on 2009-07-10
Hi,

Could some one please tell me the significance of { } when used to get environment variables?

For example

echo ${PATH}

versus

echo $PATH

I realize they return the same string when run from the bash shell, but it looks like the { } could be used for grouping or sequencing something.

Thanks in advance,
pmd

---

### Post by Mornedhel on 2009-07-10
The curly braces are optional, but they allow you to do something like this (> denoting a prompt here) :

```
> VAR=foo
> echo $VAR
foo
> echo $VARbar

> echo ${VAR}bar
foobar
```

As a rule of thumb, always use braces except in extremely simple expressions (like a single echo from the prompt, for instance).

---

