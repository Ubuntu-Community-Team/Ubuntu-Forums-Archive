---
title: "OpenVPN configuration with two eth adapters"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by espogian on 2015-04-14
Hi all,

I'm working on a Ubuntu 14.04 server with two eths adapters.
eth0 is configured on a router with internet access and a public IP address so currently I have an OpenVPN server which is listening to that, and all is working properly.
However, the server also has an eth1 adapter which I would like to connect to a local LAN (let's name it local-LAN).

What I want to achieve is the following:


[LIST=1]
[*]Clients from Internet should be able to open VPN sessions contacting the public IP address and hence going through eth0
[*]Successfully logged clients should be able to see the devices on the local-LAN which belongs to eth1
[/LIST]

I don't want devices on local-LAN to be able to go through my internet connection passing through the server's eth0.

Could you give me some suggestions?

---

### Post by michi1983 on 2015-04-14
So all your clients in your LAN won't have internet access, that is your goal?

Do you have your server setup with a window manager like Gnome or KDE or just command line?

---

### Post by espogian on 2015-04-14
> **michi1983 said:**
> So all your clients in your LAN won't have internet access, that is your goal?

Do you have your server setup with a window manager like Gnome or KDE or just command line?

Yes I don't want the clients on the local-LAN to be able to reach what is on the other side (eth0) including internet access.
And I'm currently on command-line.

---

### Post by michi1983 on 2015-04-14
Okay, this means you will have to handle this with your iptables firewall. 
Did you do anything with iptables so far?

Can you please post the output of ```
sudo iptables -L
```

---

### Post by espogian on 2015-04-14
> **michi1983 said:**
> Okay, this means you will have to handle this with your iptables firewall. 
Did you do anything with iptables so far?

Can you please post the output of ```
sudo iptables -L
```

At the moment I'm in a clean situation with the firewall.
Let's assume that:

eth0 is on 10.0.1.254/24 (the router has a 1:1 NAT with the public IP)
and eth1 is on 192.168.1.2/24

---

### Post by michi1983 on 2015-04-14
Well if you are sure about that, then here is what I found on the net which might work:
[http://www.gaggl.com/2013/04/openvpn-forward-all-client-traffic-through-tunnel-using-ufw/](http://www.gaggl.com/2013/04/openvpn-forward-all-client-traffic-through-tunnel-using-ufw/)

---

### Post by espogian on 2015-04-14
> **michi1983 said:**
> Well if you are sure about that, then here is what I found on the net which might work:
[http://www.gaggl.com/2013/04/openvpn-forward-all-client-traffic-through-tunnel-using-ufw/](http://www.gaggl.com/2013/04/openvpn-forward-all-client-traffic-through-tunnel-using-ufw/)

Thank you for the link, it seems that with this configuration I'm able to pass through the OpenVPN server.
I assume that I need to configure correctly my routing table, but I don't know how.
Do you think the information in your link are sufficient? I'm not sure

---

### Post by michi1983 on 2015-04-14
The information from my link will tell you how you can access your OpenVPN server from outside.
In addition you will have to forbid your eth1 to "talk" to eth0. You can find that info online as well, that shouldn't be a problem.
But something like ```
sudo ufw deny from 192.168.1.2/24
``` should work to block all traffic from your internal LAN.

---

