---
title: "Finding available connections with broadcom wifi"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by the8thstar on 2007-04-28
Hello there,

In order to successfully find use unsecured networks, I had to switch to windows XP in order to identify them by name. Then I got back to ubuntu and installed them.

Now, how can I 'sniff' the network and see the available networks out there in Ubuntu?

PS: whenever I select 'roaming mode', the wifi card is unable to find a network by itself.

Any clues?

Tanks!

---

### Post by the8thstar on 2007-04-28
Any ideas?

---

### Post by the8thstar on 2007-04-28
Anyone?

---

### Post by DarkN00b on 2007-04-28
Lets say your connection is on eth0 like mine (even though it is wireless), this is what you'd type:

```
iwlist eth0 scan
```

Here's what I get on my home network (essid redacted of course):

```
          Cell 01 - Address: 00:13:49:3C:2D:EA
                    ESSID:"essidISshownHERE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-55 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 36ms ago
```

---

