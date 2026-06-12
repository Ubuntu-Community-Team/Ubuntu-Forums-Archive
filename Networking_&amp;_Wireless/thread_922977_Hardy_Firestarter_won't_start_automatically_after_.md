---
title: "Hardy: Firestarter won't start automatically after boot"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by mibadt on 2008-09-17
Hi,
I've recently switched to a new firewall-firestarter on my Kubuntu Hardy (KDE 4.1.1) PC. The PC is on a local LAN and gets a dynamic IP address using dhcpd.
I can't cause firestarter to start "automatically" during boot, although I've tried all the following:

1. Configure Firestarter to start on program startup and DHCP lease renewal.
2. Added respective entry into the end of rc.local.
3. Added respective entry into he end of /etc/dhcp3/dhclient.conf
4. Combinations of the above.

Please advise.

Thanks.

Michael Badt

---

### Post by Ayuthia on 2008-09-18
> **mibadt said:**
> Hi,
I've recently switched to a new firewall-firestarter on my Kubuntu Hardy (KDE 4.1.1) PC. The PC is on a local LAN and gets a dynamic IP address using dhcpd.
I can't cause firestarter to start "automatically" during boot, although I've tried all the following:

1. Configure Firestarter to start on program startup and DHCP lease renewal.
2. Added respective entry into the end of rc.local.
3. Added respective entry into he end of /etc/dhcp3/dhclient.conf
4. Combinations of the above.

Please advise.

Thanks.

Michael Badt
Have you tried adding a script to call firestarter and placing it in ~/.kde4/Autostart?

---

### Post by mibadt on 2008-09-19
Thanks,
I haven't yet tried it (i will), yet I'd rather have the firewall start regardless of the graphic environment.


Michael Badt

---

