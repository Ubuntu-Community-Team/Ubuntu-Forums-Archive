---
title: "bash version number"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Diametric on 2010-01-12
From the terminal, how would you determine what version of bash is being used?

Thanks.

---

### Post by Mornedhel on 2010-01-12
```
bash --version
```

The version is in the first line of output.

---

### Post by Diametric on 2010-01-12
Thank you.  Would you or anyone else speak to how often you keep bash updated?  For instance, I am currently running 4.0.33 however the current version of bash is 4.1. I imagine unless there is a specific change to look forward to, or a major update, it probably doesn't matter...

Thanks again.

---

### Post by Mornedhel on 2010-01-12
I have 4.0.33 as well, as anyone running the Karmic version should.

You can check the changes in 4.1 [here](http://tiswww.case.edu/php/chet/bash/NEWS). There are quite a few new features, but for most users it shouldn't be something they'd notice. The most visible changes came with the 4.0 release.

I generally don't update bash or coreutils until there's a new version in the repositories, although I must admit I considered upgrading to bash 4.0 when I was running Jaunty.

Hint: if you don't understand the new features (and for many of them, I don't either), you don't need to upgrade.

---

### Post by Diametric on 2010-01-12
Thank you again for your replies, Mornedhel, they have been very helpful.

---

