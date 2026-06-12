---
title: "Help with Wireguard &amp; Tailscale"
date: 2022-05-30
forum: Networking &amp; Wireless
---

### Post by paul921 on 2022-05-30
[COLOR=#141414][FONT=&quot]Sitting with a bit of a headache - maybe someone here can point me in the right direction.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I have an Oracle VPS instance in Sydney, on which I have installed TVHeadend, this connects to another VPS in Auckland via Wireguard.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I also use Tailscale to talk to my other VPS instances, and so that I can connect to them from my home network, and when I am on the go, and also as another form of security. For example I don't need to port forward, and have hackers trying to access my content, I just need to install Tailscale, and then all services which I would usually have to open ports for are there.[/FONT][/COLOR]


[COLOR=#141414][FONT=&quot]The ARM instance is superior, but I need the NZ VPS so that I can pick up TVNZ with the geoblocking, and there minimal latency between the two countries.[/FONT][/COLOR]


[COLOR=#141414][FONT=&quot]After struggling with Wireguard, I managed to get the two talking, and Sydney successfully connects through NZ, and can confirm if I connect via SSH, and tunnel the TVHeadend ports, I can stream the NZ geoblocked content perfectly here in Cape Town.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]However whenever I connect to Wireguard on my Sydney instance, Tailscale stops working, I can't ping my Tailscale network addresses. Doing so gives me a "Time to live exceeded" error. Pinging the Tailscale address on my Windows machine, the address times out When Wireguard is disconnected the ping responds as it should.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]On my Windows laptop, in Cape Town I did a test connection to my Wireguard server in Auckland, ensured my allowedips were "0.0.0.0/1, 128.0.0.0/1, ::/1, 8000::/1", and I was able to connect to both my LAN, and tailscale devices from my laptop just fine.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I have specified routes in my wg0.conf file, without these Putty would disconnect as soon as I brought up the wg0 connection. - I also set up another VCN in Oracle cloud, as I didn't want oracle's private 10.0.x.x.x.x range interfering with Wireguard's address range which is also 10.x.x.x.x.x. Changing it on Wireguard proved to be too much of a headache, with the connection failing.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Here's the custom rooting[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]PostUp = ip route add table 200 default via 192.168.0.1[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]PostUp = ip rule add table 200 from 192.168.12.73[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]PreDown = ip rule delete table 200 from 192.168.12.73[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]PreDown = ip route delete table 200 default via 192.168.0.1[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I tried using the same "0.0.0.0/1, 128.0.0.0/1, ::/1, 8000::/1 settings on my Sydney VPS, which hopefully would have let LAN traffic through, it wouldn't even load internet traffic, and I would have no SSH or anything.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]How difficult can it be to get Tailscale working over Wireguard on Ubuntu? With Windows it can be down in a few clicks.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I just have a feeling the problem is probably something simple.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Just in case it's easier for solution, here's my Network interface addresses[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]IPv4 address for enp0s3: 192.168.12.73[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]IPv4 address for tailscale0: 100.86.133.32[/FONT][/COLOR]

---

### Post by TheFu on 2022-05-31
You have a bunch of fairly unique tools being used. I suspect you'll get better help on forums for those specific tools than here.
My only comment is to be 100% certain that your subnets (real and otherwise) are unique to everywhere in the connection chain.  Using 192.168.0.0/24 is almost always a failure point. That subnet is used far too often.  You'd be better off using a random 10.100.61.0/24 network.

I've vaguely looked at TVHeadend and decided that avoiding it was in my best interest. I use HDHR network turners with DLNA, which avoids any need for TVHeadend.  Don't know what tailscale is. Never needed it with my VPN setup. Also, I disable IPv6 on all my systems and actively block it on all routers.
When I'm traveling, my VPN connection provides a LAN IP on the same subnet as Jellyfin and the HDHR devices.  I have used a simple SOCKS5 proxy over ssh when remote to use the jellyfin webapp to stream stuff too.  I seldom watch live content, so playback of already recorded content is possible in many different ways.

---

