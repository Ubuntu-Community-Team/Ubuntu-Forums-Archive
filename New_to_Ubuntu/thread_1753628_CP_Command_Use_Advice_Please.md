---
title: "CP Command Use Advice Please"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Kakym on 2011-05-09
Trying to copy files created on todays date to an archive folder and so far I have got:

[B]find . -name “*” -type f -mtime 0 -print0 | xargs -0 cp -r -u -v -t ~/Archive

[/B]which unfortunately does not work.

Would a kind soul please correct my syntax to achieve what I'm trying to do.

Thank you

---

### Post by TeoBigusGeekus on 2011-05-09
Try with the exec option
```
find ./ -name “*” -type f -mtime 0 -exec cp -r -u -v -t "{}" ~/Archive \;
```

---

### Post by hakermania on 2011-05-09
> **TeoBigusGeekus said:**
> Try with the exec option
```
find ./ -name “*” -type f -mtime 0 -exec cp -r -u -v -t "{}" ~/Archive \;
```
This ofcourse doesn't mean that Greeks are kind souls ! xD
&#928;&#945;&#964;&#961;&#953;&#974;&#964;&#951;!

Please note that find has already got the -exec argument, which is very helpful ;)

---

### Post by Kakym on 2011-05-09
Thank you kind souls!

For some reason I couldn't get the original command to work so stripped it back to:

find . -iname "*" -mtime 0 -exec cp {} ~/Archive \;

which seems to work fine

Is it possible to incorporate zipping the resulting files?

Thanks

---

