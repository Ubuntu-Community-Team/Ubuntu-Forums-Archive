---
title: "Configure a/b/g card for g"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Techboy on 2008-07-17
I have a Cisco Aironet card, AIR-CB21AG-A-K9, running under Hardy.  I recently switched routers from Belkin to Netgear and the connection will no longer make.  iwconfig shows the card being configured as 802.11a, which the new router isn't set for.

The system dual boots to XP (work-issued Lenovo T61) and the card works perfectly over on that side.  Just for grins, I booted to the Ubuntu Live CD, input my WEP key and popped right in.  That shows that it does work, just that somehow my configuration got fouled.

Any suggestions on how to reconfigure the card for b or g?

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"xxxxxx"  Nickname:""
          Mode:Managed  Frequency:5.745 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by helgman on 2008-07-18
I've had the same problem. Got a wireless card, Atheros Communications, Inc. AR5413 802.11abg NIC, and it went for 802.11a whenever it had the chance. I'm just using it for experiments so I've never had to worry about longtime solutions but for a quick fix I use this:

```
iwpriv ath0 mode 3
```
Regards,
Helgman

---

### Post by Techboy on 2008-07-19
Thanks!  I'll give it a shot.  Of course, with my putzing with it the past few days, now when I login, the drivers are not loading.  Have to enable them every time.  Probably time to wipe it and start over....

---

