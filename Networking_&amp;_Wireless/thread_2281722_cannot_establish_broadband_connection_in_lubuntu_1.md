---
title: "cannot establish broadband connection in lubuntu 14.04"
date: 2015-06-09
forum: Networking &amp; Wireless
---

### Post by Agnishwar_Samanta on 2015-06-09
[COLOR=#111111][FONT=Ubuntu]I have a broadband connection... I cant establish the connection in lubuntu.. I have read some forums and tried the "sudo pppoeconfig" command, and the message that appeared was[/FONT][/COLOR][INDENT]```
"Sorry, I scanned 2 interfaces, but the Access concentrator of your provide did not respond. 

Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process 

which controls the modem"
```[/INDENT]
[COLOR=#111111][FONT=Ubuntu]here are the other informations-[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]1)output of[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]cat /etc/network/interfaces[/FONT][/COLOR]
```
auto lo

iface lo inet loopback

auto dsl-provider

iface dsl-provider inet ppp

pre-up /sbin/ifconfig eth0 up # line maintained by 

pppoeconf

provider dsl-provider

auto eth0

iface eth0 inet manual
```
[COLOR=#111111][FONT=Ubuntu]2)i'm using a wired ADSL router.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]3)I use the router's inbuilt dialer (pppoe mode)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]4)I use dhcp[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]5)cant ping to 192.168.1.1[/FONT][/COLOR]

---

