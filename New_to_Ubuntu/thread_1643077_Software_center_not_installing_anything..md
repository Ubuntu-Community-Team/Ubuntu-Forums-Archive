---
title: "Software center not installing anything."
date: 2010-12-11
forum: New to Ubuntu
---

### Post by drazelian on 2010-12-11
I tried to install a few games today. It had an error on warsow, and wouldnt install. Now whenever I try to install anything at all, I get this error.
```
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at http://launchpad.net/aptdaemon/+filebug and retry.
```
When I click details, this is what I get.
```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the warsow-data package. This might mean you need to manually fix this package.
```

I don't know why a failed install of warsow is affecting my ability to download and install all other programs. Help would be greatly appreciated. Thanks!

---

### Post by sanderd17 on 2010-12-11
Can you purge warsow?

```

sudo apt-get purge warsow

```

---

### Post by drazelian on 2010-12-11
Solved it myself, i typed
sudo apt-get install warsow, and now I have the ability to install things in the software center again

---

