---
title: "Problems with snmpwalk"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by Hlio_Calaa_Fil on 2014-03-20
Hello folks!

I'm getting bored with my snmpwalk.
When I use snmpwalk in my Ubuntu it works well and it shows MIB data as well, but it shows information in OID numeric form as it default output (as we can see below).

> root@test1:/root# snmpwalk -v 2c -c public 10.1.10.110
iso.3.6.1.2.1.1.1.0 = STRING: "Cisco IOS Software, 1841 Software  (C1841-SPSERVICESK9-M), Version 12.4(23a), RELEASE SOFTWARE (fc11)
Technical Support: [http://www.cisco.com/techsupport](http://www.cisco.com/techsupport)
Copyright (c) 1986-2009 by Cisco Systems, Inc.
Compiled Wed 03-Jun-09 13:23 by prod_rel_team"
iso.3.6.1.2.1.1.2.0 = OID: iso.3.6.1.4.1.9.1.620
iso.3.6.1.2.1.1.3.0 = Timeticks: (20596115) 2 days, 9:12:41.15
iso.3.6.1.2.1.1.4.0 = ""
iso.3.6.1.2.1.1.5.0 = STRING: "SW"
iso.3.6.1.2.1.1.6.0 = ""
iso.3.6.1.2.1.1.7.0 = INTEGER: 78
iso.3.6.1.2.1.1.8.0 = Timeticks: (0) 0:00:00.00
iso.3.6.1.2.1.1.9.1.2.1 = OID: iso.3.6.1.4.1.9.7.129
iso.3.6.1.2.1.1.9.1.2.2 = OID: iso.3.6.1.4.1.9.7.115
iso.3.6.1.2.1.1.9.1.2.3 = OID: iso.3.6.1.4.1.9.7.265
iso.3.6.1.2.1.1.9.1.2.4 = OID: iso.3.6.1.4.1.9.7.112
iso.3.6.1.2.1.1.9.1.2.5 = OID: iso.3.6.1.4.1.9.7.106
iso.3.6.1.2.1.1.9.1.2.6 = OID: iso.3.6.1.4.1.9.7.47
iso.3.6.1.2.1.1.9.1.2.7 = OID: iso.3.6.1.4.1.9.7.122
iso.3.6.1.2.1.1.9.1.2.8 = OID: iso.3.6.1.4.1.9.7.135
iso.3.6.1.2.1.1.9.1.2.9 = OID: iso.3.6.1.4.1.9.7.43

And I need to get those infos in textual or named form like below.

> root@test1:/root# snmpwalk -v 2c -c public 10.1.10.110
iso.3.6.1.2.1.1.1.0 = STRING: "Cisco IOS Software, 1841 Software  (C1841-SPSERVICESK9-M), Version 12.4(23a), RELEASE SOFTWARE (fc11)
Technical Support: [http://www.cisco.com/techsupport](http://www.cisco.com/techsupport)
Copyright (c) 1986-2009 by Cisco Systems, Inc.
Compiled Wed 03-Jun-09 13:23 by prod_rel_team"
Cannot find module (LM-SENSORS-MIB): At line 0 in (none)
Cannot find module (NET-SNMP-EXTEND-MIB): At line 0 in (none)
SNMPv2-MIB::sysDescr.0 = STRING: Cisco IOS Software, 1841 Software  (C1841-SPSERVICESK9-M), Version 12.4(23a), RELEASE SOFTWARE (fc11)
Technical Support: [http://www.cisco.com/techsupport](http://www.cisco.com/techsupport)
Copyright (c) 1986-2009 by Cisco Systems, Inc.
Compiled Wed 03-Jun-09 13:23 by prod_rel_team
SNMPv2-MIB::sysObjectID.0 = OID: SNMPv2-SMI::enterprises.9.1.620
SNMPv2-MIB::sysUpTime.0 = Timeticks: (20612424) 2 days, 9:15:24.24
SNMPv2-MIB::sysContact.0 = STRING:
SNMPv2-MIB::sysName.0 = STRING: SW
SNMPv2-MIB::sysLocation.0 = STRING:
SNMPv2-MIB::sysServices.0 = INTEGER: 78
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORID.1 = OID: SNMPv2-SMI::enterprises.9.7.129
SNMPv2-MIB::sysORID.2 = OID: SNMPv2-SMI::enterprises.9.7.115
SNMPv2-MIB::sysORID.3 = OID: SNMPv2-SMI::enterprises.9.7.265
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-SMI::enterprises.9.7.112
SNMPv2-MIB::sysORID.5 = OID: SNMPv2-SMI::enterprises.9.7.106
SNMPv2-MIB::sysORID.6 = OID: SNMPv2-SMI::enterprises.9.7.47
SNMPv2-MIB::sysORID.7 = OID: SNMPv2-SMI::enterprises.9.7.122
SNMPv2-MIB::sysORID.8 = OID: SNMPv2-SMI::enterprises.9.7.135
SNMPv2-MIB::sysORID.9 = OID: SNMPv2-SMI::enterprises.9.7.43
...

How can I fix this?
Tnx to all!

---

### Post by undefine2 on 2014-04-01
hi. try:
export MIBS=+UCD-SNMP-MIB
before using snmpget/snmpwalk
or add  -m +UCD-SNMP-MIB to commandline

---

