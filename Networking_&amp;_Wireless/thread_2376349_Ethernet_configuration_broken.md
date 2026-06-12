---
title: "Ethernet configuration broken"
date: 2017-11-02
forum: Networking &amp; Wireless
---

### Post by ubupro97 on 2017-11-02
I believe ethernet was working out of the box on this machine about a year ago, but I appear to have manually broken it.

Distro: Ubuntu MATE 17.10 (AMD64) - upgraded from 16.04
Device: Gigabit Ethernet driver 2.3LK-NAPI
Driver: r8169
Destroyed config: /etc/network/interfaces
dmesg: [    1.367446] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.367458] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.367887] r8169 0000:02:00.0 eth0: RTL8101e at 0xffffa5abc0645000, 00:24:21:b0:bb:b8, XID 94200000 IRQ 24
[    1.422722] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    8.653161] r8169 0000:02:00.0 enp2s0: link down
systemD logs: 
[https://paste.ubuntu.com/25870247/plain/](https://paste.ubuntu.com/25870247/plain/)

Note that I currently have network access with a USB dongle (R8188EU).

History: network worked fine in 16.04, updated to 17.04 and it broke. I fixed it with a hackish solution of typing dhclient which I set up automatically. That no longer works in 17.10, dhclient seems to never finish running. I would expect that there is some issue with the link name changing from eth0 to enp2s0.

Edit: while typing this the network came online. I'll investigate a router problem.

Edit 2: It could be because I attempted:
# systemctl start systemd-networkd.service

Edit 3: I enabled
# systemctl enable systemd-networkd.service

But ethernet is never working reliably on boot.

---

### Post by jeremy31 on 2017-11-02
*Thread moved to **Networking & Wireless**.*

---

### Post by ubupro97 on 2017-11-09
Bump.

---

### Post by ynota on 2017-11-11
If your problem is on a laptop have a read of this wiki article on [ASPM]("https://en.wikipedia.org/wiki/Active_State_Power_Management"), Do you have power management in your BIOS? Could this be disabling your Ethernet adaptor?

---

