---
title: "2  Network Cards"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by patihk19 on 2008-07-03
I would like to be able to use  2 network cards  at the same time. 
Can i access both networks at the same time  ? 

I tried DHCP on both devices , both devices got separate  IP addresses  but  i am able  to only access one network.

---

### Post by nixscripter on 2008-07-03
If you mean using two cards connected to different networks, yes, you can use them at the same time.

The first question is, which one to use as the default route. That is to say, which one to send packets out of when you're not sure exactly how they are going to get to the destination. Usually, this would be one connected to the internet. If they both are, then it doesn't matter.

The "one at a time" problem is usually caused by software using defaults. You can set it up by editing the **/etc/network/interfaces** file. Information on its contents can be found here: [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

Hope this helps.

---

### Post by patihk19 on 2008-07-04
I  have followed the article and  did the  following  only the VPN is working

auto eth0 eth2
mapping eth0 eth2
        script /path/to/get-mac-address.sh
        map 00:1e:c9:6c:1f:56 Internet
        map 00:08:a1:b9:9e:c0 VPN
iface Internet inet static
        address 192.168.1.11
        netmask 255.255.255.0
        gateway 192.168.1.1
iface VPN inet static
        address 10.9.4.64
        netmask 255.255.248.0
        gateway 10.9.0.1

---

### Post by patihk19 on 2008-07-04
I  have also tried  using DHCP for both cards  by typing  

auto eth0 
iface eth0 inet static 

auto eth2
iface eth2 inet static

Only  one  card gets an IP . I also have  the  gui network manager installed  and  if I choose  romaining  enabled  i can switch between cards  and  both cards  work when connected  to only  one network. 

Please help !!!

---

### Post by nixscripter on 2008-07-05
Slow down, I'll need to know a little more about what you're trying to do.

1. What is home and VPN?
2. What are eth0, eth2, Internet and VPN in your file above?
3. Are there any non-physical devices (i.e. software not cards)?

---

