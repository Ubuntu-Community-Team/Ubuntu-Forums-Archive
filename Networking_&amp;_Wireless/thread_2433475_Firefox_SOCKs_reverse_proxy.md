---
title: "Firefox SOCKs reverse proxy"
date: 2019-12-19
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2019-12-19
Hi All, 

I have a server at work sitting behind a firewall that allows outbound traffic only:

work-server---------> Internet

What i am looking to try and do is SSH from the work-server back to a server at home. From there i am looking to access resources via the work server:

laptop--------home-server----> Internet -------> work-server --------> internal web servers

More detailed:
(laptop 192.168.0.2)-------->(home-server 192.168.0.3)----> (Internet) -------> (work-server 172.31.61.20) --------> (internal web servers 172.31.57.215)

Work and home servers are running Ubuntu server.

In the past i used to use SSH -D as the work-server used to allow inbound ssh however this is no longer the case. 

Can i reverse ssh from work-server to home-server then tunnel web traffic down the tunnel?

Thanks

---

### Post by TheFu on 2019-12-19
Need to speak with the network security team at your work.
172.31.x.x is a private IP, just like 10.x.x.x and 192.168.x.x are.

I have no idea what firefox has to do with this question. Can you please expand on htat?

---

### Post by howefield on 2019-12-19
As said, you're best speaking to the relevant administrator.

Thread closed.

---

