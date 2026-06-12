---
title: "telnetd problem"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by captainiom on 2010-11-14
I have been quietly evaluating UBUNTU since getting help from this forum during installation.  I am more familiar now and am starting to install and test various applications.  One of these is a telnet server telnetd-ssl which installed without problem and works either localhost or from other computers internal to this network but does not do so from external sources.

Poking mckenzietrust.com on port 23 from external sources reports port 23 as closed.

OK so naturally you look at the firewall on the router, a Netgear dg834g v4, to check the port forwarding.  In the firewall rules telnet service is forwarded to the UBUNTU NAT address and marked allow always.  The web server on 80 points in the same way (to a different m/c) and that works fine so it appears to be set up correctly.  I have the latest firmware from Netgear so that should be OK.

I have mailed manxnet to ask if they perhaps block telnet packets upstream but this seems very unlikely (they havent replied yet)

As far as I know there are no .allow files needed on UBUNTU but anybody who has any ideas about how to resolve this problem I would appreciate them!

Please free to try to telnet to mckenzietrust.com - it is only the test UBUNTU m/c that is at the other end and there is no confidential data on it even if you could guess the password (:

---

### Post by Verbeck on 2010-11-14
works fine when i try:

```
verbeck@Vector-Sigma ~ $ telnet mckenzietrust.com
Trying 87.254.74.112...
Connected to mckenzietrust.com.
Escape character is '^]'.
Ubuntu 10.04.1 LTS
jsm-ubuntu login:

``````
verbeck@Vector-Sigma ~ $ telnet-ssl mckenzietrust.com
Trying 87.254.74.112...
Connected to mckenzietrust.com.
Escape character is '^]'.
[SSL - attempting to switch on SSL]
[SSL - handshake starting]
SSL: Server has a self-signed certificate
SSL: unknown issuer: /O=Internet Widgits Pty Ltd/OU=jsm-ubuntu telnetd/CN=jsm-ubuntu./emailAddress=root@jsm-ubuntu.
[SSL - OK]
Ubuntu 10.04.1 LTS
jsm-ubuntu login: 

```

---

### Post by captainiom on 2010-11-14
Don't understand!!
Here is output from net testing tool at hq42.net
"
Back to the Test a Telnet Server page
Service appears to be down, port 23 is closed. 
"

---

### Post by Verbeck on 2010-11-14
that must be broken..
[http://www.t1shopper.com/tools/port-scan/](http://www.t1shopper.com/tools/port-scan/)
result 
[img]http://img594.imageshack.us/img594/5581/screenshot1im.png[/img]
also
[img]http://img237.imageshack.us/img237/3818/screenshot2rb.png[/img]

---

