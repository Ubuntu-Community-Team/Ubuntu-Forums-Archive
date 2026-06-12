---
title: "problems with my gateway"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by onthejazz on 2010-12-29
On my windows pc my default gateway = 192.168.1.254. 

On my ubuntu server my /etc/network interface reads

The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.210
netmask 255.255.255.0
gateway 192.168.1.254


However my ifconfig reads

inet addr:192.168.1.210  Bcast:192.168.1.255  Mask:255.255.255.0


why does the bebox not use 192.168.1.254?

---

### Post by QLee on 2010-12-29
> **onthejazz said:**
> On my windows pc my default gateway = 192.168.1.254. 

On my ubuntu server my /etc/network interface reads

The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.210
netmask 255.255.255.0
gateway 192.168.1.254


However my ifconfig reads

inet addr:192.168.1.210  Bcast:192.168.1.255  Mask:255.255.255.0


why does the bebox not use 192.168.1.254?

What is a bebox? Are you referring to the old computer of that name, BeBox?

Are you saying that your Ubuntu can't surf the net? Or, why would you expect, the  ifconfig, command to show the gateway, which is the IP address of your gateway? 

Can you re-phrase your question?

---

### Post by onthejazz on 2010-12-29
> **QLee said:**
> What is a bebox? Are you referring to the old computer of that name, BeBox?

Are you saying that your Ubuntu can't surf the net? Or, why would you expect, the  ifconfig, command to show the gateway, which is the IP address of your gateway? 

Can you re-phrase your question?

I'm sorry my bebox is my modem/router. 

I'm talking about my ubuntu server. It can connect to the internet and the ifconfig is

inet addr:192.168.1.210  Bcast:192.168.1.255  Mask:255.255.255.0

Whereas, my gateway for my modem/router and my windows pc is 192.168.1.254. I thought the Bcast address and the default gateway were the same things? Should they not be the same on my entire network?

---

### Post by QLee on 2010-12-29
> **onthejazz said:**
> ... I thought the Bcast address and the default gateway were the same things? Should they not be the same on my entire network?

No. The broadcast address is normally the top address of the address range on your subnet. In your case the top address of the 192.168.1.0 through 192.168.1.254. 

The "gateway" address is where your computers send connection requests. For example, a DNS request or a request for a website, your gateway (probably a broadband modem/router/firewall/NAT combination) does the network address translation and routes the request to the WAN (Internet) and then routes returning packets back to your computer.


[Edit] I should add, yes, the gateway does need to be the same and it is because you can surf from your Ubuntu computer.

---

### Post by onthejazz on 2010-12-29
> **QLee said:**
> No. The broadcast address is normally the top address of the address range on your subnet. In your case the top address of the 192.168.1.0 through 192.168.1.254. 

The "gateway" address is where your computers send connection requests. For example, a DNS request or a request for a website, your gateway (probably a broadband modem/router/firewall/NAT combination) does the network address translation and routes the request to the WAN (Internet) and then routes returning packets back to your computer.


[Edit] I should add, yes, the gateway does need to be the same and it is because you can surf from your Ubuntu computer.

Thanks

---

