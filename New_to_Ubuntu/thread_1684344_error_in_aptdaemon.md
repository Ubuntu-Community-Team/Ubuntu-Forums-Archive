---
title: "error in aptdaemon"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by josephmills on 2011-02-09
Ok, so when I go to.Applications>Ubuntu Software Center>  I search for a program and then try to install it and this is what I get, 

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at link and retry.

So I reported it to the link. restarted the computer a couple of times nothing.  I looked at the details of it and this is what I see. 

 File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-symbol-replacement package. This might mean you need to manually fix this package.

Thanks you SO much for your time.

---

### Post by taseedorf on 2011-02-09
does it work if you go into synaptic?

---

### Post by josephmills on 2011-02-09
> **taseedorf said:**
> does it work if you go into synaptic?

yes it did work in synaptic and then after that I used software center and then that worked :confused: but its working :confused:

---

### Post by josephmills on 2011-02-09
even though everything seems to have worked out could someone tell me what happened with the software center thanks again for your time

---

### Post by P4man on 2011-02-11
Its a bug:
[https://bugs.launchpad.net/aptdaemon/+bug/659438](https://bugs.launchpad.net/aptdaemon/+bug/659438)

A fix has been released meanwhile.

---

### Post by hacker_at_linux on 2011-07-20
I am getting the same problem but its even worse. I am not able to install the packages even through synaptic also . It show exactly the same error as mentioned above.
Can any one help how to solve this thing

---

