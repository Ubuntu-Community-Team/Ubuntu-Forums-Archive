---
title: "multiple network interfaces, routing to interface with apache"
date: 2022-10-03
forum: Networking &amp; Wireless
---

### Post by curious877 on 2022-10-03
[SIZE=3][COLOR=#232629][FONT=-apple-system]ubuntu 22.04 . 2 virtual machines

[/FONT][/COLOR]
first vm has two private lan:

```

172.16.0.2
192.168.100.2

```

second vm has two private lan:

```

192.168.100.4
192.168.102.4

```

[COLOR=#232629][FONT=-apple-system]using netplan how can i redirect traffic from vm1 192.168.100.2 to vm2 192.168.102.4 ? as far i got i need to use address 192.168.100.4 ?

[/FONT][/COLOR][/SIZE][COLOR=#141414][FONT=&amp]vm1 yaml[/FONT][/COLOR]
```

[COLOR=#141414][FONT=&amp]network:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]  version: 2[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]  renderer: networkd[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]  ethernets:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]    eth1:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      dhcp4: true[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]    eth2:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      addresses:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      - 172.16.0.2/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]    eth3:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      addresses:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      - 192.168.100.2/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      routes:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      - to: 192.168.102.4/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]        via: 192.168.100.4/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]        on-link: true[/FONT][/COLOR]

```
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]vm2 yaml[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
```

[COLOR=#141414][FONT=&amp]---[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]network:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]  version: 2[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]  renderer: networkd[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]  ethernets:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]    eth1:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      addresses:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      - 192.168.100.4/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      routes:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      - to: 192.168.102.4/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]        via: 192.168.100.4/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]   eth2:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      addresses:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      - 192.168.102.4/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      routes:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]      - to: 192.168.100.2/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]        via: 192.168.102.4/24[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]

```

---

