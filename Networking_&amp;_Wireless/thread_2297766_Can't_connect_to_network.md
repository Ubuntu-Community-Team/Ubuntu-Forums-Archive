---
title: "Can't connect to network"
date: 2015-10-06
forum: Networking &amp; Wireless
---

### Post by cheeze2 on 2015-10-06
Hi, i'm new to Ubuntu.

My problem is : My PC can't connect to network or another computer on network. I do the ping and the result is this : "network is unreachable"
I have tried many method and still no result.

I write some code that i got from the internet, and here's the result :

```
sudo lshw -C network

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:08:00.0"]pci@0000:08:00.0[/EMAIL]
       logical name: p4p1
blablabla..........................
```

```
ifconfig -a

lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask : 255.0.0.0
inet6 addr : 1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric : 1
blablabla.................................................

p4p1
Link encap : Ethernet HWaddr 74:d4:35:25:xx:xx
inet6 addr : fc80::xxxx;xxxx;xxxx;xxxx/64 scope : link
blablablabla..............................................
```

```
sudo nano /etc/network/interfaces

# The loopback network interfaces
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 inet DHCP

auto p4p1 inet static
address 192.168.88.10
netmask 255.255.255.0
gateway 192.168.88.1
dns-nameservers 192.168.88.1
```


What else should i do? Please help

---

### Post by slickymaster on 2015-10-06
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by gordintoronto on 2015-10-07
What version of Ubuntu? You can't ping 192.168.88.1? (Which is an unusual router address...)

---

### Post by cheeze2 on 2015-10-09
Ubuntu ver 14.0.4. That's my router ip address (192.168.88.1), and my PC ip address is 192.168.88.10.
Can you tell me how to check my ethernet is enable or disable?

Thankyou

---

### Post by helgman on 2015-10-10
If you are not running a server without a desktop maybe you could use the network manager? 

From [https://help.ubuntu.com/community/NetworkManager:](https://help.ubuntu.com/community/NetworkManager:)

> NetworkManager should be installed by default on Ubuntu Desktop installs, as well as most flavours of Ubuntu. 

You could then input your information there. If you have the NetworkManager installed I think it will override the interfaces file (seem to recall having that problem a couple of years ago).

---

### Post by michi1983 on 2015-10-10
why do you have your IP address assigned static instead of dhcp from your router?
also, this p4p1 is kind of a fedora thing from what I've read

---

### Post by cheeze2 on 2015-10-13
> **helgman said:**
> If you are not running a server without a desktop maybe you could use the network manager? 

From [https://help.ubuntu.com/community/NetworkManager:](https://help.ubuntu.com/community/NetworkManager:)



You could then input your information there. If you have the NetworkManager installed I think it will override the interfaces file (seem to recall having that problem a couple of years ago).

I try NetworkManager coomand like :
```
sudo NetworkManager start
```

and the result is :
command not found

i assume that NetworkManager is not installed in my server so i try to install using :

sudo apt-get install network-manager network-manager-gnomeResult:
so many line with this information : E: failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/](http://id.archive.ubuntu.com/ubuntu/pool/).............................

What should i do then?

---

### Post by cheeze2 on 2015-10-13
> **michi1983 said:**
> why do you have your IP address assigned static instead of dhcp from your router?
also, this p4p1 is kind of a fedora thing from what I've read

I just want to try because dhcp doesn't work. I have changed it back to dhcp but still doesn't work.

---

### Post by michi1983 on 2015-10-13
> **cheeze2 said:**
> I just want to try because dhcp doesn't work. I have changed it back to dhcp but still doesn't work.

What does a ```
ifconfig -a
``` show when you have it set to dhcp?

---

### Post by helgman on 2015-10-14
Just re-read the original post.

```

auto p4p1 inet static
address 192.168.88.10
netmask 255.255.255.0
gateway 192.168.88.1
dns-nameserve rs 192.168.88.1
```

Assuming you are not using GNOME or Unity or KDE or any other desktop environment then the interfaces file is the place to go. I have not worked with it for some time but maybe it should be something like this?

```

auto p4p1 
iface p4p1 inet static
address 192.168.88.10
netmask 255.255.255.0
gateway 192.168.88.1
dns-nameservers 192.168.88.1
```

You could also try setting an IP address using ifconfig just to see what happens (and then try to ping the gateway):

```
sudo ifconfig p4p1 192.168.88.10/24
```

---

