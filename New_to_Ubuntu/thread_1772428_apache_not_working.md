---
title: "apache not working"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by drathi on 2011-05-31
Hi,

On my Ubuntu system,apache is corrupted and when I try to restart ,It showing this below message:


/etc/init.d/apache2 restart
 * Restarting web server apache2                                                (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs


Please help me to sort out this issue.

Thanks
Deepak


Thanks,
Deepak

---

### Post by mishathegoat on 2011-05-31
Have you tried:
```
*sudo* /etc/init.d/apache2 restart
```

---

### Post by azim.charaniya on 2011-05-31
try this 
[http://ubuntuforums.org/showthread.php?t=979881](http://ubuntuforums.org/showthread.php?t=979881)

---

