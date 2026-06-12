---
title: "Advanced Network Setup...Help please"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by spelman08 on 2008-09-24
**_[COLOR="Red"]EDIT: MY XP MACHINE IS NOW ABLE TO GET ON THE INTERNET USING LINUX ICS NOW FOR XBOX 360 CAN YOU TELL ME HOW TO GET THAT ON THE INTERNET/XBOX LIVE[/COLOR]_**

ere is a picture i made of my network setup (Dont laugh lol)

[IMG]http://liamspelman.sc11.co.uk/filespace/public/uploads/network%20setup.JPG[/IMG]

The problem is i want my linux box have a static ip and to share my internet connection from the linux box to both windows xp machine and xbox 360 and for them to have static ip's

im not a total retard when it comes to computers mainly just linux :p

Thanks in advance

---

### Post by jonobr on 2008-09-24
Sounds over complicated, why not connect directly to the gateway not through the linux box?

---

### Post by jonobr on 2008-09-24
Nice network diagram though!

---

### Post by Iowan on 2008-09-24
> **jonobr said:**
> Sounds over complicated, why not connect directly to the gateway not through the linux box?Cabling issues?

Check [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") page on connection sharing. You can set all addresses static, or get DHCP from wireless router (for eth0?) whilst having eth1 static to deal with downstream machines.

---

### Post by fwre01 on 2008-09-24
If you cant plug into the router due to lack of ports, why not place a switch inbetween your dads PC and the router, then you could plug as many devices in as you like...

---

### Post by spelman08 on 2008-09-24
> **fwre01 said:**
> If you cant plug into the router due to lack of ports, why not place a switch inbetween your dads PC and the router, then you could plug as many devices in as you like...

I know what ya mean but me parents dont want to have cabling all through the house hence the 'wireless router' lol nevamind

I made a linux box so i could not have to turn my main pc on for media shares and internet for my 360

I use firestarter...is that the best thing to do?

---

### Post by HangMan101 on 2008-09-24
(enables you pc to share internet)
you could try (and make a boot script of it to make it permanent):
```

sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -j ACCEPT
sudo iptables -A FORWARD -i eth1 -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward

```

configure eth0 and eth1 to an ip range (static)
for example:
eth0:
ip:       192.168.1.254
netmask:  255.255.255.0

eth1:
ip:       192.168.2.254
netmask:  255.255.255.0

and your wireless (can be dhcp)

now your win box(connected to eth0) should be configured:
ip:       192.168.1.1
netmask:  255.255.255.0
gateway:  192.168.1.254 (your linux box)
DNS:      (your main router ip)

now your xbox(connected to eth1) should be configured:
ip:       192.168.2.1
netmask:  255.255.255.0
gateway:  192.168.2.254  (your linux box)
DNS:      (your main router ip)

now you are completely shielded form your dad's pc and you can only connect to his but he not to yours (unless you add rule to allow the reverse)

but final note:
You say that you have barely experience with this kind of networking.
i would suggest you buy a wireless bridge as it is much easier to setup.
for more info on wireless bridge see: [http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

---

### Post by cariboo on 2008-09-24
You shouldn't need a second firewall behind your wrt54g. Also the the second nic and other devices should be on a different netblock then what the router is serving eg:

```
router:  192.168.1.0/24
Linux box  192.168.0.0/24
```

Also make sure you have nat enabled. The reason for no firewall behind the router is that unles your Mom or Dad are "3l33t h4ck3r5" then they won't be able to snoop around your system.

Jim

---

### Post by 3L33T on 2009-02-26
> **cariboo907 said:**
> The reason for no firewall behind the router is that unles your Mom or Dad are "[SIZE="5"]3l33t[/SIZE] h4ck3r5" then they won't be able to snoop around your system.

Jim


How dare you blaspheme thy username??!! :p

---

