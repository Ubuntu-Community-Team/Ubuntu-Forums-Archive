---
title: "Dnsmasq configuration for local network"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by Rafal_Baba on 2014-02-24
[COLOR=#333333][FONT=UbuntuRegular][FONT=arial]I am going to configure dnsmasq for my local home network but I am not sure if I understand it. Basically I have a simple network at home:[/FONT]
[/FONT][/COLOR]
[LIST]
[*]laptop - 192.168.0.10
[*]phone (galaxy s2 - ubuntu touch with LAMP server) - 192.168.0.14
[*]router - 192.168.0.1
[/LIST]

[FONT=arial][COLOR=#333333]I have installed dnsmasq on my phone where I have a LAMP server. My problem is that every time when I create new site on my server I have to add it to my /etc/hosts file on my laptop like that:[/COLOR][/FONT]
```
192.168.0.10  testingsite.dev
```
[FONT=arial][COLOR=#333333]Basically I would like to have it done by dnsmasq automatically but I don't know how to set it up for the network. It works locally (I mean on the phone) but not for computers which belong to the network. Does anyone know how the /etc/dnsmasq.conf file should look like and do I need do something extra? If you need more details let me know.[/COLOR][/FONT]

---

### Post by Rafal_Baba on 2014-03-01
Seriously, there must be someone who had a similar problem.

---

