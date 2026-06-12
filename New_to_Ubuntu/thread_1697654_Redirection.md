---
title: "Redirection"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by rhcev5 on 2011-03-01
Hello,

we have a website which connects to a our router and gets some data from a local machine via a connection string. This router is connected to a squid proxy server. The local machine is then connected to this squid server. 

The website code's connection string has the routers address and connects to port 8080. Now I have to configure this router to redirect this request to port 8080 to the squid server and then redirect to the local machine from where it will fetch the data. Squid server has a live(public) ip and also serving as the DHCP server(10.1.0.1). Local machine has ip 10.1.0.x.

I have forwarded the incomming request at port 8080 of the router to this squid machine's IP's port 8080. Also local machine's are configured to access internet via port 3128. 

What should I do to make this connection string fetch the required data from this local machine behind the squid server.

Hope you have understood my problem.

Please help.

---

### Post by HermanAB on 2011-03-01
Use the iptables redirect option.  Read the iptables man page about 5 times...

---

### Post by rhcev5 on 2011-05-12
Please help.

---

