---
title: "[SOLVED] rsh server not working"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by jakommo on 2008-04-14
Hi,

I need to use rsh to execute a command remotely on one of my machines.
I installed xinet.d and rsh-server but every time I try to run the command I get this.
 ```
ticket ~ # rsh 10.2.2.148 -l root date
Couldn't get address for your host (ticket.local)

```
and this is the syslog from the machine where the rsh-server is running.
```
Apr 14 20:39:04 money rshd[8551]: Couldn't look up address for ticket.local: Name or service not known
```

with nslookup I can resolve the ip and the hostname on both machines.

these are my config files (maybe I forgot something)

xinet.d is running

```
root@money:/etc/xinetd.d# cat rsh 
service shell
{
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        group           = tty
        server          = /usr/sbin/in.rshd
        log_on_success  = PID HOST USERID EXIT DURATION
        log_on_failure  = USERID ATTEMPT
        disable         = no
}


```

```
root@money:/etc# cat securetty | grep rsh
rsh
root@money:/etc# 
```

```
root@money:/etc/pam.d# cat rsh 
#
# The PAM configuration file for the rsh (Remote Shell) service
#
# Due to limitations in the rsh protocol, modules depending on the conversation
# function to work cannot be used.  This includes authentication modules such
# as pam_unix.so.

auth    required        pam_nologin.so
auth    required        pam_env.so
auth    required        pam_rhosts_auth.so
account required        pam_unix_acct.so
session required        pam_unix_session.so
auth    sufficient      pam_rootok.so

```

```
root@money:/etc# cat hosts.equiv 
# /etc/hosts.equiv: list  of  hosts  and  users  that are granted "trusted" r
#                   command access to your system .

+ ticket.local root

```

```
root@money:~# cat .rhosts 
ticket.local root
```

can someone help me?

regards

jakommo

---

### Post by jakommo on 2008-04-15
Ok its working now, I had to insert the host into /etc/hosts.

---

