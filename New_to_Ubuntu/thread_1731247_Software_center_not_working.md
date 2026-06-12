---
title: "Software center not working"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by abhishek39 on 2011-04-16
I can't install anything from software center.
like for example whenever i tried to install wine from software centre i got this error message.

**_An unhandlable error occured_**

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.



Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


WHAT TO DO PLZ HELP

---

### Post by stoogiebuncho on 2011-04-17
Open a terminal and try entering
```
sudo apt-get update
```

If that returns errors, post them here.  If not, try
```
sudo apt-get install wine
```

---

### Post by abhishek39 on 2011-04-17
> **stoogiebuncho said:**
> Open a terminal and try entering
```
sudo apt-get update
```

If that returns errors, post them here.  If not, try
```
sudo apt-get install wine
```

after the second step the END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE    
is displayed
there is no option to accept or decline the agreement.
how to close it, if i manually close the page wine is not installed
and after then if i try the third step it is saying something is using it.
sombody help, plz.

---

### Post by oldos2er on 2011-04-17
> **abhishek39 said:**
> after the second step the END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE    
is displayed
there is no option to accept or decline the agreement.


Use Page Down key, when you see 'OK' hit Tab to highlight it, then Enter to continue its installation.

---

