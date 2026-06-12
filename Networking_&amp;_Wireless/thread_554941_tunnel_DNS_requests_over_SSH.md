---
title: "tunnel DNS requests over SSH"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by band-aid on 2007-09-19
I have set up an old machine to act as a SSH/file server. My goal is to be able to tunnel my http traffic at remote locations over this SSH connection. The traffic tunnels just fine using ssh -D <port> but for some reason (even though I am using SOCKS5) I am unable to get my DNS requests to be made remotely. This is a problem because even though logs or sniffing will not show the contents of my traffic, it will show the dns request for whatever site I happen to be visiting.




Also, what log would ssh traffic like this be stored in, if at all.

Thanks for the help.

---

