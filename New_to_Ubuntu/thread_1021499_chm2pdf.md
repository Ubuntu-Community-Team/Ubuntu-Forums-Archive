---
title: "chm2pdf"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by 21:27 on 2008-12-25
Can anybody tell me what am I doing wrong?
I have the file I want to convert on my desktop.

/usr/bin/chm2pdf --book --datadir /home/john/Desktop my-file.chm

CHM file "c++pp4th.chm" not found!

---

### Post by spiderbatdad on 2008-12-25
havent used chm2pdf for a while, but it usually works well. Try running without the --book option, or with no options. This should produce a directory containing the file you need. One of them will be the pdf text.```
chm2pdf /home/john/Desktop/my-file.chm

```Also the command in your post is missing the forward slash after Desktop.

---

### Post by 21:27 on 2008-12-25
chm2pdf --webpage /home/john/Desktop/my-file.chm
worked
I am new at this, so i did not realize how to specify file location correctly. Thanks.

---

