---
title: "Problem! No switching to secondary DNS when DJBDns as primary is dow"
date: 2017-06-22
forum: Networking &amp; Wireless
---

### Post by cecuevas on 2017-06-22
Hi everyone.


First of all, sorry for my poor english. I'm a beginner.


Currently in my job I've a DNS (DJBDNs based) to answer queries for my local domain (eg: dunno.net). Besides I've a Fortinet Fortigate 1000C acting as a firewall and as secondary DNS. Both servers have the same number of local records (mainly 'A' records). My DHCP sends the DNS using DJBDns as primary DNS server and Fortigate as secondary DNS. 


The problem comes when for some reason my primary DNS suffers an outage and it's showtime for secondary DNS... But it doesn't work. When a client tries to reach both local or external domain name, is trying to reach the primary DNS instead secondary. 


I've read some pages describing similar troubles and the reasons: many pages describes it as a problem with the client (Windows, Linux, etc) and their timeouts. Some given solutions is reseting manually these timeouts but it is not practical.


Is there a solid answer for this? Without editing client by client or modifying the DHCP server configuration.


Using the DNS separately (i.e. setting statically the IP of primary or secondary DNS in my interface settings) they work fine.


Please buddies, help me.


Thanks in advance .

---

### Post by SeijiSensei on 2017-06-23
Windows is especially bad in these situations because it caches DNS entries and won't "forget" them unless you issue an "ipconfig /flushdns" command at the Windows command prompt or reboot.

I presume both the primary and secondary have NS records for both servers, and that both servers are registered through your DNS registrar.  Am I correct?

Beyond that, I'm not sure I can be much help.  I only use ISC BIND and always thought DJB was rather a self-important blowhard.

---

