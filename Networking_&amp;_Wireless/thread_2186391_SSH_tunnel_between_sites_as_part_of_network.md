---
title: "SSH tunnel between sites as part of network?"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by pelle-masendata on 2013-11-07
Hi,
I wonder if it possible to use two Linux servers (I usually use Ubuntu) to setup a SSH tunnel between them and have network traffic go through them? I want the servers just to forward traffic inside the tunnel to next building and I wish to have them in same IP address space. I hope the servers can be completely transparent to other equipment.

Some explanation: 
- We have a office in one building with clients and servers.
- In another building we have our backup system.
- We're not sure that nobody else can look at the traffic in the network between the buildings.

I have looked at some VPN solutions but the cost are a little bit high to get high througput. We wish a speed of near 1Gbps.
I have made a simple sketch of the networks. The red line are the connection between the buildings.
[IMG]http://www.masendata.com/images/Sketch001.jpg[/IMG]

---

### Post by TheFu on 2013-11-07
ssh tunnels are for specific ports and best for quick needs, not a corp-to-corp permanent connection. Sure, using ssh is quick and works, but tcp has overhead that most people would like to avoid and there are specific tools for this.

If you need all traffic between 2 locations to be encrypted, then use a VPN like OpenVPN. Many routers will support this so that end-users do not need to know anything about the tunnels. It "just works."  Also, real VPNs use udp, which has much lower overhead.

If you are lazy and have money, then you can purchase small-business routers with VPNs built-in.  I know that some Zyxel models have this.  pfSense and dd-wrt can do it too ... using openvpn means you are device independent, which might be very important.

---

### Post by Lars Noodén on 2013-11-07
You can use SSH to make your own VPN.  An outline of the process is here:

[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

You'll have to read up on it to see how it compares to OpenVPN for speed and such, but it's not complex.  Just make a tunnel and adjust the routing tables.  You'll need root access on both ends for that.

Edit: better URL

---

### Post by pelle-masendata on 2013-11-07
Thanks Lars, I will check that link. I will be back with result.

To use some cheap firewall does not work because I need high throughput and often you get 3-20Mbps VPN pass through in cheap filrewalls.

---

### Post by Lars Noodén on 2013-11-07
I've found a more detailed description, oriented towards Ubuntu specifically:

[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

YMMV

Still in the process of trying it.

---

### Post by SeijiSensei on 2013-11-07
Setting up a [static-key OpenVPN tunnel]("http://openvpn.net/static.html") is by far the simplest method.

---

