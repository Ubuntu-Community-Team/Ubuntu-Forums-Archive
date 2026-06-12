---
title: "Problem with wireguard and Ubuntu server"
date: 2023-09-16
forum: Networking &amp; Wireless
---

### Post by viciud on 2023-09-16
[COLOR=#212529][FONT=-apple-system]I have a VPS Ubuntu server on AWS on which I run a Wireguard client, [/FONT][/COLOR][COLOR=#1C1C1C][FONT=&quot]while my Wireguard server is in my home router with Open WRT firmware[/FONT][/COLOR][COLOR=#212529][FONT=-apple-system]. The server works correctly because I tried to connect remotely with various clients including Android, Windows and Kali and the internet connection was correctly routed to my home router, thus allowing me to use its public IP even from remote clients, running a speedtest I see that on these clients the upload and download speed is 20 mbps and that's ok for me. On the Ubuntu VPS, however, something is wrong, because Wireguard doesn't work well, traffic isn't routed correctly on wireguard, even if ssh from another client connected to the same VPN works, if I run wget to see my public IP I can see that of the home router but if for example I run speedtest-cli as download speed I get 0 mbit/s while in upload 6 mbit/s same problem if I run an apt-get update I get 0% [Waiting for headers]. I think it's a routing problem that unfortunately I don't know how to solve, I searched on the web but I didn't find anyone with a similar problem. This is the configuration as a Wireguard client on the Ubuntu Server VPS:[/FONT][/COLOR]
```

[COLOR=#212529][FONT=-apple-system][Interface][/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system]Address = 10.10.10.3/32[/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system]PrivateKey = (My private key)[/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system]DNS = 8.8.8.8[/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system]ListenPort = 51820[/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system][Peer][/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system]PublicKey = (router wireguard Public Key)[/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system]AllowedIPs = 0.0.0.0/0[/FONT][/COLOR]
[COLOR=#212529][FONT=-apple-system]Endpoint = (Public IP homenetwork):51820[/FONT][/COLOR][COLOR=#212529][FONT=-apple-system]
[/FONT][/COLOR]
```[COLOR=#212529][FONT=-apple-system]
Thanks, any help is welcome.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-09-16
Not sure i can help, but you can watch what's happening with:
```
sudo watch wg show

```
Looks like to me a routeing problem as well,(Mine allowed ips: ::/0, 0.0.0.0/0 )there is a GUI browser based to help with that: [https://github.com/vx3r/wg-gen-web](https://github.com/vx3r/wg-gen-web)

---

