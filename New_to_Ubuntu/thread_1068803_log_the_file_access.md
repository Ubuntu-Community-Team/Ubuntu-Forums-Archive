---
title: "log the file access"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by cosine352 on 2009-02-13
Hi All,
I was wondering if it is possible to log the event if a file is access (read or write). For example I want to log the event of the file 'test'. Now if I run this command
> ls -lu $HOME/test
it will give the last time. What I want to do is automatically run this command each time the file 'test' is read or write. 

Thanks for your help

---

### Post by HavocXphere on 2009-02-13
I think Tripwire should be able to do that...wasn't designed for that though.

---

### Post by cosine352 on 2009-02-13
> **HavocXphere said:**
> I think Tripwire should be able to do that...wasn't designed for that though.
thanks HavocXphere. I will try that.

---

