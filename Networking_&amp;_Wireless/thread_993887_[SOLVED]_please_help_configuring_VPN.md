---
title: "[SOLVED] please help configuring VPN"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by dipeshmehta on 2008-11-26
Hello,

We have two networks located at different places. Both networks are windows networks with windows 2003 server.  At both places I have setup Ubuntu 8.04 server.  I want to connect these networks by means of VPN through ubuntu server and not windows server.

Please suggest me how to do this.

Thanks in advance.

Dipesh

---

### Post by SpaceTeddy on 2008-11-26
maybe this helps ?

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=752127[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127")

i'd go for part 1 since that is probably more what you want... part 2 is a real lot of network reconfiguration. 
Also, you're in for some heavy configuration and head bashing against a (random) wall if you have not done this before... I don't mean to discourage, i just want to point out that this can be very frustrating. If questions arise, just ask.

---

### Post by dipeshmehta on 2008-11-27
Hello,

I have setup OpenVPN at one of the location on ubuntu server.  Now I want to connect to my VPN from windows clients, please tell me how to do I?

Is there any client application for OpenVPN to download or may I use windows built-in vpn client?

Dipesh

---

### Post by SpaceTeddy on 2008-11-27
thread hijacking... mhm... not really nice.

Anyway, the build-in vpn client for windows does not work with OpenVPN(that is a vpn based on ipsec if i am not mistaken) because it uses only SSL/TLS connections. You will need an extra client for that. The best place to start with that is here [[COLOR="Blue"]http://www.openvpn.se/[/COLOR]]("http://www.openvpn.se/")

---

### Post by dipeshmehta on 2008-11-29
Hi,

I am able to connect to my OpenVPN server from remote client.  I am able to work in full on server, but I can not see other networked computers/devices on server side. 

I know, there is some to be done in route, iptables etc., but I don't know how.

Please help me configuring this.

Dipesh

---

### Post by update_manager on 2008-11-29
> **dipeshmehta said:**
> Hello,

We have two networks located at different places. Both networks are windows networks with windows 2003 server.  At both places I have setup Ubuntu 8.04 server.  I want to connect these networks by means of VPN through ubuntu server and not windows server.

Please suggest me how to do this.

Thanks in advance.

Dipesh

The simplest way is to use SSH tunnels.

An example would be that network #1 has an Ubuntu Server running SSH. Clients connect to that SSH server starting up a SOCKS proxy (for an example: [http://www.jonlee.ca/wp-content/uploads/2007/04/putty-ssh-tunnel-config.gif](http://www.jonlee.ca/wp-content/uploads/2007/04/putty-ssh-tunnel-config.gif)). These clients will be able to browse http/https sites on the other network. You might want to use Squid or another proxy to take the load off of the clients. SMB also can be tunneled (another example [http://www.security-hacks.com/2007/05/18/tunneling-smb-over-ssh-secure-file-sharing](http://www.security-hacks.com/2007/05/18/tunneling-smb-over-ssh-secure-file-sharing)).

The biggest downside of this setup is that every client needs to be running an SSH client.

---

