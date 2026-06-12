---
title: "Webmin: Good option?"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2007-08-22
Dear Comarade,

I plan to have a **Webmin** in my Linux own build router.

I must have the **DHCP** and **DNS** on the linux box which provide to my connected client.It is Webmin the best option for me?

Network setup:-
[http://www.geocities.com/fy_heng/Network.JPG]("http://www.geocities.com/fy_heng/Network.JPG")

IF I installed the Webmin, do I need to install the dhcp3-server and the DNS server? or the Webmin auto install the DHCP and DNS once i start on it?


Please give some info to me. Thanx ^_^

---

### Post by EndPerform on 2007-08-22
Webmin is just an generic system administration interface, it does not install any servers for you.  If you need a DHCP server, you'll have to install it.

---

### Post by Paris Heng on 2007-08-22
> **EndPerform said:**
> Webmin is just an generic system administration interface, it does not install any servers for you.  If you need a DHCP server, you'll have to install it.

Ic, thanx alot. The **dhcpd** it the same function as **dhcp-3.server**? Which one i should install?
I need a **DNS server** as well.

---

### Post by ragrim on 2007-08-22
With webmin it doesnt install anything for you other than the webmin interface, once webmin is installed it has tabs that show you all the modules it supports, if the module is installed, in your example DHCP and DNS itll give you options to change settings, if its not installed most modules can be installed via webmin by clicking the get module button then it does an apt-get and installs it for you.

*NOTE* ive had issues installing things like DHCP and DNS via webmin, i would suggest manually installing anything you want to use.

---

### Post by Paris Heng on 2007-08-23
> **ragrim said:**
> With webmin it doesnt install anything for you other than the webmin interface, once webmin is installed it has tabs that show you all the modules it supports, if the module is installed, in your example DHCP and DNS itll give you options to change settings, if its not installed most modules can be installed via webmin by clicking the get module button then it does an apt-get and installs it for you.

*NOTE* ive had issues installing things like DHCP and DNS via webmin, i would suggest manually installing anything you want to use.

Ok thanx, i will try on it

---

