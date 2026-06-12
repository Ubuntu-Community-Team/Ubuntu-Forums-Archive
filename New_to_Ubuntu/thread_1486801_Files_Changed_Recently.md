---
title: "Files Changed Recently"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by Zeophlite on 2010-05-18
How do I list all the files changed in the last day from the entire filesystem?

---

### Post by viralmeme on 2010-05-18
> **Zeophlite said:**
> How do I list all the files changed in the last day from the entire filesystem?
$find . -type f -mtime 0

---

