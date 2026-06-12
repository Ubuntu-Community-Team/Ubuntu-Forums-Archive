---
title: "Unsupported Updates source problem"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Loki*PI on 2009-06-16
Whenever I update I get an error message that the system has not been updated for 100+ days.  This is caused by the Unsupported update source [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/)  Distribution feisty-backports. 

I'm running hardy heron.  I can uncheck unsupported updates and no problem.  

Is there another source for unsupported updates I can put in?

Shouldn't it be looking for harding-backports not feisty?

Thanks

---

### Post by dje on 2009-06-16
can you please post the output of the following from a terminal:
```
cat /etc/apt/sources.list
```

dje

---

