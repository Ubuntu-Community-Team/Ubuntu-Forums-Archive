---
title: "Chown many files"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-07-08
What's easier than doing this(?):
[[IMG]http://img219.imageshack.us/img219/6118/screenshotoqc.th.png[/IMG]]("http://img219.imageshack.us/i/screenshotoqc.png/")

---

### Post by sisco311 on 2009-07-08
```
chown -R username\: ~/Documents
```

---

### Post by Paqman on 2009-07-08
It's that -R option that does all the work btw. It makes the chown command recurse into any directories and chown all the files in them as well.

---

### Post by Elep.Repu on 2009-07-08
> **Paqman said:**
> It's that -R option that does all the work btw. It makes the chown command recurse into any directories and chown all the files in them as well.

Thank you very much. :)

---

