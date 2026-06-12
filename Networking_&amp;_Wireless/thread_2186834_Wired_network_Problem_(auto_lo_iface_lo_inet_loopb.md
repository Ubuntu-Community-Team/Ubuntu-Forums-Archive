---
title: "Wired network Problem (auto lo iface lo inet loopback)"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by zanklob on 2013-11-09
[COLOR=#333333][FONT=lucida grande]Hi,[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]I have a dual partition in my laptop (Ubuntu 12.04 and windows 7).[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]After booting to windows 7 (after a long time) and then back to Ubuntu 12.04 for some reason I have problems with my internet access.[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]NOTE: The internet access still works fine when I boot in windows 7 again.[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]
I see the following when I run an ifconfig:
ifconfig
eth0 Link encap:Ethernet HWaddr 00:26:22:ee:d2:25 
inet6 addr: fe80::226:22ff:feee:d225/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0[/FONT][/COLOR]:  B | [COLOR=#333333][FONT=lucida grande]TX bytes:6005 (6.0 KB)

[/FONT][/COLOR][COLOR=#333333][FONT=lucida grande]lo Link encap:Local Loopback [/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]RX packets:915 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]TX packets:915 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]collisions:0 txqueuelen:0 [/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]RX bytes:68820 (68.8 KB) TX bytes:68820 (68.8 KB)


My /etc/networks/interfaces was[/FONT][/COLOR][COLOR=#333333][FONT=lucida grande]:
[/FONT][/COLOR]auto lo
iface lo inet loopback

and then I appended and made it:

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


But this didn't work either...


ls /sys/class/net is:
eth0 lo wlan0



Any ideas/suggestions?

---

### Post by zanklob on 2013-11-09
I also want to add that  my /etc/NetworkManager/nm-system-settings.conf is:

[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false

---

### Post by steeldriver on 2013-11-09
First of all, revert your changes to the /etc/network/interface file - they're not needed when you are using the desktop Network Manager and may even conflict with it.

Next I would try editing the connection (either from the GUI applet, or by running nm-connection-editor from a terminal) and disabling IPv6 by changing the IPv6 method to 'Ignore'.

If that doesn't work, post back with more info about your network hardware e.g. from

```
sudo lshw -C network -sanitize
```

in case there are any known driver issues

---

