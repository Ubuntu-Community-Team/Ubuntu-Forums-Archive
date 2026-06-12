---
title: "Error accessing service from remote computer (Openstack Swift)"
date: 2014-11-20
forum: Networking &amp; Wireless
---

### Post by Fasterfox06 on 2014-11-20
Hi,
 I have running an Openstack Swift testing environment running on  Ubuntu 14.04, I'm able to create containers, upload files, etc, using the  default internal address 127.0.0.1:8080. My problem is that I'm not able  to get access to it from an external client, for example from another  computer, using the external IP address is for example: 192.1.1.10.

 The error is:

 HTTPConnectionPool(host='192.1.1.10',  port=8080): Max retries exceeded with url: /auth/v1.0 (Caused by  <class 'socket.error'="">: [Errno 111] Connection refused)

 I think is a problem of a network configuration, how can I open/expose that port to be visible externally.

 
I also have installed Apache on the default port 80 and it works fine.

The Ubuntu firewall UFW is disabled.

Thanks for your help.

---

