---
title: "SSHD problems"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by ankh2054 on 2007-04-24
Hi,

I installed my ubuntu server @ home with ip 192.168.1.10, connected to the LAN port of a netgear firewall (192.168.1.1) with port forwarding enabled for SSH (port 22, TCP and UDP).
I could log on via SSH over the internet fine.

I then moved my server to work, and put it behind a new linksys firerwall (192.168.1.1), again with port forwading enabled for port 22 (tcp/udp). 

I have port forwarding setup for http, ftp , and webimn, and they all work fine, but not SSH.

When  I try to connect I get the following error:


When I do a port scan , I can see the port is open.

What I have done so far is:

1. I have deleted all /etc/ssh/ssh_host*  and restarted the SSH server.
2. Restart SSHD daemon

Im not guru so I have no idea where to start to be honest, apart what I can get of google.

I would really aprreciate the help,

thanks

Charles

---

### Post by Jussi Kukkonen on 2007-04-24
You forgot the connection error message.

---

### Post by ankh2054 on 2007-04-25
oops,
Read from socket failed: Connection reset by peer

---

### Post by netztier on 2007-04-25
> **ankh2054 said:**
> oops,
Read from socket failed: Connection reset by peer

Some routers require that you configure firewall rules separately from port-forwarding settings. So the firewall has to allow incoming tcp/22 in the first place; port-forwarding rules are checked *after* an incoming packet has passed the firewall rules.

I used to have a Linksys WAG-54G a while back, and AFAICR, it was one of them that needed configuration in two separate places. My current router is another brand (ZyXEL), and it's the same there.

best regards

Marc

---

### Post by ankh2054 on 2007-05-02
Hi,

I took the firewall out out of the picture completely, and just connected the linux box to a hub, and my laptop to the same hub, using the same addresses as before.

Still getting the error.

any ideas

---

### Post by netztier on 2007-05-02
> **ankh2054 said:**
> Hi,
I took the firewall out out of the picture completely, and just connected the linux box to a hub, and my laptop to the same hub, using the same addresses as before.

Still getting the error.


Try **sudo netstat -napt** and see if port 22 has state "LISTEN" to see if the sshd has actually opened a port. If not, check if the ListenAddress option in **/etc/ssh/sshd_conf** tries to configure the daemon to bind to some specific (nonexisting?) IP address.

You're sure that there's no firestarter, iptables or netfilter (read: a local firewall) running on the machine itself?

best regards

Marc

---

### Post by ankh2054 on 2007-05-16
ahhh thanks for help !!

I did the netstat - napt , and I could a error aboyut the hostname, because I recently did a hostname change oin the box by using the hostname command. I did however did not update the /etc/hosts adding the 127.0.0.1 for the new hostname.

I appreciate the help :)

cheers

---

