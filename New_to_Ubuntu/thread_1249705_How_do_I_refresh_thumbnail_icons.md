---
title: "How do I refresh thumbnail icons?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by mvalviar on 2009-08-25
I did a reinstall of ubuntu. I copied my vids from backup before in installed the necessary codecs. All of them doesn't have thumbnail icons but new videos I add has thumbnails. For the sake of OCness how do I give all of them thumbnails?

---

### Post by Technoviking on 2009-08-25
You can try deleting the directory /home/username/.thumbnails and the thumbnails should be recreated.

```
rm -rf .thumbnails
```

or better yet, in case of problems

```
mv .thumbnails .thumbnails.bak
```
T-V

---

### Post by mvalviar on 2009-08-26
Works like a charm. Thanks.

---

