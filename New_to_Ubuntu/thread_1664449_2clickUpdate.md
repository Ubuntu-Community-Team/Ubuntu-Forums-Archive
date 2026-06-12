---
title: "2clickUpdate"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-01-11
/usr/bin/2clickUpdateCore &> /tmp/updatelog;

is the line in my script called update in my root crontab. However I get a file in /tmp but the file is blank. I do not know why because when i run that line in terminal i get a file with the output from the program.

---

### Post by lance bermudez on 2011-01-11
this works
/usr/bin/2clickUpdateCore 2>&1 | tee /tmp/updatelog;

---

