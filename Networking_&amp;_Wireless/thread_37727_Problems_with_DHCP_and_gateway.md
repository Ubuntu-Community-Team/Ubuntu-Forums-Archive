---
title: "Problems with DHCP and gateway"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by pccampos on 2005-05-28
Hi Ubuntu folks,


I'm using Ubuntu for a month now and I relly enjoying it. But there is a problem that makes my experience far from perfect.

I'm using a DHCP connection wich give me this configuration:

```
inet end.: 192.168.168.198
Masc: 255.255.255.255
gateway: 192.168.168.222
```

But when I boot my computer I cannot get my gateway configuration, I must do this myself with the following statements:

```
sudo ip route replace 192.168.168.222 dev eth0 scope link
sudo ip route replace default via 192.168.168.222 dev eth0
```

Others distribuition that I used could up my network without any problems. Anyone here has a clue where is the problem, and if you don't please, tell me where is the best place to put the above code on startup.


That all, thanks in advance,
Pedro

---

### Post by PiTT on 2005-05-29
I'm having the exact same problem. DHCP configures my network fine, except for the routes. The only way the routes get configured right (besides setting it up manually) is if I configure my eth0 card with a static IP address.

---

### Post by outtacontrol on 2005-08-22
To prevent from having to do the route add everytime, you have to edit your /etc/network/interfaces file and add your gateway manually there.

# The primary network interface
iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x

---

### Post by garbergs on 2006-10-21
What if you want your gateway on eth0 to be the IP of eth1, where eth1 gets its IP from a DHCP-server? I tried writing "gateway eth0" for eth1 in /etc/network/interfaces but that didn't work.

---

