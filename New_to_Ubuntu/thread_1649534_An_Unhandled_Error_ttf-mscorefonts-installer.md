---
title: "An Unhandled Error: ttf-mscorefonts-installer"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by White_Fox112 on 2010-12-20
Was all good until today - now i cant seem to install any software using the Software Centre...here's the details:
[I]
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.[/I]


Any ideas?

Thanks!

---

### Post by dargaud on 2010-12-20
Maybe you removed something (like Wine) which was using those fonts, and they are still required by that python script but the dependencies are mishandled. Try:
```
sudo aptitude install ttf-mscorefonts-installer
```

---

### Post by White_Fox112 on 2010-12-20
> **dargaud said:**
> Maybe you removed something (like Wine) which was using those fonts, and they are still required by that python script but the dependencies are mishandled. Try:
```
sudo aptitude install ttf-mscorefonts-installer
```

```
me@ubuntu:~$ sudo aptitude install ttf-mscorefonts-installer
sudo: aptitude: command not found

```

:?

---

### Post by coffeecat on 2010-12-20
> **White_Fox112 said:**
> ```
me@ubuntu:~$ sudo aptitude install ttf-mscorefonts-installer
sudo: aptitude: command not found

```:?

Curious. Which version of Ubuntu are you using? I know the intention is to remove aptitude from the list of default applications in Natty/11.04. Perhaps it was removed from Maverick as well - whatever.

Anyway, go to System > Administration > Synaptic. Search for ttf-mscorefonts-installer. Is the box green? If not, mark it for installation and click on 'Apply'. If the box is green, right-click on it and select 'Reinstallation' and then 'Apply'. See if that helps.

---

### Post by White_Fox112 on 2010-12-20
Synaptic Package Manager wont even open...

```
E:dpkg was interrupted, you must manually run 'sudo dpkg -configure-a' to correct the problem.

E:_cache->open() failed, please report.
```


Using 10.10

---

### Post by coffeecat on 2010-12-20
> **White_Fox112 said:**
> Synaptic Package Manager wont even open...

```
E:dpkg was interrupted, [COLOR=Red]you must manually run 'sudo dpkg -configure-a' to correct the problem.[/COLOR]

E:_cache->open() failed, please report.
```Using 10.10

Did you retype the error? Because I believe it should be: 

```
sudo dpkg --configure -a
```Run that in a terminal.

---

### Post by Addor on 2010-12-20
Hey there, I signed up because I'm having the same problem.

```
 dpkg --configure -a 
```returns

```
 dpkg: status database area is locked by another process 
```:/

---

### Post by coffeecat on 2010-12-21
> **Addor said:**
> ```
 dpkg --configure -a 
```returns

```
 dpkg: status database area is locked by another process 
```:/

Close Synaptic, Update Manager or Software Centre, whichever you have open.

---

### Post by White_Fox112 on 2010-12-21
I get 

```
dpkg: requested operation requires superuser privilege
```

Which is strange... i try entering my 'su' password, but it doesnt have it; its definitely the correct password (i enter it successfully each time i get asked for permission to install something)

---

### Post by coffeecat on 2010-12-21
Use sudo.

---

### Post by MrMikie1954 on 2011-09-22
I just had the same issue last night. 

Today I went to systems and ran the update manager and it did a partial update and fixed it. It did take a while to run, so be patient.

---

