---
title: "Ubuntu client NOT Auto re-registering with Infoblox DNS server"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by shehjad.sayyed on 2016-11-14
I have Ubuntu 12.04 (Precise) client which gets it's IP from an  Infoblox DHCP server. This Infoblox grid also acts as our DNS server  (Secondary Zone for the domain abc.xyz)
  When its rebooted it's DNS entry gets registered with DNS. The DHCP lease time is 4 hours & the IP also gets renewed within 2 hours. However, the DNS record is never updated & after 7 days it is auto-scavenged.

  Question: Does Ubuntu have some DNS client which should periodically  update the DNS record just like the DHCP client or It should be the DHCP  server which should update the DNS record of the client?


  Windows has a DNS setting "Register this connection's addresses in  DNS" with a DNS client which periodically updates it's DNS record.

  [https://technet.microsoft.com/en-us/library/cc754143(v=ws.11).aspx]("https://technet.microsoft.com/en-us/library/cc754143%28v=ws.11%29.aspx")

  
Does Ubuntu has something similar which periodically updates DNS server with it's A record?

  
Thank you.

---

