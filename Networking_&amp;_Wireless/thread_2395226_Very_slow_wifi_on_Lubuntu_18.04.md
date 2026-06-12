---
title: "Very slow wifi on Lubuntu 18.04"
date: 2018-06-28
forum: Networking &amp; Wireless
---

### Post by account-1 on 2018-06-28
I have very poor wifi performance on my machine under Lubuntu 18.04, downloads run at ~ 120 kB/s, making software updates and installations a pita and streaming media impossible. The machine also has a Windows 10 partition, and the same wifi adapter is giving me speeds up to 5 MB/s there.

I am using a USB wifi stick by Asus that has a Realtek RTL8192CU chip:

```

lsusb | grep Network
Bus 002 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
```

What I already tried (based on Googling for the problem):
- I disabled n wifi on my router, it is in a/c mode now.
- I ensured that power management if off for the card.

Any suggestions on what to try next?

---

### Post by jeremy31 on 2018-06-28
Try blacklisting the rtl8192cu module and reboot, see if the rtl8xxxu module works better alone

---

### Post by account-1 on 2018-06-28
Thanks a lot, that did the trick.

For others who have the same problem:what I did was adding the following line to */etc/modprobe.d/blacklist.conf*:

```
blacklist rtl8192cu
```

---

