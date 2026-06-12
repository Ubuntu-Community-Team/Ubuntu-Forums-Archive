---
title: "xinetd doesn't seem to work"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Bill Cosby on 2008-06-17
Hi there,

I have the Ubuntu Server Edition installed on my system, as services I want to run bitlbee and vsftpd over xinetd.
As standalone deamons both servers work fine, but xinetd somehow doesn't work.
I don't even get a log file, eventhough I specified one:

xinetd.conf
```

defaults
{
       instances       = 4
       log_type        = FILE /var/log/servicelog
       log_on_success  = HOST PID
       log_on_failure  = HOST RECORD
       #only_from      = 192.168.1.3
}
 
includedir /etc/xinetd.d
```

and e.g. vsftpd in /etc/xinetd.d
```

service ftp
{
       disable         = no
       socket_type     = stream
       protocol        = tcp
       wait            = no
       user            = ftp
       server          = /usr/sbin/vsftpd
}

```

I am really wondering what that could be, when I start xinetd with
    # /etc/init.d/xinetd restart
it seems to work fine, but I can't connect to any of my services, and not even the log file is written :(.
I don't know what to do.

regards,
Bill

---

### Post by Bill Cosby on 2008-06-19
Hmm, maybe I should change the runlevel of xinetd?
Can anyone start xinetd, and tell me which runlevels he uses?

---

