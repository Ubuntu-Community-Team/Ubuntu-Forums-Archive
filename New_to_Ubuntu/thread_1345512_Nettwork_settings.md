---
title: "Nettwork settings"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by hawk007 on 2009-12-04
Hi, im totally new to this linux/ubuntu stuff. Here is the problem im having.
 
My router recognized the server and an ip addres of 192......1.1 something like that.
 
I changed the settings as prescribed using: $ sudo vi /etc/network/interfaces
 
Here are the new settings:
 
THE LOOPBACK NETWORK INTERFACE
auto lo
iface lo inet loopback
 
THE PRIMARY NETWORK INTERFACE
auto eth0
iface eth0 inet static
address 81.x.x.182
gateway 81.x.x.190
netmask 255.255.255.240
network 81.x.x.176
broadcast 81.x.x.191
 
Now my router doesnt recognize theres a server on. I also tried changing the:
 
sudo vi /etc/resolv.conf
 
FROM:
 
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
 
TO:
 
domain gateway.2wire.net
search gateway.2wire.net
nameserver 81.x.x.181
nameserver 192.168.1.254
 
 
Still the router doesnt recognize i have a server on.
 
Using a proliant DL580 server theres also iLO which i dont understand at all but the settings in the interface are: 
 
IP 0.0.0.0
netask 0.0.0.0
DNS 0.0.0.0 etc
 
I have to remove the ethernet cable from the network card to the iLO slot to get iLO to have any settings whatsoever from the router.
 
Any help would be greatly appreciated.

---

### Post by yeats on 2009-12-04
> My router recognized the server and an ip addres of 192......1.1 something like that.

but you are assigning a static IP on a different subnet:

```
address 81.x.x.182
gateway 81.x.x.190
netmask 255.255.255.240
network 81.x.x.176
broadcast 81.x.x.191
```

Where are you getting the 81.x.x.x addresses?  If your router is using the 192.x.x.x range, you have to use that or it will not work.

---

### Post by hawk007 on 2009-12-04
I have static ip addresses and want to use them for the server. ie change router to map my static ip to the server. But after i changed addresses in ubuntu router doesnt know theres a server plugged in at all

---

### Post by yeats on 2009-12-04
> I have static ip addresses and want to use them for the server. ie change router to map my static ip to the server. But after i changed addresses in ubuntu router doesnt know theres a server plugged in at all

In your router settings, what is the IP range for which it will work?  If it doesn't know about the IP addresses you're setting on the Ubuntu server, it will not work.  The router will only see what you tell it to and if the server IP is outside the range you tell it to use, the router won't "see" it.

Also, in your /etc/network/interfaces, where is the gateway address coming from?  This would typically be the router/gateway you use to connect to the Internet, but it sounds like that's not the case here.

---

### Post by hawk007 on 2009-12-04
These are the ips my isp has allocated to me.
 
You've ordered a range of Static IP addresses, which contains 16 addresses from 81.142.255.177 to 81.142.255.189. Three of these are reserved:
[LIST]
[*]network address: 81.142.255.176
[*]router/Hub address: 81.142.255.190
[*]subnet mask address if you have 5 Static IP addresses: 255.255.255.248
[*]subnet mask address if you have 13 Static IP addresses: 255.255.255.240
[/LIST]My /etc/network/interfaces ips are as follows:THE LOOPBACK NETWORK INTERFACE
auto lo
iface lo inet loopback

THE PRIMARY NETWORK INTERFACE
auto eth0
iface eth0 inet static
address 81.142.255.182
gateway 81.142.255.190
netmask 255.255.255.240
network 81.142.255.176
broadcast 81.142.255.191

---

### Post by yeats on 2009-12-04
> **router/Hub address: 81.142.255.190**

Does the router know that it has this address?  Your first post indicated that it was in the 192.x.x.x range,

---

### Post by hawk007 on 2009-12-04
My router doesnt even know theres a server attached. Its not the lead because when i plug the ethernet cable into iLO (integrated Lights Out) on the rear of the server the iLO is assigned 192.168.1.1 ip. The router recognizes the iLO input but not the network card.
 
When it does eventually recognize theres a server attached i can map the ip ending 182 (the one i want to use for that server) but not until the ruter recognizes the network card.
 
The card has been working ok i think. I did diagnostics on it which i am now going to do again.
 
By the way thanks for the assistance.

---

### Post by yeats on 2009-12-04
Okay, by way of diagnostics, I would recommend this, then I'm going to leave you to it ;-):

Undo the changes to /etc/network/interfaces and /etc/resolv.conf (make backups to *filename*.orig or something like that so you don't have to redo everything).  Then restart networking.  If Ubuntu 9.04 or before:

```
sudo /etc/init.d/networking restart
```

If you're using 9.10, it's:

```
sudo service networking restart
```

Then connect the server to the router and do:

```
sudo dhclient eth0
```

Even if it doesn't work it will provide useful feedback.  Good luck with everything and I hope you figure it all out.

---

### Post by hawk007 on 2009-12-04
Broadcom NC7771 Gigabitbnserver Adaptor Tests OK. Il try to update firware now

---

