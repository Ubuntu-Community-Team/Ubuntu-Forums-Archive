---
title: "snmpd access control issues on Feisty"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by Ysbeer on 2007-06-27
Hi there,

I did an apt-get install of snmpd and snmp on a Feisty box. I have read up quite a bit to get a basic "read only" community configuration up and running. Even used just the basic "snmpconf -basic" script. However, as much as  I like I can only do a "snmpwalk" or "snmpget" query to "localhost" on the box itself. This defeats the purpose for me. I want to be able to monitor the memopry and cpu use using MRTG from another box on the same network. When I copy the snmpd.conf file to a Dapper box it works fine and I can retrieve snmp info remotely. But it refuses on Feisty. Connection timed out. On Feisty AND Dapper I am running NET-SNMP version:  5.2.3. 
What is configured, and where, in Feisty that will prevent remote snmp queries. I am at wit's end here... Any assistance will be much appreciated.

Regards,

snmpd.conf contents below: (Commented lines excluded)

com2sec readonly  default  mycommunity

group MyROSystem v1        paranoid
group MyROSystem v2c       paranoid
group MyROSystem usm       paranoid
group MyROGroup v1         readonly
group MyROGroup v2c        readonly
group MyROGroup usm        readonly
group MyRWGroup v1         readwrite
group MyRWGroup v2c        readwrite
group MyRWGroup usm        readwrite

view all    included  .1                               80
view system included  .iso.org.dod.internet.mgmt.mib-2.system

access MyROSystem ""     any       noauth    exact  system none   none
access MyROGroup ""      any       noauth    exact  all    none   none
access MyRWGroup ""      any       noauth    exact  all    all    none

syslocation Unknown (configure /etc/snmp/snmpd.local.conf)
syscontact Root <root@localhost> (configure /etc/snmp/snmpd.local.conf)

---

### Post by Stransky on 2007-06-28
I've been experiencing the same issue as well.  Currently, my search leads me to a file /etc/default/snmpd that is loaded by init.d/snmpd script.  By default the default/snmpd file has options in it that limit it to 127.0.0.1 interface.  Removing 127.0.0.1 should cause snmpd to listen on all interfaces on port 161.

I've tried this and snmpd is indeed listening on port 161 (test using 'sudo lsof -i').  My issue is that I am still unable to use snmpwalk to get data out of my machine.

I'm sorry that I don't have a solution for you but, maybe sharing this information will help the both of us.

--Tyler Stransky

---

### Post by aynema on 2008-01-03
I've been having the same problem but I seem to have fixed it now by removing that 127.0.0.1 bind in 
/etc/default/snmpd

If your still having problems make sure your snmd.conf is correctly setup
I setup mine up the same way as my gentoo server so my snmd.conf looks like this

```
com2sec local     127.0.0.1/32    public
com2sec local     10.1.1.0/24   public

group MyROGroup v1         local
group MyROGroup v2c        local
group MyROGroup usm        local

view all    included  .1                               80

access MyROGroup ""      any       noauth    exact  all    none   none

syslocation Boardroom
syscontact Contact@email.address.com
```

---

### Post by coljuaug on 2008-04-18
Aynema,
Thanks a lot.
i also didn't get what was causing the issue, but i used your config, modified based on my settings and voila.

thx again.

---

