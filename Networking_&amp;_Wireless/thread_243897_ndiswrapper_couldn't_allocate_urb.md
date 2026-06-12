---
title: "ndiswrapper: couldn't allocate urb"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by SigmaX on 2006-08-25
Linksys WUSB11v4 with ndiswrapper.  All the steps I followed to install it are presented on my howto  [here]("http://sigmax.no-ip.org/nix_wusb11v4.php").

The driver works fine, and I get network access via wireless.  However, within a few minutes of booting up and running any sourt of resource intensive task (Network related or not), the system hangs.  The last messages sent are several instances of:

```
ndiswrapper (wrap_bulk_or_intr_trans:621): couldn't allocate urb
```

Any tips for the weary?  

SigmaX

---

