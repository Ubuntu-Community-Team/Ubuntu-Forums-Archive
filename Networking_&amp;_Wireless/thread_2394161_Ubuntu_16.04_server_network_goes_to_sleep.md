---
title: "Ubuntu 16.04 server network goes to sleep"
date: 2018-06-13
forum: Networking &amp; Wireless
---

### Post by drwhoit03 on 2018-06-13
[COLOR=#242729][FONT=Arial]I have a linux server (Ubuntu 16.04) which I access through vSphere client. I have defined static interface looking like this:[/FONT][/COLOR]
auto ens160
iface ens160 inet static
  address 91.185.215.206
  netmask 255.255.255.224
  gateway 91.185.215.193
  dns-nameservers 8.8.8.8
[COLOR=#242729][FONT=Arial]I've also installed NetworkManager and set managed to true, since I am using static configuration.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The problem is, that after approximately 40 seconds after boot (or after network-manager restart), I loose connection to and from the server (I determine that with ping from a third server to this one).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I then again recover the connection either by initiating ping from this very server to, for example google, or by restarting network-manager. As if network went to sleep and needs to be 'waken up' by something (in this case ping to google).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But the thing is that even ping to google goes stale after approximately 40 seconds.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any ideas?[/FONT][/COLOR]

---

### Post by rsteinmetz70112 on 2018-06-15
How did you define the static interface? Through Network Manager or through /etc/network/interfaces?

---

