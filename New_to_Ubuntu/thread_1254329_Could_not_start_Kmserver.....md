---
title: "Could not start Kmserver...."
date: 2009-08-31
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-08-31
Starting kate with root privelages from command line produces a how bunch of errors which eventually log me out....

```
carl@CarlsLaptop ~ $ sudo kate etc/usplash.conf
Error: "/var/tmp/kdecache-carl" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-carl" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-carl" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-carl" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-carl" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
Error: "/tmp/ksocket-carl" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-carl" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kded4
Error: "/var/tmp/kdecache-carl" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-carl" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-carl" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-carl" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-carl" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch
QThreadStorage: Thread 0x905cb48 exited after QThreadStorage 2147483641 destroyed
```

---

