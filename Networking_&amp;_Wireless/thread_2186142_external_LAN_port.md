---
title: "external LAN port"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by meetjames.antony on 2013-11-06
how to configure the external LAN port in Ubuntu 10.10 or 13.10..
plz help me

---

### Post by houstonbofh on 2013-11-06
These may not apply, but without more information we can not help you...

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)
[https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

---

### Post by meetjames.antony on 2013-11-09
[COLOR=#000000]Product    : Gigabit PCI Adapter[/COLOR]
[COLOR=#000000]Model No  : DG-NI1000T[/COLOR]
[COLOR=#000000]OS            : UBUNTU 10.10[/COLOR]
[COLOR=#000000]Hardware :  External  LAN PORT
 
They gave one src folder also  [/COLOR]

---

### Post by tgalati4 on 2013-11-09
Open a terminal, post the output of:

```
lspci | grep Ethernet
```

and 

```
ifconfig
```

---

### Post by gordintoronto on 2013-11-10
10.10 expired more than two years ago, so it's not a useful environment for troubleshooting.

It's not obvious what you want to do. Generally, there is no need to "configure" an Ethernet port.

---

