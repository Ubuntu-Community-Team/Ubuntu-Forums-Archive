---
title: "Squid3 Configuration"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Nazil on 2011-03-31
Please any buddy help me **Squid3 Configuration **Please Please Please .......

---

### Post by bodhi.zazen on 2011-04-01
What about it ? What are you trying to configure ?

Unfortunately I find the squid documentation is a bit lacking.

Fortunately the configuration file is well commented, and reading it should be your first step.

Unfortunately it is about 4,000 lines long last time I counted.

If you want more specific help you will need to explain what you are needing help with.

---

### Post by Nazil on 2011-04-01
**Squid3 Configuration** 			
 			 			 		   		 		 		Hello,
 
Good Morning,
 
I need help to publish the Public IP for the webserver to access outside LAN.
 
I have an **UBUNTU server 10.10** machine running with **squid3** configured as transparent proxy successfully.
 
Now I have a other machine running with **apache2 webserver** and my  local website is hosted on it. I want this webserver to be used outside  the LAN using the Public IP the Public IP is provided by our ISP.

The  following is my setup for your reference:
 
**Internet**
**||**
**UBUNTU Server10.10 with SQUID3 *(Transparent Proxy, IP: 192.168.1.1)***
**||**
**LAN**
**    ||**
**    Webserver *(IP: 192.168.1.5 Name: computerscience)***
 
I need to assign a public IP for the webserve as 61.8.153.212
 
In my LAN I can access this webserver with out any problem same way I want to access my computer/webserver outside the LAN
 
Please help me with complete configuration to the above setup through SQUID3.......

---

