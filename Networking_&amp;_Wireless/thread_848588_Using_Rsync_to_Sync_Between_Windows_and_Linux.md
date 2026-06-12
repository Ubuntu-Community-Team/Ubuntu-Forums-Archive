---
title: "Using Rsync to Sync Between Windows and Linux"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by seuzy13 on 2008-07-03
I'm having some problems finding a good walkthrough for this. I have Cygwin installed on Windows (with rsync), and I have a configuration file on Linux for the daemon. Basically, I just copied it from the tutorial on everythinglinux.com--which doesn't explain everything very well--and modified it a little.

    motd file = /etc/rsyncd.motd
    log file = /var/log/rsyncd.log
    pid file = /var/run/rsyncd.pid
    lock file = /var/run/rsync.lock

    [simple_path_name]
       path = *My home directory*
       comment = Rsync server
       uid = nobody
       gid = nobody
       read only = no
       list = yes
       secrets file = /etc/rsyncd.scrt
       hosts allow = *My Windows IP address*

rsyncd.scrt reads as follows:
MyLinuxUsername=Password

The tutorial didn't really say what to do with that, so I took a guess. Anyway, rsyncing doesn't work, because when I enter my password it says "permission denied," even though it should be the right password.

I don't know a lot about what I'm doing, so feel free to explain things to me like I don't know what I'm doing. :-)

---

### Post by funkydan2 on 2008-07-04
In my password file, the username and password are seperated by a colon (:) not an equals sign.

Also, the secrets file needs to be readable only by the root user, so you might need to
'sudo chmod 600 /etc/rsyncd.scrt'

---

