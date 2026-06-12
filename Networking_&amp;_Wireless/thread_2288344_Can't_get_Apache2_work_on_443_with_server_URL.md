---
title: "Can't get Apache2 work on 443 with server URL"
date: 2015-07-26
forum: Networking &amp; Wireless
---

### Post by espogian on 2015-07-26
Hi, I've configured Apache2 on my machine with a self-signed certificate and the HTTPS is correctly working only if I use the local IP of the server.
I have also configured a dynamic DNS with no-ip to reach my server when I'm outside (and the DDNS is correctly working since I can remotely SSH the server, and my router is configured to forward all ports to my server).
I would like to see my web-page when i input myddnsaddress.com in the browser, but it is not working with both http and https.
What could be the problem?
Also, which would be the simplest way to redirect http request to https?

):P

---

### Post by espogian on 2015-07-26
Sorry guys, this was an issue caused by the configuration of my router that was incorrect forwarding the port 443 to another machine

---

