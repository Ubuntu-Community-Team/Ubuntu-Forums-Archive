---
title: "Socks5 Proxy Logging Discussion"
date: 2019-04-24
forum: Networking &amp; Wireless
---

### Post by dyous87 on 2019-04-24
I am using an Ubuntu 18.04 server as a Socks5 proxy and tunneling traffic through it by binding 127.0.0.1:10000 on my client devices. This allows all traffic from the clients to go through the Ubuntu server via an encrypted SSH tunnel similar to a VPN server. 

On the server I am using Tshark to log all proxy traffic. The issue is that I currently have no way to determine which client device the traffic originates from (Tshark shows the Ubuntu server as the source IP for all the traffic). I am trying to brainstorm the best way to attribute traffic going through the SSH tunnel back to the originating client devices. 

One thought that I had was to use a different network namespace for every user. That way I can have a unique SSH user account for every client device that logs into the Socks5 proxy and each of those connections would use a different "virtual IP address" on the server. Theoretically this should allow Tshark to capture a different source IP for every logged in user account/ client.

Does anyone know how this can be accomplished or have other ideas on how i can implement the above?

Thanks in advance!
David

---

### Post by slickymaster on 2019-04-24
Thread moved to **Networking & Wireless** for a better fit

---

