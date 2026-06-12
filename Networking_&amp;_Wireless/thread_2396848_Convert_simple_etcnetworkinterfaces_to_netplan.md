---
title: "Convert simple /etc/network/interfaces to netplan"
date: 2018-07-21
forum: Networking &amp; Wireless
---

### Post by ralph+shnelvar on 2018-07-21
I'm on Ubuntu 18.04.

I have this simple /etc/network/interfaces in Ubuntu 16.04:
 ```

  # This file describes the network interfaces available on your system

  # and how to activate them. For more information, see interfaces(5).
   
  source /etc/network/interfaces.d/*
   
  # The loopback network interface
  auto lo

  iface lo inet loopback
   
  # The primary network interface
  auto ens33[INDENT][FONT=&amp]iface ens33 inet dhcp
[/FONT][/INDENT]

```[FONT=&amp]
What would the equivalent netplan file look like?

Is there an automatic converter "out there"?
[/FONT]

---

### Post by wildmanne39 on 2018-07-21
Thread closed. Please do not post duplicates, it dilutes community effort.

---

