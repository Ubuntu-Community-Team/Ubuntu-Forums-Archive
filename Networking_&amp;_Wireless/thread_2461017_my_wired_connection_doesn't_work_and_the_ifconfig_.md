---
title: "my wired connection doesn't work and the ifconfig command doesn't work either"
date: 2021-04-22
forum: Networking &amp; Wireless
---

### Post by h2k52nj on 2021-04-22
[COLOR=#242729][FONT=Arial]Hello I am new to Ubuntu, I installed it following all the steps except in step 5 of the guide ([https://ubuntu.com/tutorials/install-ubuntu-desktop#5-prepare-to-install-ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-prepare-to-install-ubuntu)) where I did not allow me to check the first box, only the second . Everything else is fine until I enter the system and I have no internet connection when I go to settings it only shows me Network and bluethooth and in the network screen only vpn and network proxy appear I have seen several tutorials to solve the problem but in all of them wired appears in the network tab but it only shows me what I said additionally I have tried the ipconfig command but it shows me command "ifconfig" not found, but can be installed with sudo apt install net-tools and when I enter that command it says reading package lists ... done Building dependency tree reading state information ... done E: Unable to locate packege net-tools[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I appreciate help to solve my problem[/FONT][/COLOR]

---

### Post by Bashing-om on 2021-04-22
h2k52nj; Hello - Welcome to the Forum.

Networking:
what results from terminal command:
```

ping -c3 8.8.8.8

```

As to "ipconfig" it is depreciated (old docs) in favor of the "ip" suite:
```

ip link ls
ip address

```
To relate what the networking configuration is doing.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

