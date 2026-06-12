---
title: "How can I set the ssh without public ip?"
date: 2023-02-27
forum: Networking &amp; Wireless
---

### Post by allsolution on 2023-02-27
I have ubuntu server with ssh configured. But I don't have a public ip. Public ip is used for  firewall. Can I configure NAT with custom port for ssh something like this 143.0.1.21:90443?


Note: I have 143.0.1.21 public ip but it used for firewall.


How can I ssh from outside to ubuntu server? 
my ubuntu server's lan ip is 192.168.1.153
Can I set NAT 143.0.1.21:90443 to 192.168.1.153?

---

### Post by TheFu on 2023-02-27
a) 90443 isn't a valid port. There are 64K ports, not 90K.
b) Most routers allow forwarding a port from the WAN interface to a specific, static, LAN, IP.  Don't have your LAN on 192.168.1.x/24.  This is too commonly used and when you outgrow just ssh, you'll wish you'd made your LAN subnet something less used, say 10.33.10.9/24 instead.  Fix it now.

So .... 143.0.1.21:62022/tcp ----> 10.33.10.9:22/tcp

If you do this, you can test internal and external connections using 2 different target IPs.

You'll need to allow the firewall on port 62022 inbound. If you can, restrict that to only the public internet locations/IPs where you know you will be.  Block 99.999% of the world from access.  Also, never use passwords for authentication, only ssh-keys or ssh-certs.  Preferably ellipical-curve PKI or at least 4Kb RSA keys. Anything shorter isn't considered secure anymore.  You can allow password authentication from your LAN, if you like, but definitely NOT from the internet.

Install a brute force protection tool, because not using port 22/tcp isn't sufficient. Within about 5 minutes, the world will know about your ssh server and the attacks will start.  On port 22, there will be 10,000s of attacks daily.  On other ports, it will be much less, but still exist. I see thousands daily  from places known to be nasty on the internet.  There attacks appear to come from will be different based on where you are in the world.  Local laws will usually prevent people in the same country attacking your system, but places that don't have strong ties to your govt won't care and will waste bandwidth with attacks. Some countries seem to encourage college students in this regard.

---

### Post by allsolution on 2023-03-02
Thank you mate. Almost solved solution. Successfully configured NAT with default port 22. I couldn't change the port. Or should I change default port on Ubuntu and Firewall too?

---

### Post by TheFu on 2023-03-02
> **allsolution said:**
> Thank you mate. Almost solved solution. Successfully configured NAT with default port 22. I couldn't change the port. Or should I change default port on Ubuntu and Firewall too?

What you should do is completely up to you. I've already made suggestions that I think are smart.  It is your network and your risk to accept, not mine.

---

