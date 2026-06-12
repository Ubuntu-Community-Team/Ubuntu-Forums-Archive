---
title: "tcp port opening with netcat"
date: 2014-05-05
forum: Networking &amp; Wireless
---

### Post by ubu_lin on 2014-05-05
Hello everybody. I am trying to open a tcp port on ubuntu 12.04, but without success yet, any help is appreciated. Here is what I am doing.

Using netcat, I set a port to listen

netcat -l 1234

Now to test that port, I opened another terminal instance, and used telnet with internal ip address like this, and it connected.

Vostro-1450:~$ telnet 192.168.1.3 1234
Trying 192.168.1.3...
Connected to 192.168.1.3.
Escape character is '^]'.

But when I use my external Ip address, it is not working. It says connection refused.

Vostro-1450:~$ telnet <external ip> 1234
Trying <external ip>...
telnet: Unable to connect to remote host: Connection refused

I have setup port forward in my router.
start port: 1234
end port: 1234
service: tcp
ip: 192.168.1.3

these services are enabled in my router.
LAN: ftp, http, icmp, snmp, telnet, tftp
WAN: icmp, snmp, telnet.

I have also used nmap for port scanning, it doesnt shows when I use external ip address. What I am doing wrong here ?

---

### Post by steeldriver on 2014-05-05
Not all routers support 'NAT loopback' (aka 'hairpinning') back to the same LAN - maybe that's the issue here? Can you try it from a separate external network (e.g. a cell phone)?

[URL="http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback"]http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback
[/URL]

---

### Post by ubu_lin on 2014-05-05
Thank you for quick reply. I don't have saparate external network device currently. But one thing I have noticed, when I used online services to check open ports, it says port is open. So may be you are right. I will try that tomorrow and let you know. Thanks

---

