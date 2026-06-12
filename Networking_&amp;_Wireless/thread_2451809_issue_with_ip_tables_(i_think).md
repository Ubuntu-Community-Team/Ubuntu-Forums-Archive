---
title: "issue with ip tables (i think)"
date: 2020-10-11
forum: Networking &amp; Wireless
---

### Post by mmeir0las on 2020-10-11
hello everyone

i would like to get some guidance concerning connection to a server that's behind a commercial vpn service, if you don't mind.

i am using ubuntu 20.04 desktop (where i have a media and a syncthing server installed), and which i need to access remotely from my android device.

when the vpn service on that ubuntu server is off, i can access the server fine over ssh (wireguard and openvpn).
once i enable the vpn service, wireguard connects but i am not able to log in over ssh, neither am i able to connect to the media and syncthing server GUIs. openvpn doesn't even establish a connection...

after a bit of googling it seems to be an issue with routing tables, but i am far from being an experienced linux user, and don't want to ruin everything that has been running good so far

i'd appreciate some help solving this

cheers guys

EDIT: i forgot to add that my router has of late ipv4 tables in the menu as well... maybe it would be easier to do it there..

---

### Post by TheFu on 2020-10-11
You can request that the VPN allow inbound connections. My provider has a setting for that, but I've never used it.  I don't have the entire network setup to use the VPN, only a few desktops and not by default.

The outbound VPN users are different from the inbound connections.  My router knows nothing about the outbound, but it does forward some ports for the inbound VPN connection. Most of the time, I'll use the 1194/udp connection, but some hotels are challenging and I have 443/tcp setup for openvpn on an IP.  I have a few public IPs, which is handy for needs like this.

When I need remote access into the LAN, I'll connect via the VPN server or use ssh/scp/sftp that I run to a different machine on the LAN. There are sftp clients for Android, but usually the openvpn client works easiest for me.

I've not gotten wireguard working across my systems yet.

---

### Post by mmeir0las on 2020-10-14
Thx a lot for your answer.

I might try asking the vpn provider if he allows inbound connections, tho that provider is not the one being used as a VPN server... Don't know if that is an issue.

I access the server through a normal OpenVPN/Wireguard Server. The commercial VPN i'm using just as a Client, as another layer of security since it has it's own Firewall. 

Still even with the VPN Firewall off, i can't access the server when the VPN Client is running.

I think it might have to do with IP routing tables or ports... I'll ask the VPN provider unless someone else has a clue...

Cheers guys

---

### Post by TheFu on 2020-10-14
I don't understand the networking you seek at all.  The descriptions appear to mention things that are completely unrelated and shouldn't be used together.  There should only be 1 VPN client and 1 VPN server. Doing more than that when not an expert is asking for problems.

---

### Post by SeijiSensei on 2020-10-15
Doesn't the server have an IP address within the VPN space when the VPN is active, and maybe a public IP address when it is not? When you connect over the VPN, are you pointing the ssh client at the server's VPN address?

---

