---
title: "kpackakekit, konsole, upgrades and installing programs"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by tzepu on 2009-09-26
hi guys
i am facing an issue about two days now
kpackagekit is useless , even console updating or upgrading just can't be done anymore
after some surfing i decided to try avast, but for hell knows what reason installation failed ( dependency problems)( i tried the .deb files from official site)
now the failed install hangs on  kpackagekit and konsole
i surfed for two day now and the advices found proved useless for me (i even installed an patch for utf)(on nabble i found a discussion list, i tried some advices from it)
if i try to upgrade programs, install some, refresh kpackagekit, i get this error

Traceback (most recent call last): File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run threading.Thread.run(self) File "/usr/lib/python2.6/threading.py", line 477, in run self.__target(*self.__args, **self.__kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 168, in wrapper func(*args, **kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1326, in doRefreshCache self._check_init((0,10)) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1756, in _check_init self._cache.clear() File "/usr/lib/packagekit/aptDBUSBackend.py", line 246, in clear self._depcache.Init() SystemError: E:The package avast4server needs to be reinstalled, but I can't find an archive for it.


apt-get tells me about avast and closes

aptitude gives me this

    E: I wasn't able to locate file for the avast4server package. This might mean you need to manually fix this package.
    Writing extended state information... Done
    E: I wasn't able to locate file for the avast4server package. This might mean you need to manually fix this package.
    E: Internal error: couldn't generate list of packages to download


i tried to manually manage the install, but i get the first error

the install -f, --cofigure -a commands solve nothing
can any of you help? even with a link to documentation, so to be able to solve it by myself and eventually understand what broke
thanks in advance
best regards

---

### Post by Darkwing-Duck on 2009-09-28
Sorry no one has gotten back to you. Okay. Does apt-get work at all? Tell me what is error is (if any) for the following command.

```
sudo apt-get update
```

It should scroll through a list of repositories.

Let me know and I will do what I can to help you out.

---

