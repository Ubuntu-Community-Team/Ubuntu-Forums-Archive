---
title: "[SOLVED] Static Ip Address ?"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by suffer1989 on 2008-12-01
Hey, i have my router setup with port forwarding, to allow my Torrents to run smoothly, but my IP adress is dynamic, so it keeps on changing.

After running :

```
sudo gedit /etc/network/interfaces
```
 i get 
```

auto eth0
iface eth0 inet dhcp
```


I did a google and came across several tutorials to assign a static IP Address, but all of them also required details such as gateway, and other details i simply dont know about. :confused: Can i simply set a static IP, but keep the default settings for everything else ?

I tired to use : 
```

auto eth0
iface eth0 inet static
address 192.168.1.100
```

But the net didnt work till i undid the changes.

---

### Post by zotkop on 2008-12-01
it's not that hard.
The things you should know are:
static ip = the desired ip eg:192.168.1.100
subnet = the subnet you want to be in eg: 255.255.255.0
gateway = ip of your router like eg: 192.168.1.1
dns server = you can assing the ip of your ISP's dns servers or the one of your router.

ps: yes, you have to add these things to the config file, or it will fail :s

---

### Post by suffer1989 on 2008-12-01
> **zotkop said:**
> it's not that hard.
The things you should know are:
static ip = the desired ip eg:192.168.1.100
subnet = the subnet you want to be in eg: 255.255.255.0
gateway = ip of your router like eg: 192.168.1.1
dns server = you can assing the ip of your ISP's dns servers or the one of your router.

ps: yes, you have to add these things to the config file, or it will fail :s

ok, so i know what my desided IP address should be, as well as the ip address of my router, just not sure about Subnet, or DNS. Anywhere i can find out ?

looking at this :[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)
[B]> 
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.3
*network* 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1[/B]

What do they mean by Network ?

---

### Post by suffer1989 on 2008-12-01
No worries, solved

---

