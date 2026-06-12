---
title: "Cant access server outside my network"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by allthegoodnamesaretaken on 2005-06-22
Im a newb to Linux and was able to set up all the software i needed to run a server but i dont know what to do to allow external computers to access my server. I set my Netgear WGT624 to forward TCP port 80 to my server yet i cant access it out of my network.

---

### Post by bunced on 2005-06-23
Make sure there is the correct hole punched in your firewall. I don't know how this is set up, but you need to have port 80 unblocked on the server and any other computers it passes through to get to the internet. One final thought - is Apache running whilst you are doing all this configuration?

---

