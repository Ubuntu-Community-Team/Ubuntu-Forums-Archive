---
title: "Hadoop/ Cassandra cluster w/ multiple services on different ports - how to domainname"
date: 2016-02-19
forum: Networking &amp; Wireless
---

### Post by Sebastian93 on 2016-02-19
Hello,

Our company is running a Hadoop/Cassandra cluster. Our main node is currently running services like Hue, Cloud era, Ops center. All accessible via web browser using the server ip and the service's port number. For example:

192.168.1.128:8888 - HUE

The node is also publicly accessible, public IP port forwarded to the the router.

Public IP X.X.X.X to 192.168.1.128:22

Is there a way to have HUE assigned to a web domain for example hue.domain.com. I noticed that you cannot add a port number to An A record on a domain provider. All of these services run on different ports, that's where the problem comes in. 

We would like to have these systems publicly facing which is fine when I port forward the public ip to each port number of service. I can access the service via web broweser by inserting public ip and its port number.

However, we would like for example HUE to be accessed at hue.domain.com. Is this possible?

Thanks in advance.

Sebastian.

---

