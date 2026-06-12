---
title: "Opening Ports for server"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by Madmoose on 2007-03-21
Trying to start a scorched 3D server, but a lot of my game ports are closed. Can anyone tell me how to open ports 27270 TCP and 27271 UDP  to be accessible externally. I also need game port 7845 TCP/UDP, and 80 TCP.

Thanks

---

### Post by bloodniece on 2007-03-22
Madmoose,

Unless you are using iptables or Firestarter, all ports are open on an Ubuntu server.  I would look at, possibly, your router that is connected to your DSL/Cable modem.  Most routers allow you to forward ports to local IP addresses.  Just be sure to set your Ubuntu server to a static IP to ensure that the router always forwards the ports to that computer.

---

### Post by Madmoose on 2007-03-23
As much as it shames me to say so, I don't have a router.  I do have firestarter installed, but it doesn't seem to be running. Unless it runs in the background without needing to have it up.

---

