---
title: "regex brackets"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-07-04
Is it possible to match a expression that look somethin like this.
```
maybe somethin[something]maybe something
```

---

### Post by DaithiF on 2010-07-04
sure.  not sure whether you are just searching for matching items, or wanting to do a search/replace, but heres a search/replace example:
```
$ cat testfile
text at beginning maybe somethin[something]maybe something text at end
text at beginning [something] text at end

$ sed 's/\(maybe somethin\)\?\[something]\(maybe something\)\?/REPLACED/' testfi
le
text at beginning REPLACED text at end
text at beginning REPLACED text at end
```

---

