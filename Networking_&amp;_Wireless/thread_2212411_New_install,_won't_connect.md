---
title: "New install, won't connect"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by thault on 2014-03-21
I have a hardline to my server with a fresh install of Ubuntu Server 12.04, the hardline comes off of a printer router and have never had problems with past devices. This install was done on a different then the Hard Drive was thrown into the current computer. When starting up there will be a pause in start up while it waits for connection.

---

### Post by steeldriver on 2014-03-21
What is the interface configuration?

```
cat /etc/network/interfaces
```

What are the hardware and drivers?

```
sudo lshw -C network -sanitize
```

Could there be an address conflict with the other computer (where the HDD was taken from)?

---

### Post by thault on 2014-03-23
[COLOR=#222222][FONT=Times]```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface lo inet dhcp
```

The second command said the network was disabled. I don't know how to paste the full information here. I'm using a RTL8111/8618B PCI Express Gigabit Ethernet Controller. Also has a logical name of eth1[/FONT][/COLOR]

---

### Post by thault on 2014-03-26
I solved this problem by editing /etc/udev/rules.d/70-persistent-net.rules and changing eth1 to eth0, Ubuntu was trying to use the Ethernet port from the computer I installed on, not the computer it is now hooked into.

---

