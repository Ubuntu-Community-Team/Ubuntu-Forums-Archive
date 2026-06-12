---
title: "How to access a web server that only has an internal LAN IP from outside?"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-12-15
I have a web server on the DMZ machine and I can access this from outside.
I also have a router (no firewall) behind the DMZ machine (which has firewall) and a desktop ("internal desktop") and a laptop behind that router.

How can I access the webserver that is on that internal desktop?
To make it easy for mself, let's say my domain for the DMZ machine is:
me.com
and say the internal IP for the internal desktop is:
192.168.0.100

I can view [http://me.com](http://me.com), but how can I view the web material on 192.168.0.100?
Thanks!

---

### Post by tak1150 on 2007-12-17
This issue seems so simple that it seems like I should be able to get the answer from Google in a sec. But I haven't found any yet. Anybody?

---

### Post by mpokrywka on 2007-12-18
Depends how exactly your network is configured, but generally you need to configure "port forwarding".

I don't know if I understood your description properly, but if your network looks like this:
```

{ INTERNET }---[Firewall]---+---[DMZ Machine] (public ip address f.e. 69.89.31.**126**)
                            |
                            |  (public ip address f.e. 69.89.31.**127**)
                        [Router]
                            |
                            |
                  [Laptop, desktop] (private ip 192.168.0.100)

```
if your "router" has public ip address, then you need configure it to forward port 80 to internal desktop, and you would be able browse web material via [http://**69.89.31.127](http://**69.89.31.127)**
(ask if you need directions with portforwarding)

If your network is configured like this:
```

{ INTERNET }---[Firewall]---+---[DMZ Machine] (private ip address f.e. 192.168.1.**10**)
                            |
                            |  (private ip address f.e. 192.168.1.**20**)
                        [Router]
                            |
                            |
                  [Laptop, desktop] (private ip 192.168.0.100)

```
then you need double port forwarding, and your internal web content will be available on non standard port: (port numbers may be chosen freely)
on Firewall: portforward port 81 from "internet" -> to 192.168.1.20 : port 81
on Router: portforward port 81 from "outside" -> to 192.168.0.100 : port 80
and you would be able browse web material via [http://**69.89.31.126:81](http://**69.89.31.126:81)**

---

### Post by tak1150 on 2007-12-18
> **mpokrywka said:**
> Depends how exactly your network is configured, but generally you need to configure "port forwarding".

I don't know if I understood your description properly, but if your network looks like this:
```

{ INTERNET }---[Firewall]---+---[DMZ Machine] (public ip address f.e. 69.89.31.**126**)
                            |
                            |  (public ip address f.e. 69.89.31.**127**)
                        [Router]
                            |
                            |
                  [Laptop, desktop] (private ip 192.168.0.100)

```
if your "router" has public ip address, then you need configure it to forward port 80 to internal desktop, and you would be able browse web material via [http://**69.89.31.127](http://**69.89.31.127)**
(ask if you need directions with portforwarding)

If your network is configured like this:
```

{ INTERNET }---[Firewall]---+---[DMZ Machine] (private ip address f.e. 192.168.1.**10**)
                            |
                            |  (private ip address f.e. 192.168.1.**20**)
                        [Router]
                            |
                            |
                  [Laptop, desktop] (private ip 192.168.0.100)

```
then you need double port forwarding, and your internal web content will be available on non standard port: (port numbers may be chosen freely)
on Firewall: portforward port 81 from "internet" -> to 192.168.1.20 : port 81
on Router: portforward port 81 from "outside" -> to 192.168.0.100 : port 80
and you would be able browse web material via [http://**69.89.31.126:81](http://**69.89.31.126:81)**

Thanks for a detailed answer.
Here's what my network looks like:
[IMG]http://taksuyama.com/images/proxy_server_hardware_config.png[/IMG]
The "proxy server" also acts as the firewall. There is no hardware firewall.
I'm using shorewall, so the file to configure is .. policy?
Thanks.

Tak

Edit: I guess it's the "rules" file, but I'm having some problem
I'm trying:
DNAT net loc:192.168.0.110:80 tcp 888
192.168.0.110 is the internal IP of the web server. 888 is the dummy port number (Cox doesn't allow outbound port 80).

---

