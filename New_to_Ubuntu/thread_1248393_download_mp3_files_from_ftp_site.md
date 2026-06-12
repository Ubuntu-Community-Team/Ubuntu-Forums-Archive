---
title: "download mp3 files from ftp site"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by lesterness on 2009-08-24
I need to download some mp3 files from an FTP site.  What Ubuntu programs for this are best?

Thanks.

Lesterness

---

### Post by wojox on 2009-08-24
Go to Places > Connect To Server
Service Type Public FTP or FTP with Login
Fill in the rest

---

### Post by credobyte on 2009-08-24
```
wget ftp://www.domain.com/song.mp3

```

---

### Post by XCan on 2009-08-24
gftp or filezilla if you plan to use ftp extensively. The built in support in Nautilus is fine, but it's slow as heck.

---

