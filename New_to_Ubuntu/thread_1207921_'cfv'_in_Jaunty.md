---
title: "'cfv' in Jaunty"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by m_ad on 2009-07-08
```
[matt@matt-desktop:~]$ cfv
/var/lib/python-support/python2.6/cfv.py:670: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/var/lib/python-support/python2.6/cfv.py:699: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
0 files, 0 OK.  0.001 seconds, 0.0K/s
```

How can I fix this error? It produces the same error when I follow cfv with a .sfv file.

---

### Post by Mornedhel on 2009-07-08
It isn't an error, it's just a warning. I've had this since Dapper at least.

If I remember well, the correct way of using cfv is cd'ing into the directory and just running cfv without arguments.

---

