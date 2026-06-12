---
title: "Network Manager With Static IPs"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by ihavenoideax2 on 2008-05-20
I was wondering if anyone else had this problem. I use static ips in my house, but still have a dhcp server. I just upgraded to 8.04 on my laptop from 7.10. So far its alot better that 7.10 because i dont have to mess with things, it just works. Anyway, i wanted to make 2 profiles, one for my house and one for everywhere else. I want my home profile to have the wired network a static ip and nothing with wireless. Than the other i want to have both in roaming mode. So i did that, but for some reason my home profile when its applied, it doesnt actually give it an ip address. I figured out if i run ```
sudo ifdown eth0; sudo ifup eth0
``` it somehow gets the ip address and works beautify. As soon as i switch around profiles again, roaming works fine, but switching back to the home profile causes it to do the same thing as before and i have to run the command again.

Anyone know what im talking about?

Also i think the problem might be in the interfaces file. I think network manager is adding things in the wrong order.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet static
address 192.168.10.6
netmask 255.255.255.0
gateway 192.168.10.254

auto eth0

```

If im not mistaken, auto eth0 should be right over iface eth0. Im at a loss because i need something simple to switch between profiles because i constantly move around with my laptop and dont feel like editing the interfaces file every time.

---

### Post by ilrudie on 2008-05-20
It sounds to me like you have set up IP address reservations on your home router.  Is this correct?  If so your router should look at the MAC address of your NIC and give it the same IP without setting up a static IP on your PC.

---

### Post by ihavenoideax2 on 2008-05-20
I dont have my router giving reserved ip addresses. Nor do i have that option. It doesnt seem to be the router at all but a configuration on the laptop. Also the ip is part of my static addresses under my dhcp range. I have almost all my other machines on the network with static ips.

---

### Post by ilrudie on 2008-05-20
I don't think auto eth0 needs to be above the iface eth0.  I had a similar issue with having to bounce interfaces to get my static IP to work.  The easy solution for me was to just use DHCP and reserver the IP address for my PC.  If that is not an option for your router's current firmware you can always check out dd-wrt to see if it supports your router.  It will unlock tons of functionality.

---

### Post by ihavenoideax2 on 2008-05-20
I would but im using a fon. I used to use a smoothwall router but i needed to cut power usage. I just wish i could figure this out. Does anyone have an idea about this?

---

