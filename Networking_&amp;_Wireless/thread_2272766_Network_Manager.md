---
title: "Network Manager"
date: 2015-04-08
forum: Networking &amp; Wireless
---

### Post by ylafont on 2015-04-08
I was under the impression that  Network Manager does not manage the interface card if

1) there are entries in /etc/network/interface 

and

2) /etc/NetworkManager/NetworkManager.conf contains

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


However when in place a static IP in /etc/network/interface like this

iface eth0 inet static
  address 192.168.1.3
  netmask 255.255.255.0
  gateway 192.168.1.1
  network 192.168.1.0
  broadcast 192.168.1.255
  dns-nameservers 8.8.8.8 8.8.4.4


The interface never comes up.


Did i miss something?


or is there an easy way of placing a static IP with the nmcli command?

---

### Post by michi1983 on 2015-04-08
Try this instead:

```

auto eth0
[COLOR=#000000]iface eth0 inet static[/COLOR]
[COLOR=#000000]address 192.168.1.3[/COLOR]
[COLOR=#000000]netmask 255.255.255.0[/COLOR]
[COLOR=#000000]gateway 192.168.1.1[/COLOR]
[COLOR=#000000]network 192.168.1.0[/COLOR]
[COLOR=#000000]broadcast 192.168.1.255[/COLOR]
[COLOR=#000000]dns-nameservers 8.8.8.8 8.8.4.4[/COLOR]

```

and after that type ```
sudo /etc/init.d/networking restart
```

---

### Post by ylafont on 2015-04-08
[[COLOR=#000000]michi1983[/COLOR]]("http://ubuntuforums.org/member.php?u=1842111")

you were correct!    i failed to see that 


auto eth0  was missing!

Thank  you for the quick reply.

---

### Post by michi1983 on 2015-04-08
you are welcome!

please mark the post as solved if you don't mind.

---

