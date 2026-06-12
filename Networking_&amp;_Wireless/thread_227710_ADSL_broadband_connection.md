---
title: "ADSL broadband connection"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by satimis on 2006-08-02
Hi folks,

Ubuntu-6.06 amd64
Onboard LAN

At time of installation I have a PCI network card installed.  PCI was network card eth0 and Onboard LAN eth1, the latter of which was selected as default.  After discovering the onboard card can be detected and finishing installation the PCI Network was removed.  Then eth0 disappeared leaving eth1 behind.  

Each time starting the PC, broadband can't be connected.  I have to play around on Network Tools/Device/Netstat, etc. and Networking.  I have no idea how it can be fixed.  But this was routine.

Please advise how to fix this problem and change eth1 to eth0.  TIA

B.R.
satimis

---

### Post by apjone on 2006-08-02
could you post your /etc/network/interfaces here please so we can have a look.

---

### Post by satimis on 2006-08-02
> **apjone said:**
> could you post your /etc/network/interfaces here please so we can have a look.Hi apjone, 

$ cat /etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth1
    iface eth1 inet dhcp

    pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf

iface eth0 inet dhcp

auto eth0
```

B.R.
satimis

---

### Post by apjone on 2006-08-02
> **satimis said:**
> Hi apjone, 

$ cat /etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth1
    iface eth1 inet dhcp

    pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf

iface eth0 inet dhcp

auto eth0
```

B.R.
satimis
in a terminal run pppoeconf

---

