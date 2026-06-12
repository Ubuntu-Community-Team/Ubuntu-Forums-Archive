---
title: "[SOLVED] Ubuntu 7.04 can't connect surf the internet unless using IP addresses."
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by beep1314 on 2007-07-23
I just did a clean install of Ubuntu 7.04 on an old Toshiba 2595CDT laptop.  I have a Linksys wired router and an Embarq DSL modem.  I connect with DCHP.
I tried to surf the internet (example [www.google.com](www.google.com)) with Firefox but got the "problem loading page" error.  I then used Ping to test my router, modem, and web sites (via IP addresses, www addresses did not work).  All of the pings went through.  
Then I went back into Firefox and tried surfing with IP addresses which worked fine.  
Does anyone have a hint as how to tell Ubuntu that it is ok to use www like the rest of us?

---

### Post by gangolli on 2007-07-23
The Linksys box serves as the DHCP server for your LAN and has to provide the IP addresses of the DNS name servers.  Check the Linksys box to make sure it is configured to provide these properly.

Do you have other machines on the LAN where name resolution is working normally?

As a result of DHCP on the Ubuntu laptop you should have a generated version of the file called /etc/resolv.conf that lists the name servers.  Check to see that it is there and contains the DNS name server IP address(es) that you expect.

---

### Post by beep1314 on 2007-07-23
yes, a Windows XP system.
Where do I find /etc/resolv.conf and what should I expect?
Thanks

---

### Post by gangolli on 2007-07-24
Open a Terminal window (Applications | Accessories | Terminal).  Please post the output of the following few commands to help diagnose this.  Readers may be able to see a clue.

> 
/sbin/ifconfig -a


That should list your interfaces and their currently assigned IP addresses.

> 
cat /etc/resolv.conf


That should list your assigned nameservers.

> 
cat /etc/network/interfaces


That will tell us if you've set up the interface for dhcp

> 
/sbin/route -n


This will show us the routing table.

---

### Post by beep1314 on 2007-07-24
Thank you for your help, I selected DCHP at install but somehow it got lost in the mix.  I dug into network and found that it had been changed to static.  Changed it back and now I can surf the web like a normal person.  YES!

---

