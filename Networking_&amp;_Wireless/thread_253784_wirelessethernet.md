---
title: "wireless/ethernet?"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by Vajs on 2006-09-08
I have Realtek RTL8139/810x Family Fast Ethernet NIC card and some thing on my roof called acces point.Realtek card and AP arre connected with cable,AP have wireless connection with my provider.Under Windows XP everything works just fine but with Ubuntu i can't open any web page. In Connections dialog it says Ethernet connection active using eth0.And everything looks ok.
How it works with windows. First I enable Local Area Connection then open my web browser and instead of home page there is page for login. There I type my user name & password and im connected.Easy.. What should I do with Ubuntu to get on the net? :)

---

### Post by whizbaby on 2006-09-09
Have you typed **sudo pppoeconf eth0** to configure the connection? (username and password for the provider and some settings for the connection)

---

### Post by dannyb37 on 2006-09-12
type into firefox ```
about:config
``` and in the filter type ipv6 and double click it. Restart FireFox.

If it works you have the same problem as me! ;) I dunno what the problem is - beein' the newbi I am. lol

---

### Post by whizbaby on 2006-09-12
Does not-posting-anymore mean it's solved, or what (and if yes,what did it)?

---

### Post by Vajs on 2006-09-12
heh,no. Problem is not solved. My connection is not pppoe. I use ethernet to connect wireless with my provider.

---

### Post by whizbaby on 2006-09-13
> **Vajs said:**
> How it works with windows. First I enable Local Area Connection then open my web browser and instead of home page there is page for login.
When that page is up, what do you see in the adress bar of the browser? Have you tried typing that into firefox?

---

### Post by Vajs on 2006-09-13
Yes I tried but nothing happens. Here it is: [http://www5.zrlocal.net/login?dst=http%3A%2F%2Fwww.google.com%2Fintl%2Fsr%2F](http://www5.zrlocal.net/login?dst=http%3A%2F%2Fwww.google.com%2Fintl%2Fsr%2F) .After login it automaticaly redirects me to my home page (as you see: [www.google.com/intl/sr/](www.google.com/intl/sr/) )

---

### Post by whizbaby on 2006-09-14
Has the AP thingy an IP adress (tried to put that in the browser?) or can it provide dhcp? (Besides, nothing happens when I click on your link and I've got full internet access)

---

### Post by Vajs on 2006-09-14
IP adress is not static.In Local Area Connection settings (in Windows) it says Adress type: assigned by DHCP

---

### Post by Vajs on 2006-09-14
Maybe this can help. Network connection details when I'm logged in and when I'm logged out.
Logged in:
[IMG]http://ubuntuforums.org/gallery/data/500/logged_in.jpg[/IMG]
Logged out:
[IMG]http://ubuntuforums.org/gallery/data/500/logged_out.jpg[/IMG]

---

### Post by whizbaby on 2006-09-14
Then let's try
**sudo dhclient eth0**
Does it get DHCPOFFER or is there an error again? Can you now get to the page?

---

### Post by Vajs on 2006-09-14
Here it is:
```

vajs@vajs-desktop:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:11:09:97:3d:bd
Sending on   LPF/eth0/00:11:09:97:3d:bd
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.4.3.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.4.3.1
bound to 192.168.103.5 -- renewal in 7 seconds.
vajs@vajs-desktop:~$


```
Still cannot get to the page....

---

### Post by whizbaby on 2006-09-15
And if you type one of these in your browser?  
192.168.103.1 
10.4.3.1

---

### Post by Vajs on 2006-09-17
Still nothing... It recognize both adresses as www5.zrlocal.net/login but nothing happens.

---

### Post by whizbaby on 2006-09-17
I just had an idea: what if your login page needs flash or sun-java? Got these installed?

---

### Post by Vajs on 2006-09-17
I think I don't need that because it is a simple page without any flash or java content.But for any way, where I can check it out if Java or Flash are installed or not? I don't know much about Ubuntu :)

---

