---
title: "Bluetooth headset pairing in Edgy"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by wammin on 2006-12-10
I'm trying without success to pair my Plantronics bluetooth headset with my laptop running Edgy. I have googled all over for a good HowTo for this, but all I can seem to find has to do with Kubuntu. I'd like a Gnome solution.

Seems like my bluetooth hardware is working and it can find my device:
```

$ hcitool scan
Scanning ...
        00:03:89:7C:C7:D6       PLT 510 v.G

```

But that's as far as I can get:
```

$ sudo hcitool cc 00:03:89:7C:C7:D6
Can't create connection: Input/output error

```

I'm still kinda a newbie, so forgive me if this is obvious. Any help would be awesome.

Thanks.

---

