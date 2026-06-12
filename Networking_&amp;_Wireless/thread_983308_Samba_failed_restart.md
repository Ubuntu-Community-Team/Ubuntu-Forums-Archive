---
title: "Samba failed restart"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by shanep-server on 2008-11-15
I tried to restart samba 

/etc/init.d/samba restart

   * Stopping Samba daemons
start-stop-daemon: warning: failed to kill 6750: Operation not permitted
start-stop-daemon: warning: failed to kill 6752: Operation not permitted
                                                                    [ OK ]
   * Starting Samba daemons                                         [fail]

Not sure what all this means? My samba didn't restart? 
I was trying to follow a tutorial for sharing files with xp. Trying to set up my laptop to share files with my home server ( ubuntu ) and my roomates computer ( WinXP )

Any help would be appreciated.

---

### Post by Iowan on 2008-11-15
Try it with **sudo**:
```
sudo /etc/init.d/samba restart
```.

---

