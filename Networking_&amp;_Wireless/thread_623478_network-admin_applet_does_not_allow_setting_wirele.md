---
title: "network-admin applet does not allow setting wireless-keymode variable!"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by wirawan0 on 2007-11-25
It appears to me that the network-admin GUI does not allow the user set everything that can present in /etc/network/interfaces . I specifically have this problem: I have a 3COM wireless card, which lspcmcia gives:

```

~/tmp$ lspcmcia 
Socket 0 Device 0:      [atmel_cs]              (bus ID: 0.0)
        Configuration:  state: on
        Product Name:   3Com 3CRSHPW_96 Wireless LAN PC Card 
        Identification: manf_id: 0x0101 card_id: 0x0696
                        function: 6 (network)
                        prod_id(1): "3Com" (0x41240e5b)
                        prod_id(2): "3CRSHPW_96 Wireless LAN PC Card" (0x3370fdce)

```

This is a nice card in that has X-jack on it. Finally It worked fine in Ubuntu Gutsy. I found out, by comparing the settings with another laptop that I have, that the "security mode" in the 3Com card was not set right. The other laptop has the security setting like this:

```

~/Work/admin/secret $ sudo iwlist eth1 encryption
Password:
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: **************************** (104 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:open

```

while in my laptop that has the 3Com card, the "Security mode" was originally set to "restricted". OK. That's why it could not connect to wireless station all the time unless I disabled the WEP!

Now that I found out the problem, I got the solution by inserting the following text in /etc/network/interfaces :

```

wireless-keymode open

```

But I wonder if this option can be set up in GNOME's network-admin applet. I am afraid it can't. This is annoying. Does anybody have any solution?

Wirawan

---

