---
title: "gpg error"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by johnystevenson on 2008-12-05
anyone know how i can resolve this error :

W: GPG error: [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

regards
johny

---

### Post by Michael.Godawski on 2008-12-05
Try this:
```
sudo apt-get update -o Acquire::http::No-Cache=true
```Found:[http://ubuntuforums.org/showthread.php?p=6074077](http://ubuntuforums.org/showthread.php?p=6074077)

---

### Post by johnystevenson on 2008-12-05
many thanks for your reply.  will try it and see how i get on
regards
johny

---

