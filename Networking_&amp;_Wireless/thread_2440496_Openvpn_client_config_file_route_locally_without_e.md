---
title: "Openvpn client config file: route locally without external DNS"
date: 2020-04-11
forum: Networking &amp; Wireless
---

### Post by vellofrell on 2020-04-11
Hi, question on making my desktop client box on my OpenVPN subnet use only local DNS in my house router, with no DNS routing to external DNS provider that I have pre-configured in my VPN client profiles. 

My VPN server sits locally on 192.168.1.3. 

Line four of my client config files is: 
‘CUSTOM_DNS_ADDRESS@youdontcare.com’ ‘CUSTOM PORT NUMBER’

...so this is the DNS routing line in all my client config files. I have one machine in my home that I need on the VPN subnet at all times. For now it auto-starts at boot the VPN and gets on the network. But it is routing to the external DNS. When I have gone into to edit my VPN client config for this desk bog to '192.168.1.3' 'CUSTOM PORT NUMBER" then this desktop box has no connectivity at all...so there's something else going on here I am missing on. 

Wanted to ask about this here because the Openvpn.net forums haven't given much in the way of suggestions so far. 

Any tips guys and girls?

---

### Post by vellofrell on 2020-04-11
Okay, I guess adding this bit into the server's iptables is what allowed the local desk box to automatically raise the VPN subnet: 

```
[COLOR=#000000][FONT=Menlo]-A INPUT -s 192.168.1.2 -p udp -m state --state NEW -m udp --dport '[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]CUSTOM_PORT_#'[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] -j ACCEPT[/FONT][/COLOR]
```

into /etc/iptables/rules.v4 on the server. 

This now allows my desk box to have the client.conf OpenVPN profile to auto-raise the VPN subnet on all boots without going out to external DNS. 

```
[COLOR=#38B9C7][FONT=Menlo]# The hostname/IP and port of the server.[/FONT][/COLOR][COLOR=#38B9C7][FONT=Menlo]# You can have multiple remote entries[/FONT][/COLOR]
[COLOR=#38B9C7][FONT=Menlo]# to load balance between the servers.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]remote 192.168.1.3 'CUSTOM_PORT_#'[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]key-direction 1[/FONT][/COLOR]
```

---

