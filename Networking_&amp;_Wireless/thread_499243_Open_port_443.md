---
title: "Open port 443"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by dutch1918 on 2007-07-12
I have installed Apache2 and apache-ssl. I looked in the Services and see they are both running.  When I did a test with [http://192.168.1.20/hot/index.html](http://192.168.1.20/hot/index.html) I can see the page ok.  When I do [https://192.168.1.20/hot/Index.html](https://192.168.1.20/hot/Index.html) I get "Unable to connect"

When I did a Port Scan under Network tools it says only port 80 is open. I checked in the apache-ssl/httpd.conf file and it has Listen 443.

So how do I get port 443 open

BTW I have no firewall or iptables set

---

### Post by meatpan on 2007-07-12
Are you running the tests locally or remotely  (i.e., is 192.168.1.20 your current workstation)?  'ifconfig' should let you know.   If you are not running locally, check and see if the router is allowing access to 443, and performing the subsequent port-forwarding request.  

Just for the do-diligence, run a 'grep 443 /etc/services' on the server to verify the application default ports are mapped correctly.

---

### Post by dutch1918 on 2007-07-12
> **meatpan said:**
> Are you running the tests locally or remotely  (i.e., is 192.168.1.20 your current workstation)?  'ifconfig' should let you know.   If you are not running locally, check and see if the router is allowing access to 443, and performing the subsequent port-forwarding request.  

Just for the do-diligence, run a 'grep 443 /etc/services' on the server to verify the application default ports are mapped correctly.

The test was run locally.


grep returns:

https           443/tcp                         # http protocol over TLS/SSL
https           443/udp

:confused:

---

### Post by kevdog on 2007-07-12
Do you have a firewall running - such as firestarter, guarddog etc?  or do you use manual configuration to configure the iptables file.  All server ports are closed by default, unless you open them.

---

### Post by dutch1918 on 2007-07-13
> **kevdog said:**
> Do you have a firewall running - such as firestarter, guarddog etc?  or do you use manual configuration to configure the iptables file.  All server ports are closed by default, unless you open them.

Problem resolved. Did not have the "Listen 443" in etc/apache2/ports.conf :)

---

