---
title: "Setting up a Static IP"
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by Teethdude on 2014-08-17
Hello, as the title suggest, I am setting up a Static IP on the Server side.
Now, I was reading a guide [Here]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") but got stuck at this part:
```
[FONT=monospace]auto eth0[/FONT]
[FONT=monospace]iface eth0 inet static[/FONT]
[FONT=monospace]        address 192.168.1.100[/FONT]
[FONT=monospace]        netmask 255.255.255.0[/FONT]
[FONT=monospace]        network 192.168.1.0[/FONT]
[FONT=monospace]        broadcast 192.168.1.255[/FONT]
[FONT=monospace]        gateway 192.168.1.1[/FONT]
```
What I need is a way to find this information (The IPs, network, etc.). Thank you for your assistance.

---

### Post by oldfred on 2014-08-17
Is that your /etc/network/interfaces or the example in instructions?
 What does this show? if you post it block out the HWaddr for security reasons.
sudo ifconfig

If you are defaulting to 100 with DHCP, your router probably has reserved 50 or 100 addresses for DHCP. You cannot reuse any of those and must choose one outside of that range or any other fixed address assigned. You may just be able to use .20 instead of .100 and everything else should be the same.

Many new routers now let you configure the static address from the router. My new Comcast router uses all addresses for DHCP and I have to also configure it from router. Either way you need to review settings on router to see that nothing conflicts.

---

### Post by Teethdude on 2014-08-17
That's what is showed in the example. I know you are able to normally set the IP on the router, but at this time it's not a possibility. Only one person has the administrator rights to it, and it's not me. 
I have figured out the info, except for the one called "network".

---

### Post by oldfred on 2014-08-17
First three octets should be your network whether 168. or 10. which are the standard internal networks. And the last for network is always .0 as far as I know.

[http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html)

---

