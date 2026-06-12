---
title: "Syslog issue"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by adimenia on 2008-05-29
Hello 

im trying to use syslog to relay messages from network devices such as juniper ssg and fortinet firewall and im having this odd problem
when writing the logs locally everything get written both local events and device events (juniper fortinet) now when im configuring the syslog server to relay the messages to a seim system 
(*.debug               @ipaddress ) where the ip address is my seim system i only receive the local Linux events of the syslog server all the events from my juniper and fortinet are gone nothing from those devices gets relayed i used tcpdump (my syslog machine has only one NIC) and i cant see the events coming to my syslog server 
if i change back the configuration of the syslog server to write the logs locally (*.debug         /var/log/all.log) everything gets written to the log file including the events from my juniper and fortinet i dont know what to do if anyone has ANY idea ill be most thankful:)

---

