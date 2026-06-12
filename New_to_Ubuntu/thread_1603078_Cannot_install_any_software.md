---
title: "Cannot install any software"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by scratchpost on 2010-10-22
When installing VLC, my computer hung so I manually shut it down.
Now I can't install any software!

Help! This is the error!

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libcddb2 package. This might mean you need to manually fix this package.

---

### Post by silbak04 on 2010-10-22
Try reinstalling it in the terminal. Once you get a terminal opened up, type in:

```

$ sudo aptitude install libcddb2

```

Then see if that works.

Hope this helps!

---

### Post by Hippytaff on 2010-10-22
Try
 
```

sudo apt-get remove (software name)

```
where software name id the name of the programme you tried to install
 
then
```

sudo apt-get autoclean

```
 
reboot and see if that works?
 
then maybe try reinstalling vlc

---

### Post by migs73 on 2010-10-22
A few of us have similar problems;

[http://ubuntuforums.org/showthread.php?t=1597784](http://ubuntuforums.org/showthread.php?t=1597784)

Looks like files aren't being removed/added properly. So far the only workaround is to manually delete/add the file(s) in question and try again.

Must be a bug in APT.

---

