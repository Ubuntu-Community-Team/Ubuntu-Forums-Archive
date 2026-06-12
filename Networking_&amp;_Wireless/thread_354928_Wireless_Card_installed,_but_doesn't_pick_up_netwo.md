---
title: "Wireless Card installed, but doesn't pick up network"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by liambre on 2007-02-06
Wireless has become a bit of a nightmare in the past few days, as I am overly confident with configuring networks in windows, but im a complete newbie to all linux.

I have now finally got my card working, by downloading the latest version of ubuntu (6.10), and the drivers are included on the disk. My main problem now is that I can not find any networks. I try the iwlist scan function, and no networks are returned.

The message 'No scan results' is returned. Can anyone help?

I know the card is being picked up by the computer as lspci shows the card installed.

Thanks to anyone that can help,

Liambre

---

### Post by hotstuff on 2007-02-06
Hmm does your wireless card show up when you goto System>Administration>Netwoking?

---

### Post by liambre on 2007-02-07
yeah, its showing up, just not picking up any networks when im scanning :(

---

### Post by gradedcheese on 2007-02-07
Ok.  Which card do you have?  Can you post the line about it in the lspci output?  Perhaps the radio has to be turned on separately.

---

### Post by liambre on 2007-02-08
lspci returns...

```
Network controller: RaLink RT2561/RT61 802.11g PCI
```

Hope this helps.

---

### Post by Unlimited1 on 2007-02-25
> **liambre said:**
> lspci returns...

```
Network controller: RaLink RT2561/RT61 802.11g PCI
```

Hope this helps.

Was there ever any answer to this question?  I am having the same trouble and can't seem to figure it out.

---

