---
title: "Running wow"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by antiblizzard on 2011-04-30
When I try to install this is the error I get 
Archive:  /tmp/InstallWoW-1.exe 
[/tmp/InstallWoW-1.exe] 
  End-of-central-directory signature not found.  Either this file is not 
  a zipfile, or it constitutes one disk of a multi-part archive.  In the 
  latter case the central directory and zipfile comment will be found on 
  the last disk(s) of this archive. 
zipinfo:  cannot find zipfile directory in one of /tmp/InstallWoW-1.exe or 
          /tmp/InstallWoW-1.exe.zip, and cannot find /tmp/InstallWoW-1.exe.ZIP, period. 
I am unsure how to fix this someone said something about changing the exe to wine exe if anyone can help please post.

---

### Post by Ken UK on 2011-04-30
You will have to explain what you are doing abit better.

So yuo have installed Wine and are installing from a WoW CD?

have you looked into using PlayOnLinux? It might be an easier option for you.

---

### Post by antiblizzard on 2011-04-30
File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

This is the report I got trying to install the playonlinux it is the same error I am getting for anything I try to install.

---

### Post by Joe of loath on 2011-04-30
Ubuntu is trying to open the exe file in archive manager. Right click, select properties, and change the 'open with' to WINE.

---

### Post by antiblizzard on 2011-04-30
fixed that problem it launches but I cannot see the video I hear the music of wow running but cannot see the screen when launcher switches over.

---

