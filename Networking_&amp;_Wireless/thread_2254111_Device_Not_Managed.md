---
title: "Device Not Managed"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by mehraks9 on 2014-11-25
I have installed Edubuntu 12.04 on IBM Server with two NIC along side Windows Server 2008.The configuration is eth0 and eth1 both are connected to switch and switch is with router (Belkin) with DHCP enabled. Client PC are booting successfully but the problem is eth0 is shown  as Device not managed. Clients are booting with default eth1 NIC on 192.168.0.20. Server is not connecting to internet.
I have also tried Edubuntu 140.4.1 but the problem remain same.
Is there any mannual setting or configuration to perform network boot and internet connectivity at the same time?
Kindly help........ earlier post still pending.

thanks

---

### Post by steeldriver on 2014-11-25
Can you post the contents of your /etc/network/interfaces file please?

---

### Post by mehraks9 on 2014-11-26
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.0.254
  netmask 255.255.255.0


this is the default ip for eth1 on my system 192.168.0.20

---

### Post by steeldriver on 2014-11-26
What are you trying to achieve with the dual NIC configuration? I don't  understand what you mean by "Clients are booting with default eth1 NIC  on 192.168.0.20". Are you trying to route traffic between the two NICs  on the server? 

Why do you think that "device not managed" is the problem? it's usually just an informational message from NetworkManager indicating that the device has been manually configured via /etc/network/interfaces - you can change that behaviour via the /etc/NetworkManager/NetworkManager.conf file by changing 

```

[ifupdown]
managed=false

```
to
```

[ifupdown]
managed=true

```

but I don't think it will have any effect on the internet connectivity. Your eth0 definition probably needs at least a gateway and a dns-nameservers field.

---

### Post by mehraks9 on 2014-11-26
Thank you so much for quick reply.what I want is to have internet connectivity on server as I m new to edubuntu. Actually when server is running, the rest of the windows system on my LAN and Edubuntu server gets disconnected from internet.My LAN setup  is Router-Switch-Systems + Server. In Router DHCP Server is on.I want all the things to work i.e 
1. Edububtu server running with internet access
2. Windows pc running with internet if no network booting enabled..
 I have tried to make my problem clear as I m not so good in English.. Kindly suggest some methods to configure gateway and dns-nameservers.


thanks n regrads

---

### Post by Bashing-om on 2014-11-26
mehraks9; Hi !

An example of a working /etc/network/interfaces file:
```

auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet static
           address 192.168.1.150
           netmask 255.255.255.0
           gateway 192.168.1.1
           dns-nameservers 8.8.8.8 192.168.1.1

```

Of course, your numbers will be different to suit your network.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

