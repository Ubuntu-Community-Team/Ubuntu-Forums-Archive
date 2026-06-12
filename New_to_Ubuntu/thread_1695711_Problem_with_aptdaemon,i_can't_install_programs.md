---
title: "Problem with aptdaemon,i can't install programs"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by Guch on 2011-02-26
Hi everybody, yesterday while i wanted to install some application i received this message:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the bugsx package. This might mean you need to manually fix this package.


I would appreciate any help on that, i must say that i'm totally new to ubuntu so please be quite explicit in your answer, thanks for your attention.

I have Ubuntu 10.10 netbook edition in an Acer Aspire One D255.

---

### Post by donkyhotay on 2011-02-26
> **Guch said:**
> Hi everybody, yesterday while i wanted to install some application i received this message:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the bugsx package. This might mean you need to manually fix this package.


I would appreciate any help on that, i must say that i'm totally new to ubuntu so please be quite explicit in your answer, thanks for your attention.

I have Ubuntu 10.10 netbook edition in an Acer Aspire One D255.

Looks like there is a problem with the package itself. Essentially it's running a python script and one of the files is missing. What were you trying to install and how were you trying to install it?

---

### Post by Guch on 2011-02-26
Thanks for your answer, yeah there was a problem with this program Bugsx, i uninstalled it and everything is normal, :P!!

---

