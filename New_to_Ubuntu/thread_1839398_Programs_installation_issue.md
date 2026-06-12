---
title: "Programs installation issue"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by maghrebi on 2011-09-05
Hello guys,

I'm facing the below issue whenever I try to install any application.
I'm very new to ubuntu.




Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jdk package. This might mean you need to manually fix this package.





Any advice?


Maghrebi

---

### Post by saltmarshlamb on 2011-09-05
Hi - what issue are you facing?

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/11.04/ubuntu-help/index.html](https://help.ubuntu.com/11.04/ubuntu-help/index.html)

[https://help.ubuntu.com/11.04/ubuntu-help/addremove.html](https://help.ubuntu.com/11.04/ubuntu-help/addremove.html)

---

### Post by maghrebi on 2011-09-05
Hi Mate,

Thanks for your quick response.

Actually, I followed the instructions in the links above but as I mentioned earlier, I'm getting the below message whenever I try to install any application 

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jdk package. This might mean you need to manually fix this package.

By the way, Im using ubuntu software centre and the issue is the same.

Thanks,

Maghrebi

---

### Post by saltmarshlamb on 2011-09-05
Try and get the issue into the post the first time - you caught me with a ninja edit :p

Have a look here - [http://ubuntuforums.org/showthread.php?t=1767848](http://ubuntuforums.org/showthread.php?t=1767848)

There's a useful search engine here that I use. [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

