---
title: "LAN Configuration"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by reaz on 2008-06-23
I am using ubuntu-8.04. I can configure LAN using network manager manual configuration when I run ubuntu from CD. But I cannot do this after I installed ubuntu. List of available networks remain inactive and so I cannot select any network. Enable Networking is ticked. :confused:

---

### Post by Webdawgz on 2008-06-23
To configure the Network card via X server: Click Systems --> Administration --> Network --> Unlock at the bottom right hand corner --> enter the admin password and change the ip settings.

---

### Post by gtdaqua on 2008-06-23
Or do it from the terminal yourself:

```

sudo nano /etc/network/interfaces

```

Enter the following: (change the values accordingly)

```

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

```

Once done, press Ctrl+W to save the file. Then press Ctrl+X to quit nano editor.

---

