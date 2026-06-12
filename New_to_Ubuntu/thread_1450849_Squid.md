---
title: "Squid"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by fly_boy on 2010-04-09
Hi, 

i am trying to get into the /var/logs/squid directory in order to begin configuring squid

I keep getting access denied errors...

How can I get access

Thanks

Alan

---

### Post by fly_boy on 2010-04-09
Additional

Whenever I start via the gui I also get the following error

Cant open the cache log here:
/var/log/squid/cache.log

---

### Post by natravis on 2010-04-09
You may need to launch it as root, though that seems to be bad program design. To launch the GUI as root, the command would probably be something like Alt+F2, then type ```
gksu squid
``` into the box. You may be looking at the wrong place, because the log files are almost never used to configure, unless you are troubleshooting. The configuration files are almost always stored in /etc or in your home folder as a hidden file (like .squid)

---

### Post by Barriehie on 2010-04-09
My config file is in /etc/squid/squid.conf   You might find [this](http://ubuntuforums.org/showthread.php?t=1338742) link helpful depending on what you're trying to block.  That link updates my blacklists.
```

02:48:56 /home/barrie $ >> cd ./squid
02:52:23 /home/barrie/squid $ >> wc --lines ./myblacklist ./domains ./urls
    1230 ./myblacklist
 1451821 ./domains
  179500 ./urls
 1632551 total
02:52:38 /home/barrie/squid $ >> 

```

---

