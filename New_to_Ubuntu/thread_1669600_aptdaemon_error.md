---
title: "aptdaemon error"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Tori_chibi on 2011-01-17
While i was downloading software off the Ubuntu Software Center, my computer froze so i had to re-boot, now when i go to try and re-download the things i was downloading just fine before the computer froze, i get this message:

> There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.


and here is the Details:
> raceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the kdebase-runtime package. This might mean you need to manually fix this package.



anyone have a fix to this? I believe im currently running ver.10.4

---

### Post by ecm86 on 2011-01-20
OK. I had the same problem and I am running 10.10 netbook remix. Last night I found a **solution** but I am not sure it will work for everyone.

Note: I too, had my computer freeze and had to click shutdown when installing something from the software center. When I restarted, I was faced with the same msg you got and couldn't install anything from the center. 

So, what I did was try to install something from the software center using "terminal" (this can be found under applications...just type it in the search bar.) 

In "terminal" I logged in with this command:
**sudo -i**
and then it asks for your **password** and you just type your system password that you use for everything basically.

AFTER THAT YOU SHOULD BE LOGGED IN AS "root". THEN YOU TYPE:
**sudo apt-get install** calibre
YOU CAN OF COURSE TYPE **WHATEVER PROGRAM YOU LIKE** AFTER "install". CALIBRE IS WHAT I TRIED AND IT WORKED.

After **doing this** and successfully installing this, I was **able to resume downloading from the software center** as I had before. It seemed to** set things straight i**n the system,,,, How it worked, I have no freaken idea but it did. 

Anyways, I hope this helped you and perhaps others. 

Now, I have had a problem with the new **10.10 netbook remix** and I am going to put it our there for you or anyone who might know a fix or why it's happening.

 Whenever I shutdown, sleep or do a fresh start-up, it works great but when I try to RESTART. I does the whole shutdown thing but when it gets to the point where it should be restarting, I get a black screen and it seems to get stuck and not restart at all. I have had to hold the power switch to get it to turn off. 

When I turn it back on, it works fine. SO, in short, MY** RESTART DOESN'T WORK**. Anyone have this problem with the netbook remix 10.10 or **know how to fix it?**

Thanks,

Ed

---

