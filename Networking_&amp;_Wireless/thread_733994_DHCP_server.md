---
title: "DHCP server"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by William S on 2008-03-24
Hello! 
I've been looking to run a DHCP server, but the problem is that the DHCP server never works. I have a normal Linksys router where I get my IP adresses so is there a way to set up the conf file to make it work with that?

---

### Post by drdrewdown on 2008-03-24
you dont want to run dual dhcp servers on the same LAN

you would also need at least 2 NIC's(network cards) in your dhcp server machine.  one to accept the WAN, the other to broadcast dhcp to your switched lan.  your clients would receive their ip's from the 2nd nic on your server.

cheers

---

### Post by William S on 2008-03-24
So I am therefore not able to perfom a  network boo for examplet with just one NIC?

---

### Post by drdrewdown on 2008-03-24
i would recommend dual network cards to do what you're wanting to do.

---

### Post by chilinski on 2008-03-24
I'm not entirely sure I understand what you're trying to do. Do you want to keep your existing router or replace it with the new machine? If you want to get rid of your router and have the new machine do routing and dhcp, you'll need two network cards as stated. 

If all you want to do is move your dhcp services from your router to the new machine, you don't need two cards. You just need to shut off dhcp on the router and start it on the new machine.

The Linksys router is just as configurable as any other DHCP server (you can set the scope of addresses, exclude addresses, etc.). So I don't see what you would gain by moving the DHCP services off the router.

---

