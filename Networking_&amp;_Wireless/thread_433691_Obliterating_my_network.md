---
title: "Obliterating my network"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by DarkHorizon on 2007-05-05
Hi all,

Previously I had an Ubuntu Edgy server between my desktop computers and the internet. It served HTTP, SSH, and FTP to all, as well as Samba to my desktops.

Recently I decided I wanted to add wireless to my network. Not having a lot of time for twiddling, I decided to go the cheap and easy route, and picked up a D-Link WBR-1310. I've put all computers behind it, including my server.

Now I'm trying to get the services it previously ran, once again serving the internet.

I've port-forwarded 20-22 and 80 in the router config, and from the internet all seems to be working fine. However, I am unable to touch the HTTP server (Apache 2) from within the network, unless I use the IP address of the host. And of course, using IP addressing, I am unable to view any additional sites I've set up for the various .com's I've registered and configured, only the default one.

I've gone so far as to try dumbing my firewall down as such:

```
iptables --flush
iptables -t nat --flush
iptables -t mangle --flush
iptables --policy INPUT ACCEPT
iptables --policy OUTPUT ACCEPT
```

But this does nothing.

Hitting any domains I've configured results in a timeout.

The HTTP access and error logs don't show any activity from the desktop computer from which I am attempting to access the server's HTTP daemon.

Any suggestions? Is the router I bought a lemon?

---

### Post by lamadredelsapo on 2007-05-05
So your new configuration is:

1. Router connected to the Internet.
2. Your server and desktops connected to your router to have internet access.

and your previous was

1. Server connected to the Internet
2. Desktops connected to Internet through your server?

I'm not sure, but it might be a problem with NAT (Network Address Translation)

---

### Post by DarkHorizon on 2007-05-05
Nope...

- desktops see internet and each other
- server sees internet and desktops
- desktops get timeout when accessing server's apache via domain names, but get default page when accessing apache by server's ip address
- server logs (error.log and access.log) don't show activity from desktop when apache is hit from inside the network
- computers can access the server (via port forwarding) from the internet to the server

Ideas?

---

### Post by lamadredelsapo on 2007-05-06
You should add to your httpd.conf file VirtualHosts for the local ip of the server, just the same I think you did with your public ip. That will solve the problem, (or at list I think so).

Imagine your server ip is 192.168.1.2 and your external ip is 123.234.111.222, you actually have:

```
<VirtualHost 123.234.111.222:80>
  ServerName myserver.mydomain.com
  DocumentRoot /www/myserver/
 </VirtualHost>
```

you should add

```
<VirtualHost 192.168.1.2:80>
  ServerName myserver.mydomain.com
  DocumentRoot /www/myserver/
 </VirtualHost>
```

Repeat the process for every domain you have and restart apache.

And to manage iptables you should take a look at firestarter, it's a graphical front end for iptables very easy to use.

---

