---
title: "Help, can't install anything."
date: 2011-09-07
forum: New to Ubuntu
---

### Post by camilo23 on 2011-09-07
im trying to install this app and it says that there is like unhandlable error?   the details say this  "Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package."
im new to ubuntu so no idea how to fix it or what its even wanting to fix lol so thanks for the help and time

---

### Post by Perfect Storm on 2011-09-07
Try with:
```
sudo apt-get --purge remove --force sun-java6-jre
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by camilo23 on 2011-09-07
it says this after the purge remove  "E: Command line option --force is not understood"

---

### Post by Perfect Storm on 2011-09-07
> **camilo23 said:**
> it says this after the purge remove  "E: Command line option --force is not understood"

Sorry, do it without --force flag.

---

### Post by camilo23 on 2011-09-07
> **Artificial Intelligence said:**
> Sorry, do it without --force flag.

it gives me this "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"  im new to ubuntu ive had it for 4 days thanks for ur time      but what should i do? lol

---

### Post by Perfect Storm on 2011-09-07
Make sure that Ubuntu Software Center or Synaptic Package Manager are not running when executing these commands. Then try again.

If it still complains, check "System Monitor" for "apt" process and kill it/them. Then try again. (right click on the apt process and choose "kill").

---

### Post by camilo23 on 2011-09-08
turned off the computer to make sure nothing was running and opened up only internet system monitor and terminal and shows same message
no apt process shows up

> **Artificial Intelligence said:**
> Make sure that Ubuntu Software Center or Synaptic Package Manager are not running when executing these commands. Then try again.

If it still complains, check "System Monitor" for "apt" process and kill it/them. Then try again. (right click on the apt process and choose "kill").

---

### Post by saltmarshlamb on 2011-09-08
If you've rebooted and still have the same error > E: Could not get lock /var/lib/dpkg/lock

Try this from a terminal

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by camilo23 on 2011-09-08
it just gives me more errors
i mite just uninstall and re-install this is a pain lol
> **Artificial Intelligence said:**
> Make sure that Ubuntu Software Center or Synaptic Package Manager are not running when executing these commands. Then try again.

If it still complains, check "System Monitor" for "apt" process and kill it/them. Then try again. (right click on the apt process and choose "kill").

---

### Post by camilo23 on 2011-09-08
thanks to everyone for their time

---

