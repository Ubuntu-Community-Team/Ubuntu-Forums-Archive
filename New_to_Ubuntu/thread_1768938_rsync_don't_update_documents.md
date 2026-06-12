---
title: "rsync don't update documents"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by SpinningAround on 2011-05-27
I'm trying to use rsync to backup some files problem is that rsync don't update documents like .odt and .ods . What I would like rsync to do is check if document is older (modified) and if it's smaller on the target compare to the source, in that case replace the file on the target. Would anyone please advice how to copy document files?

I'm using this command, excluding .*
```

rsync -rtuv --exclude-from 'exlude.txt'  source/ target/

```

---

### Post by papibe on 2011-05-27
Except for the size requirement, something like this should work:
```
rsync -av source/ target/
```
What do you have on exlude.txt ?

Regards.

---

