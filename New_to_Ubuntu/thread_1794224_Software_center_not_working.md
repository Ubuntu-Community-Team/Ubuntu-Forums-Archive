---
title: "Software center not working"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by aykoola on 2011-06-30
Software center won't install anymore programs on my computer. It says:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


HELP PLEASE! :(

---

### Post by CaptainMark on 2011-06-30
open  a terminal and use ```
sudo apt-get install -f
```to get apt-get to attempt to fix broken packages

---

### Post by aykoola on 2011-06-30
and how do i click ok when the blue screen with text appears?

thank you!

edit: oh, dumb me :facepalm

edit 2: IT WORKS!!! THANK YOU VERY VERY MUCH!

---

### Post by Brushstroke on 2011-06-30
Blue screen with text? What?

Just run from the Terminal: 

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install ttf-mscorefonts-installer
```That'll get the APT package manager (the thing that installs all your software) to try to repair whatever is broken, update the repositories, and reinstall the package that appears to be an issue.

EDIT: Nevermind, I see you've got things solved! Be sure to mark this thread as solved. :)

---

