---
title: "[SOLVED] rtorrent on startup"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by cdmike2k8 on 2008-12-16
I am trying to configure rtorrent to start in a screen session on startup, and am having some difficulty with setting it up.  I am using the script is provided on the rtorrent website [here]("http://libtorrent.rakshasa.no/attachment/wiki/RTorrentCommonTasks/rtorrentInit.sh").  It seems to run correctly, but it doesn't create the rtorrent file in /etc/init.d.  Here is the output ```
michael@computer:~$ sh rtorrentInit.sh 
Password: 
Password: 
Usage: /etc/init.d/rtorrent {start|stop|restart|force-reload}
michael@computer:~$ ls -l /etc/init.d/rtorrent
ls: cannot access /etc/init.d/rtorrent: No such file or directory
```
Attached is the script, configured as I think that I need to.  Any help would be appreciated.  Thanks, Michael

---

### Post by cdmike2k8 on 2008-12-17
Bump, it is ubuntu 8.10 server, by the way

---

