---
title: "2 networks / 2 domains / 2 NIC"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by mrebus on 2008-03-20
Ok I if this has been asked before a link will do just Fine.

First My Networks Layout

====================================== > this is the "business" line
...........|....................................|..................................|
File and Mail Servers......The new Ubuntu box (UB)......domain controler (DCS) for SCADA
Business Domain(BD)....will be transfering files.........only really a dns/wins
...................................to file servers from SCADA..........|
...................................computers.................................|
............................................|......................................|
++++++++++++++++++++++++++++++++++++++++ > The Scada Network     
............|................................|......................................|
........................Lots of computers.

Notes
The BD is secure (ie i am not IT and don't want to get them involved) and I don't need to be a member to access the internet or the the File servers.  Which is all I want to do.  I managed to get connected to the internet and the file server when I only had one NIC.  I did this by just adding the DNS servers, DHCP and the domain name in the NetworkManager GUI.

Now I want to be able to connect to the scada network through another NIC.  I would like to connect to the DNS server on the DCS.  both networks have different subnets are gateways.

how might I get this done.  we do have a few other servers that have dual NICs too.

Thanks

---

