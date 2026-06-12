---
title: "Routing"
date: 2016-05-17
forum: Networking &amp; Wireless
---

### Post by ramicio on 2016-05-17
192.168.1.0 is my network. My Ubuntu server is 192.168.1.2 (eth0). The same server is also connected to 192.168.2.0 with eth1 (192.168.2.242), JUST for SMB traffic. That works fine. I want to be able to access the 192.168.2.0 network (really only port 8443 on 192.168.2.111) from the 192.168.1.0 network.

On my DD-WRT router I tried adding a route like:

Destination LAN NET: 192.168.2.0
Mask: 255.255.255.0
Gateway: 192.168.1.2

Then on the Ubuntu machine I tried a bunch of different routes.
route add -net 192.168.2.0 netmask 255.255.255.0 dev eth0
route add -net 192.168.2.0 netmask 255.255.255.0 dev eth1
route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.2.1

Nothing seems to work. I seem to be chasing my own tail here. Any help would be appreciated.

---

### Post by SeijiSensei on 2016-05-17
Did you enable packet forwarding in /etc/sysctl.conf?  You need to remove the hash mark from "net.ipv4.ip_forward" in that file and reboot.  Ubuntu and most other distros these days disable forwarding of packets between interfaces by default as a security precaution.  You shouldn't need to add any routes manually since Linux will automatically assign them based on the interface addresses.

Also the 192.168.2.111 box needs to know where to send traffic for 192.168.1.0/24.  Is the default gateway on 192.168.2.111 the Linux box at 192.168.2.242?  If it has a different default gateway, that machine would need a static route for the 192.168.1.0/24 network:

```
ip route add 192.168.1.0/24 via 192.168.2.242
```

---

### Post by ramicio on 2016-05-17
Yep. It's been enabled and rebooted. The second network has its own internet access, and their gateway is 192.168.2.1.

---

### Post by ramicio on 2016-05-17
Wow. That works now. Awesome! Thank you very much. I wasn't thinking at all about the other end of things. Too bad I can't add a static route to the Comcast modem on the other network without calling up Comcast.

---

