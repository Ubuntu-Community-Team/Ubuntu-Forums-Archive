---
title: "??? Network works but the internet wont"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Nexusens on 2007-08-07
I have finaly convinced my boss to migrate to ubuntu 7.04 from windows. Our network is routed through a watchgaurd firebox using a static IP, I can connect to the server through RDP however I cannot connect to the internet. Below info has been *** for security reasons.

Network Settings
    General
        Host Name : front.desk
        Domain Name :
    DNS
        **.**.***.**
        **.**.***.**
Connection Settings
    IP address
        **.*.*.**
    Subnet
        ***.***.***.*
    Gateway
        **.*.*.*

I can see no reson that I cannot connect to the internet, however I am new to ubuntu and I have never set up a linux box to a secure network before. If anyone can help it would be apreciated.

---

### Post by mips on 2007-08-07
> **Nexusens said:**
> Below info has been *** for security reasons.

Network Settings
    General
        Host Name : front.desk
        Domain Name :
    DNS
        **.**.***.**
        **.**.***.**
Connection Settings
    IP address
        **.*.*.**
    Subnet
        ***.***.***.*
    Gateway
        **.*.*.*

I can see no reson that I cannot connect to the internet, however I am new to ubuntu and I have never set up a linux box to a secure network before. If anyone can help it would be apreciated.


Lol, you might as well have left that out...

Do you connect to the firewall via a proxy ?

Check your dns settings and disable ipv6 is all I can tell you with what you provided.

---

### Post by Nexusens on 2007-08-07
I dont connect through a proxy directly to the firewall. I have disabled ipv6 and I have triple checked that my addresses are correct

---

### Post by nodows on 2007-08-07
Kinda hard to even think about diagnosing with what you gave us but...

i guess u could go through the basics again...

/etc/resolv.conf
scratch that... maybe you could uncomment just the last
couple (or few) octets of your configuration for us... then we still would
be in the dark but it might give us an idea if you have a CIDR/
netmask issues or gateway issues.

---

### Post by Nexusens on 2007-08-08
sorry about that my boss is obsessed with security and was looking over my shoulder when I posted.
DNS
64.59.168.13
64.59.168.15
IP address
10.0.0.10
Subnet
255.255.255.0
Gateway
10.0.0.1

---

### Post by mips on 2007-08-08
Those IPs are private IPs so no real security risk, everybody and their dog uses 10. or 192.168. internally.

Can you ping 10.0.0.1 ?
Show me the output of **traceroute 208.67.216.230**

---

### Post by Nexusens on 2007-08-08
yes I can ping 10.0.0.1
the traceroute output is as follows
*1 send failed*

---

### Post by Nexusens on 2007-08-09
Arrgg !!! well I have solved the problem. I had the host name set to "front.desk", upon changing this to "frontdesk" everything works. Now to my limited networking knowledge (entirely windows based I might add) this shouldn't make a difference could anyone explain it for me. By the way thanks for the previous effort.

---

