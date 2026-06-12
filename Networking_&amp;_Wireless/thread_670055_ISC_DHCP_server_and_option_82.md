---
title: "ISC DHCP server and option 82"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Asmodision on 2008-01-17
Hi!

Trying to enable option82 in our DHCP server but can't find where. I've added this into my dhcpd.conf file:

   [I]     if exists agent.circuit-id {
                log ( info , concat( "Lease for " , binary-to-ascii
                (10 , 8 , "." , leased-address) , " is connected to interface " ,
                binary-to-ascii (10 , 8 , "/" , suffix ( option agent.circuit-id , 2)) ,
                " (add 1 to port number!), VLAN " , binary-to-ascii (10 , 16 , "" ,
                substring( option agent.circuit-id , 2 , 2)) , " on switch " ,
                binary-to-ascii(16 , 8 , ":" , substring( option agent.remote-id , 2 , 6))));
                log ( info , concat( "Lease for " , binary-to-ascii (10 , 8 , "." , leased-address)
                , " raw option-82 info is CID: " , binary-to-ascii (10 , 8 , "." ,
                option agent.circuit-id) , " AID: " , binary-to-ascii(16 , 8 , "." , option agent.remote-id)));
                }[/I]

But I can't see anything in the syslog. Is there anywhere else I've need to "enable" option82?
Another small question is now do I look and IP to an circuit-id field?

---

