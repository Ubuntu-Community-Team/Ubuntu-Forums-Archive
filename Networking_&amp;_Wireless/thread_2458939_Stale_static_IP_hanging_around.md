---
title: "Stale static IP hanging around"
date: 2021-03-06
forum: Networking &amp; Wireless
---

### Post by kelly-gafford on 2021-03-06
I run a Ubuntu Server 20.04 on my home network. This server functions as my storage and streaming media server on my LAN. Recently I change my ISP and was sent a new router. The router does not allow me to configure the LAN IP so I ended up changing the static IP on the server. I have the IP set, however it's showing the old static IP and the new IP (See the attached file). I can't seem to clear this out. The netplan file has no reference to it and I've tried clearing out the DNS cache, but for some reason it doesn't want to give it up. I've also tried rebooting the server, but it still comes back with both IP's. I haven't done any aliasing on the NIC. I don't have any need for aliasing and the server responds to the new IP. The netplan didn't generate any error messages even with --debug. Any idea as to why it would hang onto a stale IP?

---

### Post by The Cog on 2021-03-07
The first thing I would do is to search all of /etc for the old address. Just guessing that 12 is your old subnet, try:
```
sudo grep -R '192\.168\.12\.20' /etc
```

---

