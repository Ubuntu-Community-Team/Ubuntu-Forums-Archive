---
title: "/var/cache folders"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-12-02
I've been messing around with a few different applications lately that I have just uninstalled. One such application was Google Desktop. After I ran the command to remove it dpkg told me that there were still files in /var/cache/google. I also run Google Chrome and I removed the folder google in /var/cache. There were only references to Desktop so I thought it would be safe. It seems to be that way and I just wanted to make sure the it's okay to delete folders in /var/cache?

Also, if another Google application needs to write to the /var/cache/google folder, will it just re-create it? What is the purpose of /var/cache?

Thanks

---

### Post by wojox on 2009-12-03
/var/cache is intended for cached data from applications. Such data is locally generated as a result of time-consuming I/O or calculation. The application must be able to regenerate or restore the data. Unlike /var/spool, the cached files can be deleted without data loss. The data must remain valid between invocations of the application and rebooting the system.

Files located under /var/cache may be expired in an application specific manner, by the system administrator, or both. The application must always be able to recover from manual deletion of these files (generally because of a disk space shortage). No other requirements are made on the data format of the cache directories. 

[See here]("http://www.pathname.com/fhs/2.2/fhs-5.5.html")

---

### Post by Martin Marshalek on 2009-12-03
Thank you wojox, that link is great. I'm probably going to use this a lot more when I have questions about folders in linux.

---

