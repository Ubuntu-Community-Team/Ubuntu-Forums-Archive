---
title: "Unable to Access Remotely"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by igodspeed on 2015-11-28
Hi,

We have a few computers which we are using at our office, our problem is that we are not able to access (FTP, Remote Desktop or SSH). The I think is probably is that there is an ADSL modem which is then connected to our router then our computer. Our ADSL modem has an IP address of 192.168.1.1, the router  which is connected to the modem has an IP address 192.168.2.XXX(This change was made in the router itself). The guy who came to install it told someone at our office that this is so that there is no IP conflict. 

I am not sure why we are not able to access our computers from outside internet, we can use all these features if we use local IPs. Please let me know if there is something that i elaborate on and please do help us.

Thanks.

---

### Post by Lars Noodén on 2015-11-28
Have you set up the router and modem to forward the SSH port from its external address not 192.168.x.x?  The router has an external address and you need to connect to that external address.  Before you can use that external address for SSH + SFTP, you need to set up port forwarding so that an external port on the external address is forwarded to the right port (22) on the right machine.

---

### Post by igodspeed on 2015-11-28
I have been experimenting with port forwarding but did not work, i think it may be because ADSL modem is 192.168.1.x and wireless router is 192.168.2.x.

I have attached to this email 3 pictures
[LIST]
[*]Screenshot of IP Address of linksys router
[*]Screenshot of IP Address of ADSL router
[*]Screenshot of Port forwarding in Linksys Router
[/LIST]

Have i configured port forwarding correctly? I wonder since, the local ipaddress are 192.168.1.xxx and 192.168.2.xxx. Would that cause the problem?

Thanks

---

### Post by Lars Noodén on 2015-11-29
What is the relationship there between the two routers?  Which one is actually connected to the outside and why do you have the second one?

---

