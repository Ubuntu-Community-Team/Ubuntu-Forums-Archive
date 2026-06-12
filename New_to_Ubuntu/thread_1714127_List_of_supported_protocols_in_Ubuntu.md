---
title: "List of supported protocols in Ubuntu"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by SteelCore on 2011-03-24
In a networking lecture I took to today, it was mentioned that Windows has a file WINDOWS/system32/drivers/etc/services that has a list of all the supported protocols (and their port numbers) on the machine. Is there a similar file in Ubuntu?
Thanks

---

### Post by alphacrucis2 on 2011-03-25
> **SteelCore said:**
> In a networking lecture I took to today, it was mentioned that Windows has a file WINDOWS/system32/drivers/etc/services that has a list of all the supported protocols (and their port numbers) on the machine. Is there a similar file in Ubuntu?
Thanks

If you want to know what tcp and udp ports are listening on a linux box, you can use the following command:

```
netstat -anp --tcp --udp | grep LISTEN

```

---

### Post by SeijiSensei on 2011-03-25
> **SteelCore said:**
> In a networking lecture I took to today, it was mentioned that Windows has a file WINDOWS/system32/drivers/etc/services that has a list of all the supported protocols (and their port numbers) on the machine. Is there a similar file in Ubuntu?
Thanks

Sure.  It's /etc/services.  As I recall most of the other files in Windows drivers/etc/ directory like the [hosts]("http://en.wikipedia.org/wiki/Hosts_%28file%29#Location_in_the_file_system") file have equivalents in /etc on Linux.

However it's not accurate to say it's a list of services *supported* by Ubuntu.  /etc/services simply includes all the "official" services that have been assigned port numbers by the [Internet Assigned Numbers Authority]("http://www.iana.org/").  To "support" a service requires software that listens on the assigned port and accepts requests that conform to the protocol that service employs.  

For instance, the [Simple Mail Transport Protoco]("http://tools.ietf.org/html/rfc2821")l has been assigned port 25.  If you run an SMTP server like Postfix or sendmail, it will listen on port 25 waiting for clients to connect and transfer a message using the protocol as defined in RFC2821 to which I linked.  

The program nmap will scan a machine and identify which, if any, ports are "open" and offering a service.  For instance, if you scanned my public server, you'd see something like this:

Nmap scan report for smtp.example.com
Host is up (0.012s latency).
Not shown: 992 filtered ports
PORT     STATE  SERVICE
25/tcp   open   smtp
80/tcp   open   http
110/tcp  open   pop3
143/tcp  open   imap

That shows my server is listening on four ports to provide the services in the list above.  

nmap actually uses its own services file (usually /usr/share/nmap/nmap-services) which includes entries for many known trojans and other possible exploits like this one:

```
bo2k    14141/tcp       0.000038        # Back Orifice 2K BoPeep mouse/keyboard input
```

"[BackOrifice]("http://en.wikipedia.org/wiki/Back_Orifice")" is an infamous Windows trojan that by convention of its developers listens on TCP port 14141.

---

