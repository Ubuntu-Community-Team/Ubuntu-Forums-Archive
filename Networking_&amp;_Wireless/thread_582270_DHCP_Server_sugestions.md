---
title: "DHCP Server sugestions"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by monkeymartin on 2007-10-19
I am looking for a good dhcp serve solution for my network

We have 200 customers that we statically link in the dhcp server.  Can you suggest a solution.


wee need to be able to setup 

more ghthan one ip ranges 

It would be nice to make changes through a web interface (like a router)

all this box has to do is dhcp.  

Looking for a solution that is secure and easy to add reservation.

I would like the office to be able to check the records.

It would be nice to be able to keep other customer information along with the reservation 

What is my best choice Linux server, Router, windows server.  I don't like the idea of a windows server because of the security issues.

thanks i know I am asking for a lot 

thanks

---

### Post by louie55 on 2007-10-19
I'm no server expert, nor am I a DHCP expert. But, I would suggest Ubuntu Server Edition with DHCPD installed and using Webmin as your web browser based configuration tool.

Here's webmin's site:
[http://www.webmin.com/](http://www.webmin.com/)

And here's the page that shows how to use Webmin to configure a DHCP server (including screenshots!):
[http://doxfer.com/Webmin/DHCPServer](http://doxfer.com/Webmin/DHCPServer)

Louie

---

