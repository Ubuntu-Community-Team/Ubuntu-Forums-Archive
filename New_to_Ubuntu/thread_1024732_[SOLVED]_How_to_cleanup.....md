---
title: "[SOLVED] How to cleanup...."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by vagelism on 2008-12-29
Hello to all. 
I am totally new to the Ubuntu system and I am wondering. What should I periodically clean up in order to keep my system in good condition.
In windows for example (ok I admit I said a bad word) :) there is a clean up button. Straight forward I think. Here...?
This file structure here is new to me and I do not have a clue on what to delete and what not.
Any help will be appreciated.

Thank you

---

### Post by bryncoles on 2008-12-29
open a terminal and type in

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

you really only need to do this when you've been installing and uninstalling a lot of stuff. it'll remove any clutter that got left behind.

thats it really, and i never use the second two commands. 

linux systems arent very good at collecting clutter im afraid, so a lot of your maintenance routes will become obsolete!

*edit*

open a terminal and type 

```
man apt-get
```

to get some incomprehensible geek-speak on what these commands actually do! ;)

also, dont worry about defragging the system. ext3 (the filetype ubuntu defaults to) isnt prone to fragmentation in the same way as windows

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by mikeyphi on 2008-12-29
Normally not much need to clean up!!

However, have a look at this site: [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by 67GTA on 2008-12-29
[http://ubuntuforums.org/showthread.php?t=140920&highlight=clean](http://ubuntuforums.org/showthread.php?t=140920&highlight=clean)

---

### Post by oldos2er on 2008-12-29
"This file structure here is new to me and I do not have a clue on what to delete and what not. '

 If you don't know what it is, leave it alone. 

 There shouldn't be much in / that you need to fix. /tmp is cleared out automatically on reboot; /var/log/ should be able to take of itself too most of the time. If you install and uninstall a lot of software, there could be some broken links, but this shouldn't be a cause for worry since they won't affect your system's speed and/or stability.

 But if you still feel the need to tinker, look into the program fslint.

 Here's an explanation of Linux file system structure: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html) and the ext3 file system: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

