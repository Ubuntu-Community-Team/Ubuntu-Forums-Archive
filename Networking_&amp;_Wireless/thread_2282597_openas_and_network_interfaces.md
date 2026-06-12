---
title: "openas and network interfaces"
date: 2015-06-15
forum: Networking &amp; Wireless
---

### Post by Jack_Burghardt on 2015-06-15
I have installed openas on top of 14.04 lts and I have issue where interfaces gets overwritten every five minutes. I wonder if anyone know what could overwrite my settings ?

---

### Post by cusinndzl on 2015-10-20
This is an old thread, but I ran across this issue today and solved it.

The application gets the configuration for the network interfaces from an XML file and will continually overwrite whatever is in the /etc/network/interfaces file with what's in the XML file. 

The XML file is: /etc/open-as-cgw/xml/system.xml

Towards the top there is the network configuration. Just replace that (you might have to stop the openas services first) and then reboot.

---

