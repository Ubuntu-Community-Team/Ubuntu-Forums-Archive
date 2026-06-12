---
title: "Why is Squid blocking the https webmin port 10000"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by lcsfsr1 on 2009-10-07
Hello,
I am using Ubuntu server 9.04.  I have Squid 2.7 installed, Dansguardian 2.9.9.7 installed and Webmin 1.490 installed.
 
Clients workstations are all windows XP Pro using MS Internet Explorer.
 
I have all of my pcs on the proxy.  Everytime, when I go into Webmin (with the client workstation proxy enabled) I get this error:
 
**[SIZE=3]ERROR[/SIZE]**

**[SIZE=3]The requested URL could not be retrieved[/SIZE]**


While trying to retrieve the URL: [10.0.0.37:10000]("http://ubuntuforums.org/10.0.0.37:10000") 
The following error was encountered: 
[LIST]
[*]**Access Denied. **Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect. 
[/LIST]
Your cache administrator is [EMAIL="webmaster"]webmaster[/EMAIL]. 
Generated Wed, 07 Oct 2009 14:15:47 GMT by ctproxy.&^#^&^$^*^&^.com (squid/2.7.STABLE3)  This does not happen if I uncheck the "use proxy setting". What would cause the webmin port to be blocked??? Thanks for the Help, Bobby Howerton

---

### Post by tomBorgia on 2009-10-07
Hi, 

you need to add 10000 to the acl Safe_Ports bit in your squid proxy and restart it.

in /etc/squid/squid.conf under the access control bit (about line 2392)

```
acl Safe_ports port 10000         # Webmin

```

---

### Post by lcsfsr1 on 2009-10-07
Thank you for answering so quickly...
 
I have checked my squid.conf file and as for the ports this is what is shows:
 
( also did another sudo /etc/init.d/squid reload )
 
acl localnet src 10.0.0.0/24 # RFC1918 possible internal network
#
acl SSL_ports port 443 # https
acl SSL_ports port 563 # snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 10000 # Webmin
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl purge method PURGE # Webmin
acl CONNECT method CONNECT
acl shoutcast rep_header X-HTTP09-First-Line ^ICY\s[0-9]
 
With the proxy enabled on a windows workstation... It still does not work. I still get the same Access Denied error.
 
Any other ideas???
 
Thanks Bobby

---

### Post by amolsen on 2010-01-09
A fix that worked for me was to:

 allow CONNECT SSL_port for localnet

---

### Post by eugenevdm on 2010-09-12
I have the same problem but this fix does not work.

On Chrome I get:
Error 111 (net::ERR_TUNNEL_CONNECTION_FAILED): Unknown error.

On Firefox:
The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing connections.

I have port 10002 configured for Webmin. I have also added it as to Safe_ports.

When I add:> allow CONNECT SSL_port for localnet

Squid says:
cache_cf.cc(363) parseOneConfigFile: squid.conf:674 unrecognized: 'allow'

The interesting thing is it's working for Plesk and Plesk Expand, which uses SSL on ports 8443 and 8442.

---

### Post by Vishal Agarwal on 2010-10-02
Hi,
You need to add SSL port, instead of safe port.

```
acl SSL_ports port 10000 # Webmin
```

---

### Post by hgghfnvk on 2011-01-14
> **Vishal Agarwal said:**
> Hi,
You need to add SSL port, instead of safe port.

```
acl SSL_ports port 10000 # Webmin
```

I have the same problem and with this line squid fails to start. I also tried both lines with no luck. Does anybody has a solution?

---

