---
title: "Ubuntu Server Not Booting After Changing DHCP Settings"
date: 2015-09-11
forum: Networking &amp; Wireless
---

### Post by Chris_Corbett on 2015-09-11
[COLOR=#111111][FONT=Ubuntu]I'm currently running an Ubuntu Server with 14.04LTS at home.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've recently had issues with the network and wanted to set the server to a static IP address internally. To do this I followed the guide linked [here]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When trying to remove the DHCP client it failed, but I thought this would not be an issue. However upon a reboot of the server it no longer fully boots. It boots as far as a screen showing various services running ok and some failing. The screen then goes blank and nothing.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It appears to be connected to the network at the IP address I want though as it is pingable.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Does anybody have an idea as to what the issue could be?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank You,[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Chris.[/FONT][/COLOR]

---

### Post by TheFu on 2015-09-11
That guide is out of date from 12.04 and later.

First - remove the lines:
```
network 192.168.1.0
broadcast 192.168.1.255
```

Make certain that 
```
iface eth0 inet dhcp 
```
has been removed - or is commented out.

Do not touch the resolv.conf, the dns-nameservers 192.168.1.1 line handles that.

With "server" installs (not desktop), I've never needed to do anything with DHCP configs.

---

### Post by Chris_Corbett on 2015-09-12
> **TheFu said:**
> That guide is out of date from 12.04 and later.

First - remove the lines:
```
network 192.168.1.0
broadcast 192.168.1.255
```

Make certain that 
```
iface eth0 inet dhcp 
```
has been removed - or is commented out.

Do not touch the resolv.conf, the dns-nameservers 192.168.1.1 line handles that.

With "server" installs (not desktop), I've never needed to do anything with DHCP configs.

Thank you very much that sorted it straight away.

---

