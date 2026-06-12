---
title: "Loren41"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by loren41 on 2009-05-04
When I try to run upgrade manager using Jaunty, the following error displays"
E:Malformed line 61 in source list /etc/apt/sources.list (absolute dist), E:The list of sources could not be read.'

Line 61 displays as follows:
deb [http://download](http://download) skype.com/linux/repos/debian/ stable non-free

How can I correct?

---

### Post by Didius Falco on 2009-05-04
> **loren41 said:**
> When I try to run upgrade manager using Jaunty, the following error displays"
E:Malformed line 61 in source list /etc/apt/sources.list (absolute dist), E:The list of sources could not be read.'

Line 61 displays as follows:
deb [http://download](http://download) skype.com/linux/repos/debian/ stable non-free

How can I correct?

You need a period between download and skype:

```
deb [http://download.]("http://download/")skype.com/linux/repos/debian/ stable non-free
```

---

### Post by LowSky on 2009-05-04
go to System >Admin >software source

go to the repos tab and uncheck the skype.com repo

---

### Post by loren41 on 2009-05-04
Thanks for your help.

---

