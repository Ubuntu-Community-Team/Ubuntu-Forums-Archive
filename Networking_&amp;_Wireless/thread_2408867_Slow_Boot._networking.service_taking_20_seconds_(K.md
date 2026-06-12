---
title: "Slow Boot. networking.service taking 20 seconds (KVM Hypervisor)"
date: 2018-12-24
forum: Networking &amp; Wireless
---

### Post by neil-polarnight on 2018-12-24
Hello,

On running: systemd-analyze blame -> networking.service
         ```
22.613s networking.service
```

On running sudo nano /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto br1
iface br1 inet dhcp
   bridge_ports enp0s25
   bridge_stp on
   bridge_fd 0.0
```


I have a KVM Hypervisor that works perfectly. It's my personal primary home machine.

Any idea how to speed this up? Thanks

---

### Post by praseodym on 2018-12-24
Let's check

```
grep -r "" /etc/NetworkManager/NetworkManager.conf /{usr/lib,run,etc}/NetworkManager/conf.d/ 
```

---

### Post by neil-polarnight on 2018-12-24
Thank you [COLOR=#000000]praseodym[/COLOR].

```
:~$ grep -r "" /etc/NetworkManager/NetworkManager.conf /{usr/lib,run,etc}/NetworkManager/conf.d//etc/NetworkManager/NetworkManager.conf:[main]
/etc/NetworkManager/NetworkManager.conf:plugins=ifupdown,keyfile,ofono
/etc/NetworkManager/NetworkManager.conf:dns=dnsmasq
/etc/NetworkManager/NetworkManager.conf:
/etc/NetworkManager/NetworkManager.conf:[ifupdown]
/etc/NetworkManager/NetworkManager.conf:managed=false
grep: /usr/lib/NetworkManager/conf.d/: No such file or directory
grep: /run/NetworkManager/conf.d/: No such file or directory
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf:[connection]
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf:wifi.powersave = 3

```

---

### Post by praseodym on 2018-12-24
```
:managed=[COLOR="#FF0000"]false[/COLOR]
```

Open that file```

gksudo gedit /etc/NetworkManager/NetworkManager.conf
```
and change that entry to
```

managed=true
```
save, close the editor and reboot

---

### Post by neil-polarnight on 2018-12-25
Thank you. Applied and rebooted. Booting with networking.service taking 18.7 seconds.

Any other ideas for me?

Happy Christmas

---

