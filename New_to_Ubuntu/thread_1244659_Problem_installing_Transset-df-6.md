---
title: "Problem installing Transset-df-6"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by guv999 on 2009-08-19
Hi I have downloaded the above file to my desk top and have followed the instructions at regarding installation at:
[http://transset-df.forchheimer.se/](http://transset-df.forchheimer.se/)
I keep returning the following error message in the terminal

dave@dave-desktop:~$ tar zxf transset-df-6.tar.gz
tar: transset-df-6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Any help greatly appreciated

---

### Post by michy99 on 2009-08-19
You need to change to your Desktop directory first.```
cd Desktop
tar zxf transset-df-6.tar.gz
```

---

### Post by guv999 on 2009-08-20
Thanks a lot - that was what I was missing

---

