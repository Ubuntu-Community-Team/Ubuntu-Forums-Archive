---
title: "script in if-up.d is not called"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by mrit on 2007-10-06
i have a strange situation with my new server.

ubuntu 7.04, kernel 2.6.20-15-generic, x86_64.

when i place a script in /etc/network/if-up.d it won't run at boot (when the network starts).
```
#!/bin/sh

/bin/echo "`date`: NETWORK IS UP" >> /var/log/syslog
```

this is the "simplies" script ever, chmod 755, owner root:root. but the script is not called i don't see anything in syslog, when called by hand it logs to syslog.

the strange thing is, that a firewall/iptables-script build via fwbuilder is called, the iptables rules are present at start. the rules aren't stored anywhere else, or?

the main problem was, that i wanted to set a default route at boot, and thought i could place a little script in if-up.d dir. at the moment i call it in rc2.d, but this is just a work-a-round...

markus

---

### Post by noob12 on 2007-10-06
Does it also not work if you replace `date` with `/bin/date` or a fixed string, or set a PATH?

---

### Post by mrit on 2007-10-07
mh,
i've added /bin/date, even complete PATH 

```
#!/bin/sh
export PATH="/sbin:/usr/sbin:/bin:/usr/bin:$PATH"
/bin/echo "`/bin/date`: NETWORK IS UP" >> /var/log/syslog
```

but nothing is logged in syslog when system is booting... should go there, syslogd is not needed... seems that if-up.d scripts are not called. it's a server-install, so network-manager and such are not installed - think this is good...

---

### Post by noob12 on 2007-10-08
Possible that syslogd is starting later and moving syslog to syslog.*n*.  Try another experiment writing to a file in /tmp.

---

### Post by sonicx on 2007-10-08
use some beeps, skript i just placed in /etc/ppp/ip-up.d beeps nicely on each connection. ubuntu-server install too.
regards,
sonicx

---

