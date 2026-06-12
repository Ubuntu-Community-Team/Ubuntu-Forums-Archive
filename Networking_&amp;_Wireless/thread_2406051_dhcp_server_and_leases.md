---
title: "dhcp server and leases"
date: 2018-11-15
forum: Networking &amp; Wireless
---

### Post by atux on 2018-11-15
running ubuntu server 18 in a system and it acts as dhcp server by making use of dnsmasq.
i have the setting to keep the lease 1h.
in the file ```
/var/lib/misc/dnsmasq.leases
``` i see the leases. I did attach 2 PCs and they got IPs correctly and i could see the entries in the /var/lib/misc/dnsmasq.leases. Now i have those 2 PCs removed from the LAN (for over a week) and in the ```
/var/lib/misc/dnsmasq.leases
``` the entries still exist.
I would like to see only the current leases. Is that possible please?

---

### Post by SeijiSensei on 2018-11-15
The entries will go away when the leases expire.  You can use short lease times (3600 seconds for instance) if this matters.  I've never used dnsmasq for DHCP (I use isc-dhcp-server), so I can't tell you more than that.

---

### Post by Doug S on 2018-11-17
> **SeijiSensei said:**
> The entries will go away when the leases expire.  You can use short lease times (3600 seconds for instance) if this matters.  I've never used dnsmasq for DHCP (I use isc-dhcp-server), so I can't tell you more than that.Seiji. as far as I know (and i only use isc-dhcp-server also) that isn't true. The leases information stays until such time as the server needs to use the expired IP address again, because all others have been used, or expired less time ago. Example from my /var/lib/dhcp/dhcpd.leases file:

```
lease 192.168.111.16 {
  starts 4 2017/03/30 10:25:41;
  ends 5 2017/03/31 10:25:41;
  tstp 5 2017/03/31 10:25:41;
  cltt 4 2017/03/30 10:25:41;
  binding state free;
  hardware ethernet 52:54:00:14:ff:9c;
}

```you can see it expired almost 18 months ago, but is still in the file. Why? Well, if a portable device previously on my LAN comes back someday, if available it will get the same IP address, even if the lease had long since expired. Myself, I like it that it works this way. However, it can be annoying when I decide to give a device an address based on MAC, as I keep getting "duplicate" warnings even if I delete it from the leases file, and the backup. i have to remember (which I never do) to re-start the service after the edits.

---

### Post by SeijiSensei on 2018-11-18
Thanks for the correction. Haven't run my own DHCP server in quite a while.

---

