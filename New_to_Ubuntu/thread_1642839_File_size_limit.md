---
title: "File size limit?"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Telos3K on 2010-12-10
I'm exporting the results from a query on a remote MySQL server as an Excel file.  It downloads fine, but when I try to open it, it only contains one cell:

```
Fatal error:  Allowed memory size of 134217728 bytes exhausted (tried to allocate 16 bytes) in /usr/share/phpMyAdmin/libraries/PHPExcel/PHPExcel/Cell.php on line 135
```

I've exported and opened files of this size in xp, no problem.  My understanding is that Ubuntu does not have file size limits.  

What's up?

Thanks!

---

### Post by sandyd on 2010-12-10
> **Telos3K said:**
> I'm exporting the results from a query on a remote MySQL server as an Excel file.  It downloads fine, but when I try to open it, it only contains one cell:

```
Fatal error:  Allowed **memory size** of **134217728 bytes** exhausted (tried to allocate 16 bytes) in /usr/share/phpMyAdmin/libraries/PHPExcel/PHPExcel/Cell.php on line 135
```I've exported and opened files of this size in xp, no problem.  My understanding is that Ubuntu does not have file size limits.  

What's up?

Thanks!
its the limit on the remote sql server.
its the RAM limit that a single script can use.

---

### Post by HermanAB on 2010-12-11
Howdy,

Use mysqldump.

---

