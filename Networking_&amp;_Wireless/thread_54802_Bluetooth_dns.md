---
title: "Bluetooth dns"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by z!cHz@cH on 2005-08-06
I have a problem with blueZ.

i can connect to my internet gateway but i cant visit website's.

this is what i do to connect to my internet gateway:

sudo /sbin/modprobe bnep

sudo pand -c **:**:**:**:**:**

sudo /sbin/ifconfig bnep0 192.168.4.2 netmask gw 255.255.255.0

sudo /sbin/route add default gw 192.168.4.1

it works fine i can ping an ftp server on the internet by using its ip adress but when i try to ping it by name it doesnt work. I can't visit websites by using the name.

when i plug in my ethernet cable it does work and i can visit websites. Does someone know what could be the problem?

---

### Post by jasmuz on 2005-08-07
Your problem lies withing DNS resolution for the Bluetooth connection. 
You might consider installing dnsmasq to see if it can do you any good.

---

### Post by z!cHz@cH on 2005-08-08
[QUOTE=jasmuz]Your problem lies withing DNS resolution for the Bluetooth connection. 
You might consider installing dnsmasq to see if it can do you any good.[/QUOTE]

Thanks this helpt me a lot. It was indeed using a wrong dns server

---

