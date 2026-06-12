---
title: "Iptables problem"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by SundaY82 on 2007-01-24
**Hi!**

I have some issues with forwarding of ports. I followed this guide ([http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection)) to create a iptables script for internet sharing and port forwarding and it works great except for some things.
Using the forwarding examples in the script works but not fully, i have a ftp server in the network listening on port 21, and i have this port forwarded in the script like this:

```
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 21 -j DNAT --to 192.168.0.2:21
$IPT -A FORWARD -i $WAN -p tcp  --dport 21 -m state --state NEW -j ACCEPT
```

i tried from a external computer and the forwarding worked great, but i also want to be able to from within the local network connect to the ftp using the external ip, ie i want the script to forward packages to the internal ftp server regardless if the request comes from an external or internal source, can i edit the above line somehow to fix this or add a new one?

one other question also, i want to forward both tcp and upd packages on another port. so i tried editing "-p tcp" to "-p all", according to iptables manpage that should work, but if i try that i only get this message when i try to run the script:

```
iptables v1.2.11: Unknown arg `--dport'
Try `iptables -h' or 'iptables --help' for more information.
```

Also tried setting a 0 instead of all but got the same message. I ended up creating a dublicate rule for udp and that worked, like this, but its not a pretty solution:

```
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 5580 -j DNAT --to 192.168.0.2:5580
$IPT -A FORWARD -i $WAN -p tcp --dport 5580 -m state --state NEW -j ACCEPT

$IPT -t nat -A PREROUTING -i $WAN -p udp --dport 5580 -j DNAT --to 192.168.0.2:5580
$IPT -A FORWARD -i $WAN -p udp --dport 5580 -m state --state NEW -j ACCEPT
```

Anyone able to give me some help with this?

***EDIT***
I tried removing "-i $WAN" but that didnt work, tried on port 80 that forwards to my webserver on the local net, and from the local net(same box as the webserver) putting the external ip in the address bar, but then it couldnt resolve the page.

---

### Post by handy on 2007-01-24
The following link may help:

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

---

### Post by SundaY82 on 2007-01-24
> **handy said:**
> The following link may help:

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)
I checked that post but i couldnt find anything that helps me in this case, or im to stupied to see it.

---

### Post by handy on 2007-01-24
Perhaps if you post there you will get help from **frodon** if he can, or other's that are all about iptables at the moment?

---

### Post by chantra on 2007-01-27
> **SundaY82 said:**
> **Hi!**

I have some issues with forwarding of ports. I followed this guide ([http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection)) to create a iptables script for internet sharing and port forwarding and it works great except for some things.
Using the forwarding examples in the script works but not fully, i have a ftp server in the network listening on port 21, and i have this port forwarded in the script like this:

```
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 21 -j DNAT --to 192.168.0.2:21
$IPT -A FORWARD -i $WAN -p tcp  --dport 21 -m state --state NEW -j ACCEPT
```

i tried from a external computer and the forwarding worked great, but i also want to be able to from within the local network connect to the ftp using the external ip, ie i want the script to forward packages to the internal ftp server regardless if the request comes from an external or internal source, can i edit the above line somehow to fix this or add a new one?

you might want to try:
```

WAN="eth0"
WANIP=`ifconfig ${WAN} | grep 'inet addr' | tr -s ' ' | cut -f3 -d' ' | cut -f2 -d':'`
LAN="eth1"
LANIP=`ifconfig ${LAN} | grep 'inet addr' | tr -s ' ' | cut -f3 -d' ' | cut -f2 -d':'`
...
....
$IPT -A FORWARD -i $WAN -o $LAN -p tcp --dport 80 -m state  --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT  -A PREROUTING -t nat -p tcp -d $WANIP --dport 80 -m state  --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.2:80

$IPT -t nat -A POSTROUTING -d 192.168.0.2 -s 192.168.0.0/24 -p tcp --dport 80 -m state --state NEW,ESTABLISHED,RELATED -j SNAT --to $LANIP

```
This will make it work from outside, inside but not from the serer itself.

> **SundaY82 said:**
> **Hi!**
one other question also, i want to forward both tcp and upd packages on another port. so i tried editing "-p tcp" to "-p all", according to iptables manpage that should work, but if i try that i only get this message when i try to run the script:

```
iptables v1.2.11: Unknown arg `--dport'
Try `iptables -h' or 'iptables --help' for more information.
```

Also tried setting a 0 instead of all but got the same message. I ended up creating a dublicate rule for udp and that worked, like this, but its not a pretty solution:

```
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 5580 -j DNAT --to 192.168.0.2:5580
$IPT -A FORWARD -i $WAN -p tcp --dport 5580 -m state --state NEW -j ACCEPT

$IPT -t nat -A PREROUTING -i $WAN -p udp --dport 5580 -j DNAT --to 192.168.0.2:5580
$IPT -A FORWARD -i $WAN -p udp --dport 5580 -m state --state NEW -j ACCEPT
```

Anyone able to give me some help with this?

***EDIT***
I tried removing "-i $WAN" but that didnt work, tried on port 80 that forwards to my webserver on the local net, and from the local net(same box as the webserver) putting the external ip in the address bar, but then it couldnt resolve the page.

-p all does not seem to accept --dport

---

### Post by SundaY82 on 2007-01-29
Thanks, worked great... well almost.

I have one situation that i cant get to work.

To make things more clear i have one linux box as router that shares the connection and forward ports to the internal network, this box also contain a ftp server(192.168.0.1:3346 data:33600-33700). On the network i have 2 boxes, both hosting a ftp server(one linux(192.168.0.4:6556 data:1600-1650) and one windows(192.168.0.2:21 data:34600-34700)). So i have 3 ftp servers. To make it even easier ill call the router box **1** and the linux box in the network **2** and the windows box **3**.

Connecting and transfering to and from all ftps work great but if i from an external box tries to fxp from **3** to **1** i get:

[R] 425 Can't build data connection: Connection refused.

fxping from an external box to all boxes works great too, just not when i connect from an external box (external ip to my boxes as im connecting from the outside) and tries to fxp from **3** to **1**. I havnt tried from **2** to **1** or **1** to **3** but i guess its going to behave the same.

**Anyone have a solution for this?**

My current forwarding code:
```
$IPT -A FORWARD -i $WAN -o $LAN -p tcp --dport 21 -m state  --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT  -A PREROUTING -t nat -p tcp -d $WANIP --dport 21 -m state  --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.2:21
$IPT -t nat -A POSTROUTING -d 192.168.0.2 -s 192.168.0.0/24 -p tcp --dport 21 -m state --state NEW,ESTABLISHED,RELATED -j SNAT --to $LANIP

$IPT -A FORWARD -i $WAN -o $LAN -p tcp --dport 34600:34700 -m state  --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT  -A PREROUTING -t nat -p tcp -d $WANIP --dport 34600:34700 -m state  --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.2
$IPT -t nat -A POSTROUTING -d 192.168.0.2 -s 192.168.0.0/24 -p tcp --dport 34600:34700 -m state --state NEW,ESTABLISHED,RELATED -j SNAT --to $LANIP

$IPT -A FORWARD -i $WAN -o $LAN -p tcp --dport 6556 -m state  --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT  -A PREROUTING -t nat -p tcp -d $WANIP --dport 6556 -m state  --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.4:6556
$IPT -t nat -A POSTROUTING -d 192.168.0.4 -s 192.168.0.0/24 -p tcp --dport 6556 -m state --state NEW,ESTABLISHED,RELATED -j SNAT --to $LANIP

$IPT -A FORWARD -i $WAN -o $LAN -p tcp --dport 1600:1650 -m state  --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT  -A PREROUTING -t nat -p tcp -d $WANIP --dport 1600:1650 -m state  --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.4
$IPT -t nat -A POSTROUTING -d 192.168.0.4 -s 192.168.0.0/24 -p tcp --dport 1600:1650 -m state --state NEW,ESTABLISHED,RELATED -j SNAT --to $LANIP
```

---

