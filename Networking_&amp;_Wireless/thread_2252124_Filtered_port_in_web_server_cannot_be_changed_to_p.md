---
title: "Filtered port in web server cannot be changed to public access"
date: 2014-11-09
forum: Networking &amp; Wireless
---

### Post by Juan_Perez on 2014-11-09
We want to deploy an application for testing in port 9000. Ideally, it should be open to everybody.
First we open the port with ufw:

```
sudo ufw allow 9000/tcp

sudo ufw status
To                         Action      From
--                         ------      ----
9000/tcp                   ALLOW       Anywhere 
9000/tcp (v6)              ALLOW       Anywhere (v6)

```


But the port still appears as filtered
```

nmap -sA domain -p 9000

Host is up (0.086s latency).
PORT     STATE    SERVICE
9000/tcp filtered cslistener
```

We opened the port directly on iptables.
```

sudo iptables -I INPUT -p tcp --dport 9000 -j ACCEPT

sudo iptables -L -vn
pkts bytes target     prot opt in     out     source        destination         
0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0        0.0.0.0/0     tcp dpt:9000

```

But still appears as filtered.

What could be the problem ? Any help is appreciated.

---

### Post by houstonbofh on 2014-11-09
The firewall is only one part.  What services is listening on 9000, and is it open?

---

### Post by Juan_Perez on 2014-11-09
Hi, thanks for replying.
The service that is listening is tomcat. This is what I have added to the server.xml

```

   <Connector port="9000" protocol="HTTP/1.1"
               connectionTimeout="20000"
               URIEncoding="UTF-8"
               redirectPort="8443" />

```

and the port seems to be open

```

netstat -nap | grep 9000
tcp6       0      0 :::9000                 :::*                    LISTEN  

```

Still, the port is shown as filtered ...

---

### Post by steeldriver on 2014-11-09
is it a case of your service is only listening on the IPv6 interface whereas your nmap command is only probing the IPv4 interface?

---

### Post by Juan_Perez on 2014-11-09
Sorry, I am a newbie in these topics..
Could it be that the port is open in only one interface ?
and tomcat is listening only to the other interface ?

---

### Post by houstonbofh on 2014-11-10
OK, your firewall is allowing it on v4 and v6.  But netstat only shows the server listening on v6.  This means any v4 service would not see it, even though it is open.

---

### Post by Juan_Perez on 2014-11-12
Hi... I finally found the problem... 
My configuration was correct, but there was a second firewall blocking the connections. Once the port was open there everything worked.
Thank you for the help !

---

