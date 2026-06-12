---
title: "Samba share not accessible after apt-update and reboot"
date: 2014-01-15
forum: Networking &amp; Wireless
---

### Post by vmerz on 2014-01-15
Hi folks,  
after updating my ubuntu 12.04.3 LTS machine, my shared folders are not longer accessible. I can still see them from my windows-machine, but cannot access them. 
So let´s have a look at the configuration:  

```
 
#======================= Global Settings =======================
[global]
    log file = /var/log/samba/log.%m
    idmap gid = 10000-33554431
    obey pam restrictions = no
    map to guest = bad user
    encrypt passwords = yes
    realm = MYDOMAIN.LOCAL
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    server string = %h server
    idmap uid = 10000-33554431
    unix password sync = yes
    workgroup = MYDOMAIN
    os level = 20
    syslog = 0
    security = ADS
    usershare allow guests = yes
    panic action = /usr/share/samba/panic-action %d
    max log size = 1000
    log level = 10
    pam password change = yes

#======================= Share Definitions =======================

[MYDOMAIN]
    browseable = yes
    writeable = yes
    valid users = MYDOMAIN\domainuser,@MYDOMAIN\MYDOMAINshare
    public = yes
    path = /srv/share/MYDOMAIN

[share]
    browseable = yes
    writeable = yes
    valid users = MYDOMAIN\domainuser,@MYDOMAIN\MYDOMAINshare
    public = yes
    path = /srv/share/share 

```

here a snippet from samba logfile:

```

[2014/01/15 15:09:36.425111,  3] smbd/service.c:190(set_current_service)
  chdir (/srv/share/mydomain) failed, reason: Permission denied
[2014/01/15 15:09:36.425160,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/process.c(1558) cmd=162 (SMBntcreateX) NT_STATUS_ACCESS_DENIED

```

wbinfo -t is still working
```

checking the trust secret for domain MYDOMAIN via RPC calls succeeded

```

wbinfo -g is still giving me a list of domaingroups.

shure, i could rollback my server to the last existing configuration, but skipping all future updates sounds not like a good plan to me.
Any idea what could have caused the problem after my last reboot?

Thanks in advance,
Vinc

P.s.:
smbd --version
Version 3.6.3

---

### Post by Jason_Gibson on 2014-01-15
**path = /srv/share/MYDOMAIN** doesn't match **(/srv/share/mydomain)** in error output. That doesn't look right. Capitalization matters in linux file / path names and such. If you changed it I would imagine the reboot should have done this but maybe try ```
sudo /etc/init.d/samba restart
``` Only other thing that I'm thinking is permissions got changed somewhere?

---

### Post by vmerz on 2014-01-15
Hi Jason,

thanks for your hints.

> **Jason_Gibson said:**
> What are the permissions of the shared folders. Did they get changed somehow?

the permissions are 770 and they look like following:

```

drwxrwx--- 4 domainshare MYDOMAIN\MYDOMAINshare 4096 Jan 10 12:45 MYDOMAIN
drwxrwx--- 2 root            MYDOMAIN\MYDOMAINshare 4096 Jan  8 16:17 share

```

> **Jason_Gibson said:**
> 
[COLOR=#000000]/srv/share/MYDOMAIN in shares don't match /srv/share/mydomain in the error output. Permissions may have changed but that is the first thing i see out of place.[/COLOR]

okay, this was just a copy past failure while trying to cipher my domainname :)

> **Jason_Gibson said:**
> 
[COLOR=#000000]Side note and question. Why are you using the  public = yes then having valid users. Valid users seems to cancel out it  being public?[/COLOR]

  You´re right - this is just missconfigured, i´m going to change this.

---

### Post by vmerz on 2014-01-16
Might there be a connection between ldconfig and the samba problem?

---

### Post by vmerz on 2014-01-16
Solved it with the following hint:
[https://bugzilla.samba.org/show_bug.cgi?id=8676#c24](https://bugzilla.samba.org/show_bug.cgi?id=8676#c24)

---

