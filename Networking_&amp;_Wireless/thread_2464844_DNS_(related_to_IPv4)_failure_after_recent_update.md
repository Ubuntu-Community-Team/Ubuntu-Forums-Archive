---
title: "DNS (related to IPv4) failure after recent update?"
date: 2021-07-13
forum: Networking &amp; Wireless
---

### Post by iaindcunningham on 2021-07-13
[ATTACH]288816[/ATTACH]

Since a recent update I appear to have lost the ability to resolve a large number of hostnames (including github and launchpad).  So far as I can tell the update has impacted DNS resolution for IPv4 on all of my network connections, which is making life quite awkward!

Thankfully Google and gmail work (IPv6?), and so I've managed to get a recent-ish version of the info script via my phone.  I have attached the results to this post. Hopefully, someone can help me get back to normal!

NB: apt and snap both throw connectivity errors due to these issues:  snap now just times out with a connection error; apt is unable to  download pkg lists from focal release

---

### Post by iaindcunningham on 2021-07-15
So, a better title, might be just "No IPv4"!

If I run:

```
sudo dhclient -r && sudo dhclient
```

Then all connection work as expected... now I just need to work out why I'm not getting an IPv4 lease. 
[B]
Edit:[/B]
I now have everything working again, after adding ```
dhcp=dhclient
``` to /etc/NetworkManager/NetworkManager.conf

---

