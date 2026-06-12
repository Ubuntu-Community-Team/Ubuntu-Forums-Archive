---
title: "How to redirect output to 2 files in a single line cmd"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by john77eipe on 2011-06-10
Hi,

I like to write the output of a echo command to std-out and also into a file.  

From my understanding, it's not possible.

---

### Post by papibe on 2011-06-10
You can use the 'tee' command:
```
$ echo "Hello, World." | tee log 
```
Hope it helps.

---

### Post by john77eipe on 2011-06-12
Thanks.

Damn. I had read about tee. But didn't use it for long time. Totally forgot.

---

