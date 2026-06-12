---
title: "How to automatically set Default route when connecting to Vpn"
date: 2014-02-17
forum: Networking &amp; Wireless
---

### Post by a.clever on 2014-02-17
Hi guys
I am using Vpn connections very often,but each time i must set these commands in order to connect to network

```
sudo ip route del default
```

```
sudo ip route add default via [route of specified vpn]
```

Is there anyway to these automatically for each one of vpns?

---

### Post by SeijiSensei on 2014-02-17
If you are using OpenVPN, you can [include the "up" directive]("http://askubuntu.com/questions/28733/how-do-i-run-a-script-after-openvpn-has-connected-successfully") in openvpn.conf.  That will run a script after the connection is started where you can put the routing commands.

I have no idea whether this works with the Network Management GUI.  I always edit OpenVPN configurations manually.

---

### Post by a.clever on 2014-02-18
No,Open Vpn automatically changes the default gateway.
For example when i'm in university,first i need to connect to university accesspoint,then i need to connect a vpn to connect to internet then
```
ip route
```
```
default via 172.21.0.1 dev wlan0  proto static 
10.0.0.3 dev ppp0  proto kernel  scope link  src 192.168.10.140 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
172.21.0.0/20 dev wlan0  proto kernel  scope link  src 172.21.11.20  metric 2 
172.21.0.2 dev wlan0  proto static 
172.21.0.2 dev wlan0  scope link  src 172.21.11.20 
```
then
```
sudo ip route del default
```
then
```
sudo ip route add default via 10.0.0.3
```

but i need something to do these automatically for each one of my vpns
thx

---

### Post by SeijiSensei on 2014-02-18
> **a.clever said:**
> but i need something to do these automatically for each one of my vpns

That is what the "up" directive is designed for.

---

