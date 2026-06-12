---
title: "help with network interfaces file"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by hacc on 2007-02-26
i messed with my network interfaces file and now when i try to open networking through
system>administration>networking it crashes
any suggestions?

hacc

---

### Post by spd106 on 2007-02-26
You'll have to open it in a text editor and check for mistakes. The usual one is duplicate auto lines.

Press Alt-F2 then enter this command,
```
gksudo gedit /etc/network/interfaces
```

If you're on KDE then there's probably an equivalent command, or just use nano at a terminal.

If you're unsure of the problem then please post the file here and we'll take a look.

---

### Post by hacc on 2007-02-26
# /etc/network/interfaces -- configuration file for ifup(8), ifdown(8)
# The loopback interface
# automatically added when upgrading
auto lo
iface lo inet loopback
# The first network card - this entry was created during the
# Debian installation automatically added when upgrading
auto eth0

---this is what my network interfaces file looks like, could you tell me what its supposed to look like please

---

### Post by spd106 on 2007-02-26
There should be line the contains the iface for eth0, such as this
```
iface eth0 inet dhcp
```
Add the above line to the end of the file and it should work again.

You may need more lines, but they can be added with the network-admin capplet.

---

### Post by hacc on 2007-02-26
i added the iface eth0 inet dhcp but it didnt change anyhting i have reinstalled the network manager but that didnt do anything either

---

### Post by spd106 on 2007-02-26
If you want to use network manager then you need to comment out or delete the 'auto eth0' line to allow it to take over control of the interface.
See [https://wiki.ubuntu.com/WifiDocs/NetworkManager](https://wiki.ubuntu.com/WifiDocs/NetworkManager)

---

### Post by hacc on 2007-02-26
ok so my network manager works but still when i try to open system>aministration>networking
it crashes.
could someone figure this out please?

hacc

---

