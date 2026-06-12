---
title: "Problem with SNMP in Ubuntu 12.04.2 - snmpwalk and nagios check_snmp"
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by creyes76 on 2014-01-10
Hello..

I currently have this server configured. I have installed the cacti and is currently working monitoring several routers and switches cisco. Now I installed Nagios on the same server, everything works fine except the Check_snmp command. I start validating the configuration of the server, and it seems that is a problem with the SNMP module in the server, although what I don´t really understand why cacti works with the snmp and Nagios don´t.

Usually when i configured this before I used the command snmpwalk to validate that the connection to the routers via snmp was working correctly, at this moment when I execute the command I get the following error.

**sudo snmpwalk -c S******** -v 1 129.39.82.145**
**Timeout: No Response from 129.39.82.145**

I already checkout the network and is not a firewall problem, or router problem, or community problem, as I'm already monitoring the same devices with another server.

Because of the previous problem when I try to execute the check_snmp command from nagios I get the following error.

[B]/usr/local/nagios/libexec$ sudo ./check_snmp -H 129.39.82.145 -o sysUpTime.0
External command error: Timeout: No Response from 129.39.82.145:161

[/B]I already upgraded the SNMP software, and I currently have installed a new version after following all of the steps in the configuration file.

[B]sudo snmpget --version
NET-SNMP version: 5.7.2
[/B]

Any help will be greatly appreciated.

Thanks.

---

