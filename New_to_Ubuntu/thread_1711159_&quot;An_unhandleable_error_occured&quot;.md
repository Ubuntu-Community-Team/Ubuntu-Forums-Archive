---
title: "&quot;An unhandleable error occured&quot;"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by Socinus on 2011-03-20
When attempting to install software from the Ubuntu Software Center, I'm greeted by this.

"An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

DETAILS:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package."

---

### Post by K_Boomer on 2011-03-20
Do you have update manager running? Are you trying to install anything through terminal?

If so, stop those processes before using SPM

---

### Post by Socinus on 2011-03-20
> **K_Boomer said:**
> Do you have update manager running? Are you trying to install anything through terminal?

If so, stop those processes before using SPM
I dont believe so, how would I check and then stop these processes if necessary?

---

### Post by synapsys on 2011-03-20
> **Socinus said:**
> I dont believe so, how would I check and then stop these processes if necessary?

If these were active, you would have windows open. You would simply need to close the windows. Have you tried installing the package from the command line using apt?

```
sudo apt-get install msttcorefonts
```

---

### Post by Socinus on 2011-03-21
> **synapsys said:**
> If these were active, you would have windows open. You would simply need to close the windows. Have you tried installing the package from the command line using apt?

```
sudo apt-get install msttcorefonts
```
That worked, thank you :)

We've been having power trouble here all day because of the storms and the installation must've gotten cut during an outage :)

---

