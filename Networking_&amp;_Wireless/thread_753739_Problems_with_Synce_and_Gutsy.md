---
title: "Problems with Synce and Gutsy"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by tsbaker on 2008-04-13
I have everything working up til the part where I need to start sync-engine and then I get this error message:

root@tyler-laptop:~# sync-engine
SynCE sync-engine starting up
Traceback (most recent call last):
  File "/usr/bin/sync-engine", line 84, in <module>
    configObj = Config.Config(progopts)
  File "/usr/lib/python2.5/site-packages/SyncEngine/config.py", line 292, in __init__
    oldconf = os.path.join(self.path,"config.xml")
AttributeError: Config instance has no attribute 'path'

on the sync wiki for ubuntu, it says I need to install config.xml to ~/.synce/config.xml

now I know that is suppose tobe the path to that location. I however don't understand where I'm supposed tobe saving this config file too. I tried what I thought might be it to no avail. 

I just got my new HTC Mogul running WM6 and I really want to get things going. Any help is of course greatly appreciated

Tyler

---

