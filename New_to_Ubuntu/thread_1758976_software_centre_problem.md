---
title: "software centre problem"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by fractalman on 2011-05-15
Ok i installed 11:04 on my p hard drive earlier, everything went fine, i copied all my music and stuff over, installed loads of packages without any problems,   but i have just gone to install UFW firewall config from the software centre and i am getting the following error


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


i tried a few other apps but got the same message, how do i rectify this so i can use the software centre again? cos i need to install the ufw app:)

---

### Post by sikander3786 on 2011-05-15
Start Terminal and please post the output of these commands.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

While posting, you'll need to paste your text in between the [code] tags by clicking the # icon in post menu to make it easy to read and take less space.

---

### Post by fractalman on 2011-05-15
Hi thanks, i think i have sorted it out,  i had installed google earth and messed something up, i got an error trying to access the synaptic manager which told me to use

sudo dpkg --configure -a
i ran that then i could access the spm removed google earth totally and it installed the ttf-mscorefonts-installer package  in the process.

i can now download from software centre again:D

thanks for the reply though, much appreciated

---

