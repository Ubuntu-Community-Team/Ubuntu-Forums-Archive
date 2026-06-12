---
title: "OpenVPN Options error: You must define CA file"
date: 2014-04-11
forum: Networking &amp; Wireless
---

### Post by Sveinn_Atli_Diego on 2014-04-11
I'm setting up VPN from expressvpn.org, and I'm following this directions: [https://www.expressvpn.biz/tutorials/linux_openvpn_terminal](https://www.expressvpn.biz/tutorials/linux_openvpn_terminal)
I've installed openvpn using:
```

[COLOR=#000000][FONT=proxima-nova]sudo apt-get install -y openvpn
[/FONT][/COLOR]
```[B][COLOR=#000000][FONT=proxima-nova]
[/FONT][/COLOR][/B][COLOR=#000000][FONT=proxima-nova]and placed a .ovpn, .key and .crt files from expressvpn.biz in /etc/openvpn:
[/FONT][/COLOR]```
user@pegasus:/etc/openvpn$ ls
ca.crt      client.key                    my_expressvpn_israel_udp.ovpn  my_expressvpn_uk_-_isle_of_man_udp.ovpn  update-resolv-conf
client.crt  my_expressvpn_egypt_udp.ovpn  my_expressvpn_russia_udp.ovpn  ta.key

```[COLOR=#000000][FONT=proxima-nova]
But when I run openvpn I get this error:
[/FONT][/COLOR]```
user@pegasus:/etc/openvpn$ sudo openvpn my_expressvpn_israel_udp.ovpn 
Fri Apr 11 23:30:08 2014 DEPRECATED OPTION: --tls-remote, please update your configuration
Options error: You must define CA file (--ca) or CA path (--capath)

```[COLOR=#000000][FONT=proxima-nova]
Any ideas?[/FONT][/COLOR]
[COLOR=#000000][FONT=proxima-nova]
[/FONT][/COLOR]

---

