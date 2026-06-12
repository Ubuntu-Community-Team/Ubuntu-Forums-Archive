---
title: "Ubuntu doesn't ping router"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by dmglouis on 2006-10-17
My newly installed Ubuntu 6.06 doesn't connect to the internet. It connects via Ethernet to a router and currently all attempts to ping the router or any address for that matter fails and a "destination host unreachable" message comes in terminal. My Ethernet card gets dhcp and each time I restart it gets an ip address (192.168.2.132), but each time I do "sudo /etc/init.d/networking restart", it loses the IP address.
Can someone help?
Thanks,
Gerard

---

### Post by starsky on 2006-10-17
> **dmglouis said:**
> My newly installed Ubuntu 6.06 doesn't connect to the internet. It connects via Ethernet to a router and currently all attempts to ping the router or any address for that matter fails and a "destination host unreachable" message comes in terminal. My Ethernet card gets dhcp and each time I restart it gets an ip address (192.168.2.132), but each time I do "sudo /etc/init.d/networking restart", it loses the IP address.
Can someone help?
Thanks,
Gerard

Clean boot once and do this -

Check your /etc/resolv.conf and make sure that it points to your ISP's Primary and Secondary server and not to your router's IP ? On single system, disable the dnsmasq and resolvconf (if installed)

Make sure no firewalls are running, "iptables -L". install something more user friendly like shorewall or firestarter and use it to manipulate the firewall rules.

If it loses IP address address then stop the networking 
(sudo /etc/init.d/networking stop) and try this manually -

```

sudo dhclient3 <your_ethernet_device> (mine's eth1).
ifconfig <your_erhternet_device>

```

if it get's a lease from your modem, then it's ready for action. If not then it's something else.

I am really guessing since your post is minimal, that your /etc/resolv.conf is pointing to your modem IP address and not your ISP's nameservers.

---

### Post by dmglouis on 2006-10-18
Okay, I tried what you said but after I try dhclient eth0, it says:
```
No DHCPOFFERS received
No working leases in persistent database - sleeping
```
I know my router works because I'm connected to it through the computer I'm on right now. Does anyone know what the problem could be?

---

### Post by mips on 2006-10-18
post output of:

lspci -v
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf

Try a static ip configuration and see if it helps.
Disable IPv6 globally.

---

### Post by Iowan on 2006-10-18
> **dmglouis said:**
> 
I know my router works because I'm connected to it through the computer I'm on right now.
What IP address is assigned to the computer you're on right now? 
(What is the router IP address?)

---

