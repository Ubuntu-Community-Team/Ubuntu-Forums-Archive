---
title: "[SOLVED] Telindus adsl 1133 modem/router cannot update"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2007-06-07
Hello,

I'm trying for a week to configure my modem with partial success. I can connect to the internet via DHCP and static IP address. Yet when I want to use automatic updates, simply I cannot download them. I spent 12 euros on a network card only to see that disabling ipvc6 does the job both on usb and ethernet connection. I have tried many different combinations so as to be able to connect _and_ update, yet with no success.

The version of ubuntu I'm using is Dapper Drake. I have tampered with apt-conf (/etc/apt/) with no success. rpppoe doesn't seem to work either. Even pppoeconf or sudo pppoeconf if you prefer, doesn't do the job as well. I get the access concentrator message so I cannot configure my connection from there. 

The only thing that worked was sudo gedit /etc/modprobe.d/aliases and from there
change the alias net-pf-10 ipv6
with           alias net-pf-10 off # ipv6

I have to say that Steve's usbadslmodemmanager didn't work, yet the error I got was the same as one from a speedtouch modem user (I expect the answer as well).Yet, even that way I do not know whether this will solve the issue of updates.

Does anyone know anything about the update issue of ubuntu and how to fix this irksome problem?

Thanks in advance!

---

### Post by Claus7 on 2007-06-09
Hello,

Problem solved both with the connection (via ethernet) and with the update of synaptic package manager. The link is here:

[http://ubuntuforums.org/showthread.php?t=336073](http://ubuntuforums.org/showthread.php?t=336073)

Regards!

---

