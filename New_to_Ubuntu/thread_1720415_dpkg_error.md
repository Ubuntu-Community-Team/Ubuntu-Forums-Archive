---
title: "dpkg error"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Dinmiller on 2011-04-03
Hey all, Ok Software center is not working for me, i thought i was needing to install Java, but i got it a different way, but i have the dpkg that is apparently stuck and will not let me do anything. I keep getting errors anytime i attempt to install anything new now. Here is the errors i get

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-bin package. This might mean you need to manually fix this package.


Any help would be appreciated.

---

### Post by yeats on 2011-04-03
Okay... what happens when you try (in a terminal):

```
sudo apt-get update
sudo apt-get -f install
```?

---

### Post by Dinmiller on 2011-04-03
It wants to install java but i dont need it i already have everything up to date

---

### Post by Dutch70 on 2011-04-03
You may also want to try this one...
```
sudo dpkg --configure -a
```

---

