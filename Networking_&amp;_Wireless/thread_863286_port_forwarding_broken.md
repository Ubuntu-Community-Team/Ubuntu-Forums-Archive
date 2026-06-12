---
title: "port forwarding broken"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by satimis on 2008-07-18
Hi folks,


Ubuntu LAMP 6.06 amd64


The captioned server can be ssh connected on local pc running;

$ ssh -p 2222 192.168.0.52


It has been working couple months without problem.  Just discover it doesn't work.

$ ssh -p 2222 192.168.0.52```

Bad port ' 2222'

```


On /etc/ssh/sshd_config```

# What ports, IPs and protocols we listen for
Port 2222
Protocol 2
....

```
I haven't made any change on this file.


Another strange thing is /var/log/sshd.log disappeared.


$ sudo locate .log | grep sshd
No printout


Please help.  TIA


B.R.
satimis

---

### Post by kidders on 2008-07-20
Hi there,

> Bad port ' 2222'Try removing the space between "-p" and "2222".

---

### Post by satimis on 2008-07-20
> **kidders said:**
> Hi there,

Try removing the space between "-p" and "2222".
Hi kidders,


Thanks for your advice.


Really something funny has been happened here.  Its cause is known to me.


After switching off the server several hours it is working again now.


What I have done before;

deleting the content on;```

~.ssh/know-hosts

```


I have been running;```

$ ssh -p 2222 192.168.0.52

```

to connected the remote LAMP server for couple months without problem.


Just tried;```

$ ssh -p2222 192.168.0.52

```

It also works.  Now both of them can work w/o problem.


B.R.
satimis

---

