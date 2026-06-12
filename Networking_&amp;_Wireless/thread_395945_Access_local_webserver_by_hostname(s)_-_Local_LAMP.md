---
title: "Access local webserver by hostname(s) - Local LAMP, DHCP server"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by p.herewini on 2007-03-28
Hello all,

I have successfully setup the following network:

Multiple Windows XP and Mac clients
1 Ubuntu Samba server (also running Webmin) (Ubuntu Server _DapperDrake_)
1 Ubuntu Samba, LAMP, DHCP server (also running Webmin) (Ubuntu Server _DapperDrake_)
1 router/gateway (Dynamically being assigned DNS server)

All clients accessing Samba servers via hostnames. 
All clients accessing LAMP server via IPAddress ONLY.
All clients being leased network settings by DHCP server.

**The only thing I'm having trouble with is accessing the LAMP server by the hostname**. I thought by setting this server to be the DHCP server too, may resolve this (I just crossed by fingers and blindly hoped), but it obviously didn't.

I also want to be able to easily setup local virtual hosts  e.g.
cynosure.local
foobar.local
phpmyadmin.local

I attempted to setup a local DNS server but stopped to consult this forum before continuing as all the config for the DNS server was foreign to me.

How I thought it would work would be to setup BIND DNS service on my LAMP server. When a local machine sends an http request the local LAMP server would check if the host matched a list of local hosts, if not forward the request to the router DNS's ???

Thanks in advance for any help...

Paulus

---

### Post by Mr. C. on 2007-03-28
Add entries to /etc/hosts or c:\windows\system32\drivers\etc\hosts for now, until you decide to setup your DNS server.  Assuming your server's IP is 192.168.0.10, hosts additions will be:
```

192.168.0.10  cynosure.local
192.168.0.10  foobar.local
192.168.0.10  phpmyadmin.local
```

For each virtual host, add another entry to your hosts file (or mutliple names - aliases - to a single entry).

DHCP does not provide name translation.  It can only help provide DNS server IP addresses.

If you do decided to setup a DNS server, and the server is always available, then change your DHCP server to assign your DNS server's address, instead of your ISP's.  Your DNS server's /etc/resolv.conf will contain itself as a nameserver (eg. nameserver 192.168.0.10). Your server will be a fine caching DNS server, and be authoritative for your LAN hosts.

Here's a little DNS overview, week 8 and 9 notes, homework, and lab

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by kwiki on 2007-03-28
Your problem can be solve by setting up a local DNS server..  If [www.foo.com](www.foo.com) is configured to your DNS server pointing to LAMP server. That way your client pc's don't have to put the ip address of your LAMP server to your internet browser.

---

### Post by p.herewini on 2007-03-29
**RESOLVED!**

Thanks to those you gave advice. I did attempt to setup a BIND DNS server and I can now access my local webserver at:

cynosure.local
OR [www.cynosure.local](www.cynosure.local)
OR foobar.cynosure.local

BUT any external request will correct go out to the world e.g.
[www.cynosure.co.nz](www.cynosure.co.nz)
OR [www.google.com](www.google.com)

-- HOW? --

For anyone out there in the same predicament I was in may find the following useful: 
[LIST=1]
[*]I installed BIND DNS, then attempted to configure it using Webmin but found the interface much too involved for a n00b
[*]I found this tutorial on configuring a local (LAN) DNS server: [http://www.cameratim.com/computing/linux/using-bind-as-a-local-dns-server#aiming-for](http://www.cameratim.com/computing/linux/using-bind-as-a-local-dns-server#aiming-for)
[*]I used Webmin, but only the unrecommended "Edit config file" sections, as I could simply copy and paste from the tutorial
[*] NOTE: make sure you restart the server before testing any changes made, or if you know what your doing you can restart the required services
[/LIST]

---

