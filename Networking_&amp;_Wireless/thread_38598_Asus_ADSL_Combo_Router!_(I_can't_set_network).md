---
title: "Asus ADSL Combo Router! (I can't set network)"
date: 2005-06-01
forum: Networking &amp; Wireless
---

### Post by ridvantulunay on 2005-06-01
I just installed Ubuntu 5.04. While I was installing it, it detect my network with dhcp. But after ubuntu is installed and started with gnome, I couldn't use my netwoks that is known by dhcp (In the network setting dialog it shows me, eth0 detected and activated). Now I can't browse any internet page, and I don't know what can I do? I am waiting you to help me about this problem!

---

### Post by baRRacuda on 2005-06-01
this should be a dns problem
i had the same problem with the same modem  :) and i did these :

[QUOTE=topcop]best way, if you want to have custom DNS servers and continue to use DHCP is to specify them in /etc/dhcp3/dhclient.conf

add a line like this in the above file (replace x's with your nameservers):  

supersede domain-name-servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx;[/QUOTE]



look here for more info:
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

 :wink:

---

### Post by ridvantulunay on 2005-06-01
_I added dns-name-servers:192.168.1.1 but nothing changed. _

Then I wanted to set my network *manually*, so I opened the network setting dialog, and entered the value like this;

Ip adress: 192.168.1.20
Netmask:255.255.255.0
Gateway:192.168.1.1
DNS:192.168.1.1

in Windows dhcp is detected same value.

**But again nothing changed!**I cannot browse any page!

---

### Post by baRRacuda on 2005-06-01
you shouldn't add your modem's ip there..

use working dns' like
195.175.37.69 and 195.175.37.69 

so add
```
supersede domain-name-servers 195.175.37.69, 195.175.37.14;
```

---

### Post by ridvantulunay on 2005-06-01
I didn't add my modem's ip, I added only my DNS..(192.168.1.1) like this..
supersede domain-name-servers 192.168.1.1

my original setting that I took with dhcp in windows are;

Ip adress: 192.168.1.20
Netmask:255.255.255.0
Gateway:192.168.1.1
DNS:192.168.1.1

I set these value manually on ubuntu' s network setting dialog but nothing changed.

Note: you should send me a message with your language (turkish)!

---

