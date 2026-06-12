---
title: "Virtual Port Forwarding"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by giroux.oli on 2013-12-23
Hi Guys ! 

First of all , sorry for my english, I'm Québécois (French Canadien)

I using Ubuntu Server for a personal project. I try to start 2 times the same services. It's exactly the same , but different settings. Both use the same port. When I try to start the second one, it's just not working. Error message about the same services is already started in the same port. I can change the port of the second one, but not on the client who using the services. 

So , my question is, ... 

Can I make a redirection of the port with , example the domain name and port to a virtual port ? Same like with Apache and Virtualhost fonction ?

Example : 

I got 2 services, one use the virtual port 1 and the second one on the port 2. And I got 2 domaine name, [www.domaine1.com](www.domaine1.com) and [www.domaine2.com](www.domaine2.com). Both need to pass by the port 9966(example) to reach the services.

So what I need , still on the example, is the domaine name point to the server, the server check which domaine name is using and with which port, and make a redirection of the port to the good one. [www.domaine1.com:9966](www.domaine1.com:9966) to service with port : 1        [www.domaine2.com:9966](www.domaine2.com:9966) to service with port: 2. 

That already existing something like that ? I know I can do that with apache with the port 80 for mutli website one the same server. Can I do that with another software or services ?

thank you in advance.

---

### Post by ian-weisser on 2013-12-26
DNS records, if I recall correctly, do not include a port number. So redirection by domain name won't work.
There is no way that I know of to sub-port a port.

Ports are already virtual - merely an identification system, so the kernel knows which file descriptor the packet should be sent to. If you start using identifications that the kernel doesn't know, you can expect poor results.

- The client can use port-redirection (forwarding) in ssh. [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)

- You can run one or both of the services in an LXC container (or VM), so the service has a different IP address. [http://linuxcontainers.org/](http://linuxcontainers.org/)

- You can prod the developer of your service to make the use case easier. This is an issue with gameservers, for example. Simutrans is one example of a game that will happily bind to any port specified in the config file. Multiple instances can happily coexist on the same server. Clients can connect to any of them.

---

