---
title: "Setting up a DNS server?"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by SmoothRunnings on 2008-07-15
I am a newbie when it comes to linux. I work full-time from the Windows 2003 Server environment and need to understand how to setup a DNS server on Ubuntu so that users connected to the LAN can resolve local machines as well as IP's out on the internet. 

In the windows environment the DNS server is setup with an IP address such as 192.168.1.2, subnet mask, gateway, the primary dns server IP points back to the server itself either with it's own IP or the local host IP. The server DNS server itself has forward zone, reverse lookup and forwarders. It does not require a ns1.xxxx.com record.

I am not sure how to configure the DNS server on Ubuntu using a .local domain so that at the end of the day if I ping server1.domain.local or just server1 the DNS server replies back with the IP of server1, and if I ping [www.microsoft.com](www.microsoft.com) it replies back with the internet IP of microsoft, either on the DNS server itself or on any worksation I connect to the same LAN as the DNS server adding the servers IP into the primary DNS server window.

Is there a tutorial for fo this?

Thanks
Andrew

---

