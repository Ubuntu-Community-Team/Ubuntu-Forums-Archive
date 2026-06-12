---
title: "Ubuntu Software Center locked up on &quot;Applying Changes&quot; - can't install anymore"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Clampdown on 2011-04-08
Hi!

So, last week I tried to install pidgin from the Ubuntu Software Center, and I ran into a somewhat familiar problem - the Software center locked up on "Applying Changes".

It says that Pidgin was installed, though it's not, and now I can't install or uninstall anything from Ubuntu Software Center. I get the following error message.

> Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the pidgin-data package. This might mean you need to manually fix this package.


So! How do I fix this?

---

### Post by Dutch70 on 2011-04-08
Try these 2 commands...
```
sudo dpkg install -f
```
```
sudo apt-get --configure -a
```

---

### Post by Clampdown on 2011-04-08
> **Dutch70 said:**
> Try these 2 commands...
```
sudo dpkg install -f
``````
sudo apt-get --configure -a
```

All I'm getting for those two is:
> 
Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

and

> E: Command line option --configure is not understood

I should also point out that it the Software Center doesn't say Pidgin is installed. It says pidgin-data is installed (which is from the error in the OP). I tried to uninstall it and it says 

> installArchives() failed: dpkg: error processing pidgin-data (--remove): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting a removal. 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 pidgin-data 


---

### Post by Clampdown on 2011-04-08
I fixed it!

Should've looked a little bit harder before posting, I suppose!

I did this, from another thread:

```
sudo dpkg --force-all --remove pidgin pidgin-data
sudo apt-get update && sudo apt-get -f install
```
from [here]("http://ubuntuforums.org/showthread.php?t=856756")

---

### Post by Dutch70 on 2011-04-08
Great! glad you got it fixed, and thanks for letting us know how you did it. :)

---

