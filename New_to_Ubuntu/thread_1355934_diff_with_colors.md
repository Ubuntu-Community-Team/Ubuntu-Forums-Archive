---
title: "diff with colors"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by sharpdust on 2009-12-15
Are there any variants of diff that give some color output for the differences between two files?

I know Eclipse and other IDEs offer this type of service, however I'm looking for just a command line tool.

Thanks

---

### Post by sharpdust on 2009-12-15
Hmm, I think I found a good one for unified diff:
[http://boredzo.org/diff-colorize/](http://boredzo.org/diff-colorize/)

Using that and this alias (tsch) does a great job.
```
alias diff      'diff -u \!* | diff-colorize.py'
```

I would be happy to hear if anybody has any others.

---

