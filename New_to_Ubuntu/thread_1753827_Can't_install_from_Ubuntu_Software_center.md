---
title: "Can't install from Ubuntu Software center"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by p1ngp0ng123 on 2011-05-09
I was trying to install Skype using the Ubuntu Software Center on my ASUS EeePC running Ubuntu 10.10, but I got this error message when I verified my password:


An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

And when I clicked "Details", I got this:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

Earlier, I'd tried to install the sun-java6-fonts package from [here.]("http://embraceubuntu.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/")I can't seem to get rid of it. I can't even do sudo apt-get upgrade! :( 


How do I fix this???:confused:

---

### Post by mr_luksom on 2011-05-11
Your best bet is to file a bug at launchpad. It will come to the attention of someone who is an expert in apt, and given it is repeatable it should be straightforward to diagnose.

---

### Post by debd on 2011-05-11
```
sudo dpkg -r sun-java6-jre
```

see if this can uninstall the package.

---

### Post by p1ngp0ng123 on 2011-05-11
@ debd

I tried that code, and all I got was this message:


dpkg: status database area is locked by another process

Any ideas? :(

@ Mr_luksom

All I got there were complaints and a few suggestions that didnt work.

---

### Post by Bapun007 on 2011-05-11
> **p1ngp0ng123 said:**
> @ debd

I tried that code, and all I got was this message:


dpkg: status database area is locked by another process


That mean software center or synaptic is not closed correctly and still running . Reboot your computer and try that command again .

---

### Post by p1ngp0ng123 on 2011-05-11
> **Bapun007 said:**
> That mean software center or synaptic is not closed correctly and still running . Reboot your computer and try that command again .

Nope. Just got this:

dpkg: error processing sun-java6-jre (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java6-jre

---

### Post by Bapun007 on 2011-05-11
since i am also new to linux , i think you have to reinstall java again .

---

### Post by wojox on 2011-05-11
> **p1ngp0ng123 said:**
> Nope. Just got this:

dpkg: error processing sun-java6-jre (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java6-jre

Try to fix it:

```
sudo apt-get install -f
```

If not:

```
sudo apt-get --purge remove --force sun-java6-jre
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by debd on 2011-05-14
while booting, log into recovery mode (keep shift or F6 pressed if its a wubi installation; sorry I dont remember the appropriate one), select the "remove broken packages" opt.

---

