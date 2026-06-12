---
title: "ssh with ufw to allow for a single connection, when the client's ip changes"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by flucoe2 on 2016-01-06
I want to access my office desktop remotely. I first connect via vpn and then use ssh to turn the computer on, shh in, and turn it off. This, however, only works if I set ufw to allow all incoming connections. I want to allow a single connection, that between my laptop and the desktop. To do so, I changed ufw to deny incoming connections with the exception of a single IP, the one that my laptop reported when using ifconfig, while I was at my office, connected via wifi (no vpn as I was inside the network). When I try from my home, or any other place, I can't connect and, sure enough, ifconfig reports a different IP than the one I used to set the exception in ufw. So, how can I use ufw to allow for a single connection when the client's IP appears to be changing? Again, getting rid of the exception and setting ufw to "Allow" incoming connections does allow me to connect from every place from which I have tried, once I have connected via vpn. Thanks.

---

### Post by papibe on 2016-01-06
Hi flucoe2.

A few thoughts.

This would be the standard practice:
Firewall
[LIST]
[*]Allow all outcoming traffic, and
[*]close all incoming traffic except traffic over the ssh port.
[*]
[/LIST]
Then you configure ssh to:
[LIST]
[*]Not allow root connections over ssh,
[*]disable password connexions,
[*]allow only connexions using keys, and
[*]set a pair of ssh keys to be able to connect.
[*]
[/LIST]
Regarding your idea:

Note that unless you set up DCHP reservations, or static IPs at home (possible), and at work (hardly possible), there's no guaranty that those IP will remain the same over a certain period of time.

Extra security using a local/custom VPN:

You could setup a VPN server in your desktop at home. Then wherever your laptop is, it would first connect to the desktop over VPN, and then connect over ssh through the VPN tunnel. I've done this using [tinc VPN]("http://www.tinc-vpn.org/"). It is fairly easy to setup. You could use a VPS/cloud-server to bounce the connections, but you can do it without it if you forward ports on your router, and use a dynamic DNS service.

Hope this help. Let us know what you think, and if you have more questions.
Regards.

---

### Post by flucoe2 on 2016-01-07
Awesome, thanks! I followed your suggestions up to the point of setting up a VPN server at home. I'll have to think about how to do that. For now, I disabled password connections, allow connection only when using keys, and all incoming traffic is closed except for ssh.

Thanks for your help!

---

