---
title: "Configurar IP fija al instalar ubuntu 20.04"
date: 2021-11-22
forum: Networking &amp; Wireless
---

### Post by jdvargas2 on 2021-11-22
hola para todos, saludos desde Corrientes Argentina, es lunes 22/11/2021 15:11 hs, les quiero hacer una consulta respecto a ubuntu server 20.04.3, la cual es : como configurar una IP manual al instalar el servidor; me pide Subred:..... ?.......-Direccion: por ejemplo 192.168.0.100- Puerta de enlace:192.168.0.1-Servidores de nombres:...... ?........ - Dominios de busqueda:....... ?.......; lo cual el signo de (?) es que no se que ponerle. Agradeciendo sus deferencias saludos a uds. con un gran abrazo.

Atte.

---

### Post by chili555 on 2021-11-22
Google translate:

> Hello everyone, greetings from Corrientes Argentina, it is Monday 11/22/2021 3:11 pm, I want to ask you a question regarding ubuntu server 20.04.3, which is: how to configure a manual IP when installing the server; It asks for Subnet: .....? .......- Address: for example 192.168.0.100- Gateway: 192.168.0.1-Name Servers: ......? ..... ... - Search domains: .......? .......; which the sign of (?) is that I do not know what to put. Thanking you for your deferences, greetings to you. with a big hug.

Please try:

Address: 192.168.0.100
Subnet: 255.255.255.0
Gateway: 192.168.0.1
Nameservers: 192.168.0.1, 8.8.8.8
Search Domain: Leave blank

In future posts, please use Google translate to post your replies in US English.

[https://translate.google.com/?hl=en&tab=TT](https://translate.google.com/?hl=en&tab=TT)

---

