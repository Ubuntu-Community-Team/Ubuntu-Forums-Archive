---
title: "Content filtering - firehol error, Firefox connection"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by TravMan63 on 2007-08-03
I am attempting to setup filtering on 7.04 CE
(I reinstalled dansguardian - which removed the gui -which is fine - however - it worked only on live cd, not on install after applying the system updates)

I have dansguardian, clamav, tinyproxy and firehol installed

I'm having and error with firehol (hoping this and firefox config alone will solve the problem...)

Problem 1:
```
dad@Zach-Ubuntu-laptop:~$ sudo /sbin/firehol restart
Cannot find an executables iptable
```

iptables is installed:
which iptables
/sbin/iptables

----

conf files:

firehol
sudo nano -w /etc/firehol/firehol.conf

```

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport
3128 -m owner ! --uid-owner dansguardian -j DROP


START_FIREHOL=YES
#If you want to have firehol wait for an iface to be up add it here
WAIT_FOR_IFACE=""

# TH 2007-08-03 see log for more url http://www.pilpi.net/journal/item-985.php
transparent_squid 8080 "dad" # from proxy root (ps aux|grep tinyproxy)

interface any world
   policy drop
   protection strong
   client all accept
```

tinyproxy
sudo nano -w /etc/tinyproxy/tinyproxy.conf  
left default execpt for:

```

# 2007-08-03 edited TH (added nobody)

User nobody
Group nogroup
User root
Group root
```

and dansguardian
sudo nano -w /etc/dansguardian/dansguardian.conf 

(the UNCONFIGURED line exists as
#UNCONFIGURED)

--
PART 2:
Firefox - is configured (edit/preferences/advanced/network/settings)
to 'direct connection to internet'
and the box is greyed out.

I ran it with
sudo firefox
(should use -H option)
and it was still greyed out. Can't access the proxy settings...

---
TM

#edit 1 - firehol update --> [ http://ubuntuforums.org/archive/index.php/t-438663.html ]( http://ubuntuforums.org/archive/index.php/t-438663.html )
chmod o+x /lib/firehol/firehol
causes the file to be executeable

before:
 ls -l /lib/firehol/
total 136
-rw-r--r-- 1 dad dad 133251 2007-04-22 01:50 firehol

after:
chmod o+x /lib/firehol/firehol
ls -l /lib/firehol/
total 136
-rw-r--r-x 1 dad dad 133251 2007-04-22 01:50 firehol
----------^

--------- restart it
dad@Zach-Ubuntu-laptop:~$ sudo firehol restart
/etc/default/firehol: line 2: 3128: command not found

output:
```

--------------------------------------------------------------------------------
ERROR #: 1
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8080 nobody root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8080 nobody root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Creating chain 'in_world' under 'INPUT' in table 'filter'
WHY    : Chain 'in_world' already exists.
COMMAND: (unset)
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 3
WHAT   : Creating chain 'pr_world_fragments' under 'in_world' in table 'filter'
WHY    : Chain 'pr_world_fragments' already exists.
COMMAND: protection invalid fragments new-tcp-w/o-syn icmp-floods syn-floods malformed-xmas malformed-null malformed-bad 100/s 50
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 4
WHAT   : Creating chain 'in_world_all_c1' under 'in_world' in table 'filter'
WHY    : Chain 'in_world_all_c1' already exists.
COMMAND: client all accept
SOURCE : line INIT of /etc/firehol/firehol.conf


NOTICE: No changes made to your firewall.
Stopped: Processing file /etc/firehol/firehol.conf.

FireHOL: Restoring old firewall: OK
---------------

```

---

