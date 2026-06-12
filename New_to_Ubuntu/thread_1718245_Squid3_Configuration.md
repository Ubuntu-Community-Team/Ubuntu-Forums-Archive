---
title: "Squid3 Configuration"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Nazil on 2011-03-31
Hello,
 
Good Afternoon,
 
I need help to publish the Public IP for the webserver to access outside LAN.
 
I have a **UBUNTU server 10.10** machine running with **squid3** confgured as transparent proxy and running successfully.
 
Now I have a other machine running with **apache2 webserver** and my local website is hosted on it. I want this webserver to be used outside the LAN using the Public IP the Public IP is provided by our ISP, the following is my setup for your reference:
 
**Internet**
**||**
**UBUNTU Server10.10 with SQUID3 *(Transparent Proxy, IP: 192.168.1.1)***
**||**
**LAN**
**    ||**
**    Webserver *(IP: 192.168.1.5 Name: computerscience)***
 
I need to assign a public IP for the webserve as 61.8.153.212
 
In my LAN I can access this webserver with out any problem same way I want access my computer/webserver outside the LAN
 
Please help me with complete configuration to the above setup through SQUID3.......:P

---

