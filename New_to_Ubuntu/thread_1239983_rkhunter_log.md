---
title: "rkhunter log"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by heyyy on 2009-08-14
i recently install rkhunter and a system check and among others(which were ok) gave me this: 
 ```
   .....
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]
      ....
```

should i be concerned about it?

---

### Post by 3rdalbum on 2009-08-14
You'd need to check the rkhunter logs to find out what the warning is, but it looks like rkhunter at this point is checking the integrity of those programs against what it thinks is correct.

It's highly unlikely that the "unhide" command has been tampered with, because it has been installed as a dependency of rkhunter - and any rootkit that fast wouldn't tamper with "unhide" and not tamper with "rkhunter".

Finally, the only way to get rootkits is to be running services that are listening to incoming ports. If you're not running any servers or you are behind a firewall that is set to "block all", then there's no way you can have a rootkit.

---

### Post by heyyy on 2009-08-17
i checked the log and itgave me this:
```
...
[11:34:05] /usr/sbin/unhide                                  [ Warning ]
[11:34:05] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[11:34:05] /usr/sbin/useradd                                 [ OK ]
[11:34:06] /usr/sbin/userdel                                 [ OK ]
[11:34:06] /usr/sbin/usermod                                 [ OK ]
[11:34:06] /usr/sbin/vipw                                    [ OK ]
[11:34:06] /usr/sbin/unhide-linux26                          [ Warning ]
[11:34:06] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
...
```

---

