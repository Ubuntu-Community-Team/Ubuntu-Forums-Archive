---
title: "snmp not working"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by lipos on 2007-09-04
hi,

i just did the snmpd installation on one of my linux machines and was trying to login using my community string and from some reason it's not working. i've scanned the port 161 and it's not responding.
my computers ip is 192.168.0.60
and this is my conf file
i used iptables -F to clean the config for testing reasons
the mistake i do it's probable a small one but i can't see it. can somebody help me with that?



#       sec.name  source          community
com2sec local         localhost       public
com2sec localNet      192.168.0.0 /24   public
#com2sec readwrite    default          private



#               sec.model  sec.name
group MyROSystem v1        local
group MyROSystem v2c       local
group MyROSystem usm       local
group MyROGroup v1         localNet
group MyROGroup v2c        localNet
group MyROGroup usm        localNet
group MyRWGroup v1         local
group MyRWGroup v2c        local
group MyRWGroup usm        local



#           incl/excl subtree                          mask
view all    included  .1                               80
view system included  .iso.org.dod.internet.mgmt.mib-2.system



#                context sec.model sec.level match  read   write  notif
access MyROSystem ""     any       noauth    exact  system none   none
access MyROGroup ""      any       noauth    exact  all    none   none
access MyRWGroup ""      any       noauth    exact  all    all    none

# -----------------------------------------------------------------------------

---

### Post by cagey cretin on 2007-09-04
Is the port open? Is the daemon running?

---

### Post by lipos on 2007-09-05
from some reason port is closed when i'm scanning form my machine and it should be visible
deamon is started

snmp      9811  0.0  1.0   7096  3964 ?        S    Sep04   0:00 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1

any ideas?

---

### Post by FiFtHeLeMeNt on 2007-09-08
yep , the problem is that it is listening on 127.0.0.1 , so only localhost can access it.
edit /etc/default/snmpd and delete 127.0.0.1 there

---

