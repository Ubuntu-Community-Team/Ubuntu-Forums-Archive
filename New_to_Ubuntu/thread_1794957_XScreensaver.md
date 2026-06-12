---
title: "XScreensaver"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by fslezak on 2011-07-01
I just loaded XScreensaver on my box via the following thread:

[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)


XScreensaver works fine, except that when I try to lock, I get:

```

$ xscreensaver-command -lock
xscreensaver-command: locking not enabled.

```System Info:

Ubuntu 11.04 running off USB pen drive (Using persistent as casper-rw partition)
NOTE: I take this between computers, so I need a solution that won't get erased.

---

### Post by jtarin on 2011-07-01
Did you try this fix:```
 sudo ln -f /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```To reverse```
 sudo unlink /usr/bin/xscreensaver-command 
```

---

### Post by linuxninja39 on 2012-09-13
I'm also on a persistent thumb drive and having this same problem. Did you ever find a solution?

---

