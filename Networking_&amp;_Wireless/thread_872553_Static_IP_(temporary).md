---
title: "Static IP (temporary)"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by CarlWalters on 2008-07-28
I need to temporarily assign a static IP address to my Laptop (running Ubuntu 8.04) and was wondering how to do it.

What has happened is that I have switched Broadband provider from Sky to O2. The O2 wireless router has a gateway address of 192.168.1.254 whereas the Sky wireless router had a gateway address of 192.168.0.1. The problem is that I have a TiVo which has a network card and is currently plugged into a Wireless Bridge (Netgear WGE101) via a 5 port Ethernet switch (Netgear F605). My PS3 also goes into the 5-port Ethernet switch. The TiVo currently has a fixed IP address of 192.168.0.100 and can no longer get to the internet. I can change its IP address if I can telnet into it. So I want to connect the Laptop to the Ethernet switch and use it to telnet into TiVo and change its IP address to 192.168.1.100. Then it should be able to see the network I believe. 

So to change to my Laptop over to a Static IP (temporarily) do I edit /etc/network/interfaces?

If so how do I stop the Laptop automatically connecting to the Wireless Network on power up?

---

### Post by dentaku65 on 2008-07-28
You can try in this way, let's say that your interface is eth0
(otherwise change to your dev):

Use the folliwing commands:
```

sudo killall -9 dhclient
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo ifconfig eth0 192.168.0.55 netmask 255.255.255.0 up

```

Now you should have a static IP

---

### Post by CarlWalters on 2008-07-28
Thanks for the quick reply :)

I think this is trying to do the task wirelessly isn't it? I don't mind having the laptop offline while I tweak things. If I did it this way then I'd also need to change the IP of the WGE101 wireless bridge as well wouldn't I? This is currently set at 192.168.0.200 and I was going to try to use the Laptop to re-configure this as well (to 192.168.1.201)

My plan was 
1. Give the Laptop a Static IP (say 192.168.0.XYZ)
2. Plug Laptop Ethernet into WGE101 (currently at 192.168.0.200)
3. Use the WGE101 GUI to change its IP to 192.168.1.200
4. Plug Laptop Ethernet into TiVo (currently at 192.168.0.100)
5. Use Laptop to telnet into TiVo and change its IP to 192.168.1.100
6. Revert Laptop back to non static IP


But:
1. How can I check if my wi-fi interface is eth1 (or whatever)?
2. I'd also need to change the IP of the WGE101 as well wouldn't I? As this is currently set at 192.168.0.200 and I was going to try to use the Laptop to re-configure this as well (to 192.168.1.201)

---

### Post by dentaku65 on 2008-07-28
> **CarlWalters said:**
> Thanks for the quick reply :)

I think this is trying to do the task wirelessly isn't it? I don't mind having the laptop offline while I tweak things. If I did it this way then I'd also need to change the IP of the WGE101 wireless bridge as well wouldn't I? This is currently set at 192.168.0.200 and I was going to try to use the Laptop to re-configure this as well (to 192.168.1.201)

My plan was 
1. Give the Laptop a Static IP (say 192.168.0.XYZ)
2. Plug Laptop Ethernet into WGE101 (currently at 192.168.0.200)
3. Use the WGE101 GUI to change its IP to 192.168.1.200
4. Plug Laptop Ethernet into TiVo (currently at 192.168.0.100)
5. Use Laptop to telnet into TiVo and change its IP to 192.168.1.100
6. Revert Laptop back to non static IP


But:
1. How can I check if my wi-fi interface is eth1 (or whatever)?
2. I'd also need to change the IP of the WGE101 as well wouldn't I? As this is currently set at 192.168.0.200 and I was going to try to use the Laptop to re-configure this as well (to 192.168.1.201)

Sorry I modified my post in the meantime: reading your 1st post I see that you plug directly the cable in the device, so you don't need wi-fi configuration... as soon you have the static IP that IP is correct for both devices; to revert just reboot your machine...

---

### Post by CarlWalters on 2008-07-28
We must have been typing at the same time :)

I've read the modified post and that seems to make sense to me I'll give that a go this evening. Thanks!

---

