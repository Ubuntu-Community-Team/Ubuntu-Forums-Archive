---
title: "OpenVPN/iPredator tunnelling torrents but nothing else."
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by Ally_Wilson on 2013-09-22
So, I thought I'd share this with the community as it's something that has irked me for a couple of years.

You want to:
[LIST=1]
[*]Tunnel your torrent traffic over a VPN (OpenVPN-iPredator combo)
[*]You don't want non-torrent traffic using that VPN.
[*]You want your torrent daemon to stop/start with the VPN - so it doesn't use your normal interface.
[/LIST]

Over the years I've built up a setup as follows...

Router: Connecting my devices over ethernet and wifi (and the internet).
Server: Running XBMC & tvheadend, connected to iSCSI NAS, HDMI to TV, DVB-S2 & DVB-T (for freeview/freesat).
Desktop: Running nothing, used for browsing.
Laptop: Running nothing, used for browsing.

I wanted everything to be handled by my server, it was on all the time and quiet.

Previous torrent setup:
[LIST=1]
[*]Server connected to iPredator PPTP, all traffic routed down the PPP0 interface (default).
[*]cronjob checking if "ppp0" was up every minute, if not, disconnect transmission-daemon (my torrent client of choice), issue start command to ipredator PPTP client.
[*]cronjob checking if "ppp0" was up, if it was, issue startup command to transmission-daemon (couldn't think/be bothered checking if it was running already).
[/LIST]

This worked for me very well. I had a 1 minute period, potentially, whereby I was exposed to be a torrentor to the greater internet/my ISP if the PPP0 tunnel failed.

I had a local web interface running on the server to allow me to add/remove torrents and I had SSHFS to the download location.

I moved from 1 ISP to another, and suddenly I noticed my PPP0 tunnel was failing if the download bandwidth went above 2MB/s (I could not get greater than that speed on my old ISP), making it reconnect all the time - and increasingly putting me at risk by exposing my torrent traffic over my normal ISP connection (i.e. PPP0 disconnects every couple of minutes, and therefore torrents were using my normal connection more often - as I was bound to the 1 minute cronjobs I had setup).

I finally checked if iPredator allowed OpenVPN (it has said for ages it was going to implement it), and it did.

So, I switched to OpenVPN - infinitely better. I was seeing 5MB/s and no tunnel failures.
But, my cronjobs were still an inconvenience for me. They were still restricted to a 1 min value.

Additionally, I wanted to be able to connect over the internet to my server (port forwarded by my router), and it meant that incoming traffic was being routed *in* on eth0, but *out* on tun0 (this situation had occurred when using PPTP as well, but I was still annoyed by it).

I also wanted that connection over the internet to be encrypted, I'd previously just added a static route to my server as the client address I was coming from was always static (an amazon server), and only used for SSH access.

Nowadays, with my bigger bandwidth, I wanted to stream content, add torrents, SSH, etc. from my trusted clients whether locally or over the internet.

So, we come to todays setup...

Server has 2 VPNs setup:
[LIST=1]
[*]OpenVPN as a server
[*]OpenVPN as a client to iPredator
[/LIST]

OpenVPN has a server.conf with pretty basic settings:

```
mode servertls-server


local 192.168.1.64
port 1194
proto udp
dev tun


persist-key
persist-tun


ca ca.crt
cert mediaserver.crt
key mediaserver.key
dh dh2048.pem
tls-auth server.key 0


cipher BF-CBC
comp-lzo


server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
#push "redirect-gateway def1"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"


user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 6

```

I'm not going to go into all the details, there are better OpenVPN explanations.

Additionally, my ipredator *client* config (/etc/openvpn/ipredator.conf) has the following:

```
client
**dev tun100**
proto udp
remote pw.openvpn.ipredator.se 1194
resolv-retry infinite
nobind


auth-user-pass /etc/openvpn/ipredator/password.txt
auth-retry nointeract


ca /etc/openvpn/ipredator/IPredator.se.ca.crt


tls-client
tls-auth /etc/openvpn/ipredator/IPredator.se.ta.key
ns-cert-type server


**script-security 3 system**
**up /etc/openvpn/ipredator/up.sh**
**down /etc/openvpn/ipredator/down.sh**
**route-up "/sbin/ip route delete 0.0.0.0/1 dev tun100"**


keepalive 10 30
cipher AES-256-CBC
tls-cipher TLSv1:!ADH:!SSLv2:!NULL:!EXPORT:!DES:!LOW:!MEDIUM:@STRENGTH
persist-key
persist-tun
comp-lzo
tun-mtu 1500
mssfix
passtos
status openvpn-status-ipredator.log
verb 3



```

The important changes I made are highlighted in **bold** to show what I changed. My main aim here was to stop *all* traffic going down the iPredator VPN (/dev/tun100), I only wanted the torrent traffic (hence why I added a line to remove the default 0.0.0.0 route on the tun100 interface).

Which, although perhaps un-needed due to the binding to the interface, start and stop the daemon when ipredator starts/stops.

So, which torrent clients allowed binding to an interface and not just an IP address (iPredator uses DHCP, and you don't get the same address every time you connect). I found qbittorrent, which does allow this.

In the qBittorrent.conf file (located here: ~/.config/qBittorrent/qBittorrent.conf) *add* the following line, under the [Preferences] section: 

Connection\Interface=tun100

Remember that I use the interface tun100 for my iPredator-client setup (tun0 is used for my openvpn-server setup).

My up.sh and down.sh scripts issue: service qbittorrent-nox-daemon start/stop

At this point, when I start openvpn it starts both the local server.conf and the ipredator.conf. The former gets a /dev/tun0 interface to listen on, the latter get a /dev/tun100 interface to connect to iPredator, and deleted the default route it pulls down, on - and only 1 programme/daemon binds to /dev/tun100 (and nothing else - so even if the OpenVPN iPredator tunnel collapses, it won't use /dev/eth0).

Now all my internet/public OpenVPN clients can connect to my server (browse my content, etc) over a VPN, but all my bittorrent traffic goes over /dev/tun100 to iPredator.

Hope this helps someone else.

---

