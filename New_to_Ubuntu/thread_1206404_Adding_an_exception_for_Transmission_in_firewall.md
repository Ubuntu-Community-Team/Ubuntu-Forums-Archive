---
title: "Adding an exception for Transmission in firewall"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Wisey on 2009-07-07
I set the firewall to deny all incoming connections as the default state. However, this results in Transmission reporting any port as closed. 
I don't want to open a separate port for Transmission, is there any way I can configure the firewall so that incoming connections for Transmission are allowed?

---

### Post by meindian523 on 2009-07-07
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

If you are trying to open a port to listen for incoming connections,and have a router between your net connection and your box,you will have to login to the router and open the same port there.Google for your particular router.

---

### Post by meindian523 on 2009-07-07
If you prefer the Ubuntu wiki,here's the link:
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by Wisey on 2009-07-07
I figured it out, thank you!

---

### Post by meindian523 on 2009-07-07
Please mark the thread solved.

---

