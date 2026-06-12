---
title: "How do I change : DNS domain name"
date: 2020-07-14
forum: Networking &amp; Wireless
---

### Post by resplendent on 2020-07-14
I tried sudo /etc/resolv.conf but it just keeps rewriting it.  I made a typo on my dns domain name and need to fix it.  Seems like it should be an easy fix.  Thanks

---

### Post by SeijiSensei on 2020-07-15
Pretty limited info to go on here.

Are you talking about the "search" domain, the one that the resolver adds to unqualified hostnames?  
```

nameserver 127.0.0.53
options edns0
search example.com

```

Ubuntu usually populates this during the DHCP exchange and gets the value from the router.

Are you using a static configuration?  You can set the search domain using the standard Network Manager.

/etc/resolv.conf is always rewritten upon boot in recent Ubuntu releases.

---

### Post by resplendent on 2020-07-15
Using Ubuntu 20.04LTS server with Lubuntu GUI.  During install I set up a static IP address.  It is the search domain that I typo'd.  I tried sudo nano /etc/resolv.conf and changed it but it keeps reverting.  I need to fix it permanently. Looking for the actual file where I change it.

Example

nameserver 127.0.0.53
options edns0
search example.com //this is where I typo'd I need to permanently change this line to something else.

---

### Post by resplendent on 2020-07-15
I think I fixed this, I changed the yaml based config file in netplan and rebooted

Open terminal
cd /etc/netplan
sudo nano 00-installer-config.yaml

Find the line you are wanting to change

Ctrl0 to write
Ctrlx to exit

reboot

Back to terminal
resolvectl
to check config

Not sure if this is the 'right' way to fix the problem but it seems to work.

---

