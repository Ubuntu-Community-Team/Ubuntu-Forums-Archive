---
title: "[SOLVED] Wireless going up and down"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Bliepo32 on 2008-08-24
Alright. I have a laptop, an Acer Aspire 1350. It is running Xubuntu 8.04. So first I tried to get the internal wireless working, and I did get it working. Only problem was that my wireless network was 802.11G, and that the wirless of the laptop was 802.11B.

Anyway, I went to a store, and got one of those external wireless USB-sticks. This one WAS 802.11G. I plugged it in, and it immediately showed up on the network manager.

I configured it (network manager -> Connect to other wireless network), and it worked. Then, disaster struck, my dad pulled out the USB wireless whilst the laptop was still on.

Anyway, I rebooted, and reconfigured everything (same way I did before), and it worked. For some minutes at least. After a short while, the wireless suddenly stops working. If I check the network manager, the wireless stick doesn't show up either.

If I reboot, and enter the password for the keyring manager (or something like that), it works again for some time, and the goes down again.

Can somebody please help me fix this?

---

### Post by Bliepo32 on 2008-08-24
Alright, I have an update. Just a minute ago, I was working in the terminal and entered "lsusb" to see if something showed up. Suddenly it asked for the password of the keyring manager. I entered it, and it is working again (at time of writing), but for how long?

EDIT: Whoops, thought I was editing the post, but accidentally posted a new reply.

---

### Post by aladinonl on 2008-08-24
my wireless network in xubuntu is also unstable. I'm kinda live with it.

---

### Post by Bliepo32 on 2008-08-25
> **aladinonl said:**
> my wireless network in xubuntu is also unstable. I'm kinda live with it.

But it worked fine before, and I want to fix it. Problem is that I do not have the necessary knowledge (yet), and therefore ask others.

---

### Post by Bliepo32 on 2008-08-26
* bump *
Alright, I have been advised to install the windows drivers with ndiswrapper, because even though my wireless worked out of the box, the windows drivers might stabilise the wireless.

I did as instructed, but quickly discovered it didn't make any difference at all.

UPDATE: It seems the wireless USB is now does not work anymore without the help of ndiswrapper.

Additional information:
Security - WPA2 Personal
Wireless USB - König (CMP-WNUSB10)

iwconfig:
```

IEEE 802.11g
ESSID:[left out because it is a hidden AP]
Mode:Managed
Frequency:2.427 Ghz
Access Point:[left out]
Bit Rate=54 Mb/s
Tx-Power:20 dBm
Sensitivity=-121 dBm
RTS thr=2347 B
Fragment thr=2346 B
Power Management:off
Link Quality:56/100
Signal level:-60 dBm
Noise level:-96 dBm
Rx invalid nwid:0
Rx invalid crypt:0
Rx invalid frag:0
Tx excessive retries:0
Invalid misc:0
Missed beacon:0

```

---

### Post by Bliepo32 on 2008-08-27
I need to reformat anyway, so consider this issue: SOLVED.

---

