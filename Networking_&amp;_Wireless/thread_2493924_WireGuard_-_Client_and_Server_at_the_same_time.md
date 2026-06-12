---
title: "WireGuard - Client and Server at the same time"
date: 2023-12-29
forum: Networking &amp; Wireless
---

### Post by johnnydrama40 on 2023-12-29
Not even sure if this can be done 
My VPN provider is limiting WireGuard connections to 1, any IP is allowed but you only get single config

so I got VPS for boxing day and been messing with this for a bit

I am trying to connect to VPN from my VPS server, but at the same time have VPS act as a wireguard server and re-share my VPN connection

SO I have 
/etc/wireguard/wg0.conf acting as my server

```

[Interface]
Address = 10.7.0.1/24
PrivateKey = <private key>
ListenPort = 51820


# BEGIN_PEER JD
[Peer]
PublicKey = <public_key>
PresharedKey = <preshare_key>
AllowedIPs = 10.7.0.2/32
# END_PEER JD

```

and /etc/wireguard/wg-client.conf as my client where I entered information provided by VPN

```
PrivateKey = <private key provided by VPN>
Address = 10.2.72.50/32
DNS = 1.1.1.1
MTU = 1384


[Peer]
PublicKey = <Public key provided by VPN>
Endpoint = server:port
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25



```

if I bring wg0 up, I can connect fine I'm assigned IP address of the server

but as soon as I bring up wg-client, I can no longer access server via SSH, wireguard or any other service ..ping stops working as well

net.ipv4.ip_forward is set to 1 in /etc/sysctl.conf

can this be done, what am I missing?

---

### Post by TheFu on 2023-12-30
Seems like you are trying to get around the terms under which your VPN provider offers service ... and for very little reason.
If you have a VPS, just run your own wireguard there and setup as many client keys as you like yourself.  I don't see what paying someone else for VPN gets you.

Am I missing something?  Are you a super spy?  If you are, just use TOR with at least 3 intermediate nodes between you and the exit location.

---

### Post by johnnydrama40 on 2024-01-02
lol not even

netflix and fubo.tv sharing 

fubo.tv offers 10 max concurrent streams for home network
netflix allows 4 streams from home network


if I run my own wg server from webhosting IP, I can not set home for fubo


anyways, I managed to figure this one out

---

### Post by TheFu on 2024-01-02
Seems like you are trying to get around the terms under which your streaming services are provided.  Are you reselling access or what?
Do you have 9 dependent kids that all live in different houses?

---

### Post by mudakosarma24 on 2024-01-02
...

---

