---
title: "configuring multiple network interfaces"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by manu456 on 2007-06-14
Hi all

This question is not specific to Ubuntu but I need some help setting up a complex network configuration. I have a machine running fiesty with two ethernet cards. I have configured them both to different networks. 

eth0 - dynamic ip using DHCP connected to network 1
eth1 - static ip and is configured to use a gateway connected directly to the internet

I want to host a red5 server application on this machine. red5 is a java based server for streaming flash content. To make things simple let's just assume its tomcat.

So I want my tomcat to be accessible from the internet throuhg the static ip (to which eth1 is mapped)

Now the problem that I am facing is that when I try to access tomcat through network1 it works fine but when I try to access it from the internet using the static ip I can't seem to connect to it. Although I can ping the machine and I know its on the internet. 

netstat shows tomcat listening on port 8080. Do i also have to tell it what interface (eth0 or eth1) it should listen on? How do i do that? Or there could be some other problem?

Should I install a firewall and try to configure my open ports through that?

Any help would be appreciated.

Thanks. 
Manu

---

