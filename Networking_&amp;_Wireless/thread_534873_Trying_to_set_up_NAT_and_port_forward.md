---
title: "Trying to set up NAT and port forward"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by DarchAengel on 2007-08-25
I am using a belkin router; model # F5D7230-4 ver. 6002.  I am trying to port foward so I can use Azureus.  I've done this before on my Mac but no matter what I do I keep getting errors.  Is there an extra step that I am missing?

---

### Post by Darkhack on 2007-08-25
Is the Belkin router giving you the errors you speak of, or is it Azureus giving the error about ports not being forwarded?  Can you be more specific about "getting errors"?

---

### Post by DarchAengel on 2007-08-25
Well when I test a port, in this case 49152, the test menu gives me a NAT error.  When I use that port # in the router firmware and reload Azureus the NAT indicator says that it is firewalled.

---

### Post by DarchAengel on 2007-08-25
Okay I found a thread on the forums about opening TCP and UDP ports through the terminal but the command lines don't seem to do anything.

 iptables -I INPUT -p udp --dport <your port number here> -j ACCEPT
 iptables -I INPUT -p tcp --dport <your port number here> -j ACCEPT

Not sure what I am missing.  I entered the port as they told me to do.

---

### Post by ruibernardo on 2007-08-25
Select your router on this page: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Then select the program you want, azureus in this case.

---

