---
title: "[Wireguard] how to connect home vpn server to ProtonVPN?"
date: 2023-12-26
forum: Networking &amp; Wireless
---

### Post by jatrick29 on 2023-12-26
I apologize if this isn't the place to ask.

I am quite a noob with networking, and especially wireguard, so if my post is too vague then please let me know. However I realize that my wording is incorrect since with wireguard there is no such thing as a "server" and "client" but the terms make it easier to get my point across.

I currently have a wireguard server so I can connect to my home network remotely, but I also want the same computer that the server is configured on to be connected to protonvpn. My current situation is that both work just fine, but not together. When both are enabled, I can connect to my wireguard server but I do not receive any internet connection at all. I can't even connect to devices on my LAN. I have to disable the protonvpn connection for it to work.

```
--- wg0.conf ---

[Interface]
Address = 10.0.0.1/24
PostUp = iptables -A FORWARD -i %i -j ACCEPT
PostUp = iptables -t nat -A POSTROUTING -o enp8s0 -j MASQUERADE
PostDown = iptables -D FORWARD -i %i -j ACCEPT
PostDown = iptables -t nat -D POSTROUTING -o enp8s0 -j MASQUERADE
ListenPort = 51820
PrivateKey = XXXXXXXXXX

[Peer] # android client
PublicKey = XXXXXXXXXX
AllowedIPs = 10.0.0.5/24
Endpoint = client-ip:53161

--- protonvpn.conf ---

[Interface]
PrivateKey = XXXXXXXXXX
Address = 10.2.0.2/32
DNS = 10.2.0.1

[Peer] # protonvpn server
PublicKey = XXXXXXXXXX
AllowedIPs = 0.0.0.0/0
Endpoint = server-ip:51820

--- android client config ---

[Interface]
PrivateKey = XXXXXXXXXX
Address = 10.0.0.5/24
DNS = 1.1.1.1, 1.0.0.1

[Peer] # my home server (wg0)
PublicKey = XXXXXXXXXX
AllowedIPs = 0.0.0.0/0
Endpoint = server-ip:51820
```

as you can see I already have two separate interfaces, one to allow my android client to connect to my home server, and one for the home server to connect to protonvpn. I have spent all day looking for solutions online and have found similar issues, but have unsuccessfully followed any of them. Perhaps I need the explanations to be dumbed down even more.

also I do not require that my android client accesses the internet through protonvpn. that would be neat but as I understand it is a lot harder to do that. so simply being able to access devices on my home network and being able to access the internet is fine.

---

### Post by #&amp;thj^% on 2023-12-26
Multi Hop will be needed by one of those you show.
I've not used proton so I'm unsure if it is possible.

---

