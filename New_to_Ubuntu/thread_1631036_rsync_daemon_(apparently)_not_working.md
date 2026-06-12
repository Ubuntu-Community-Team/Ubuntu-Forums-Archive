---
title: "rsync daemon (apparently) not working"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by djmac on 2010-11-26
Hi there,

I have been successfully able to rsync between two computers using ssh without too many dramas. 

I would like to use the rsync daemon, so I can simplify and automate the process by using password files etc (i.e so I don't have to input the password each time). 

I tried (I am guessing unsuccessfully) to set up the rsync daemon. This is the error I get when I try to use the "--password-file=PASSWORD" option.

```
The --password-file option may only be used when accessing an rsync daemon
```

These are the settings I used:

/etc/rsyncd.conf
```
max connections = 2
log file = /var/log/rsync.log
timeout = 300

[share]
comment = Public Share
path = /home/share
read only = no
list = yes
uid = nobody
gid = nogroup
auth users = john
secrets file = /etc/rsyncd.secrets

```

/etc/rsyncd.secrets
```
john:password
```

Also I changed /etc/default/rsync to RSYNC_ENABLE=inetd, and installed xinetd and restarted etc. 

Cheers.

---

### Post by cj13579 on 2010-11-26
So I know its not exactly what you want to do but could you not setup rsync as a cronjob?

With that, instead of referring to a pw file isnt there a username/password switch than can be invoked?

Chris

---

### Post by djmac on 2010-11-26
Thanks for your reply. 

The 'client' is actual running in a cygwin environment (not Ubuntu - the server is in Ubuntu). I am not that familiar with cygwin, and while I am sure you could probably run cron in cygwin, it might be a bit beyond me. (FYI, I am running the rsync command via a *.bat script, and doing a 'pseudo cronjob' it by running the *.bat script with AT.exe) 

I can't really run a cronjob on the server either, as the client has a dynamic IP (i.e a 'pull' rsync from the server would have a constantly changing source location). I also don't know how difficult it is to 'pull' from cygwin (who knows?)

On the bright side, it seems I am getting somewhere with my problem. I think it is just an issue with permissions not 'lining up' (and a faulty path in the /etc/rsyncd.conf). Will report back.

Cheers

---

