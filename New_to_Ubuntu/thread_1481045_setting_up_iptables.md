---
title: "setting up iptables"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by daGeneral on 2010-05-12
Hello all,

im trying to setup iptables and do an upside down ternet trick.

But i cant set any iptables PREROUTE rule; and to begin with my iptables dont have any chains.

when i try the following:
/sbin/iptables -A PREROUTING -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.1

i get an error sayin no matchnig chains found

id appreciate it if anyone can tell me how to do this

cheers

---

### Post by daGeneral on 2010-05-12
anyone?

---

### Post by gmargo on 2010-05-12
Iptables controls several "tables" of chains.  Since your command does not specify a table, it defaults to the "filter" table, which does not contain a PREROUTING chain.  The other tables are "nat", "mangle", "raw", each of which does contain a PREROUTING chain.  Use a -t option to specify the alternate table, like this:
```

iptables -t nat -A PREROUTING -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.1

```

Here are some handy commands to dump each of the tables:
```

iptables -L -nv -t filter
iptables -L -nv -t nat
iptables -L -nv -t mangle
iptables -L -nv -t raw

```

---

### Post by daGeneral on 2010-05-12
cheers m8! that worked

---

