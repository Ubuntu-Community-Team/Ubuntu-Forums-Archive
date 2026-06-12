---
title: "&quot;An unhandlable error occured&quot;"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by rlampz on 2011-03-13
Hello,

This is my first forum post anywhere... EVER. I am very new at Ubuntu (it is fantastic!) and I have run into a few problems. I was trying to get Microsoft Word to run with Wine (or however it's supposed to work) and I was downloading some packages with the Ubuntu Software Centre... something happened (I can't remember exactly what) and I now whenever I try to download anything from the USC, I get this error message. 

"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry."

(If it helps, here are the "details")
"
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
"

Like I said, I am a newbie and I have no idea what I've done, what is wrong, or what to do. If somebody could help me out, that'd be great! Thank you!

Ryan

---

### Post by Wobblybob on 2011-03-13
Try opening the Synaptic package manager click on the [status] button on the left hand side and check if these is a broken package item in the list above it, if so go to [edit], [fix broken packages]

---

### Post by rlampz on 2011-03-14
When I tried opening The Synaptic Package Manager, I got this error message and it closed down.

An Error Occurred
The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I couldn't even get into the SPM.

---

### Post by Wobblybob on 2011-03-14
ok so open a Terminal and enter

sudo dpkg --configure -a

then press enter and type in your password when prompted, if all goes well then run

sudo apt-get update

and post any error messages

---

