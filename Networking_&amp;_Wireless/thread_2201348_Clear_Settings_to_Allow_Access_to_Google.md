---
title: "Clear Settings to Allow Access to Google?"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by kronix_00 on 2014-01-24
Not quite sure how to troubleshoot this one:

I have Ubuntu 12.04.4 LTS installed, and have been using it for quite some time.  Recently, it seems I cannot navigate my web browser to google.com.  This doesn't appear to be a router setting -- I have two other Windows laptops on the same network, and they resolve google.com just fine.  It also doesn't seem to be a browser issue -- neither chrome nor firefox can navigate to google.com from my Ubuntu machine.  All other websites I type in appear to load just fine.  Just in case, I've tried resetting the router (and cable modem) as well as the Ubuntu machine itself.

...Any idea what setting to clear, or what to check in order to allow my Ubuntu machine to visit google.com?  

Not sure if it's related, but I cannot 'ping' any addresses from the command line.  I always get a 'destination port unreachable' (unless I'm pinging localhost).  For example, I cannot ping 'cnn.com', but I can navigate there just fine in a web browser.

Any thoughts?  I'm just not even sure how to troubleshoot such an issue.  Since I think I've narrowed it to just the Ubuntu machine... where do I look?

---

### Post by Zhivargo on 2014-01-24
```

Sudo iptables -F

```
Will flush your firewall rules. To check they are gone:
```

Sudo iptables -L

```

---

### Post by kronix_00 on 2014-01-24
Wonderful!  Thanks so very much.  Any idea what I might've done to get the iptables into such a state?

---

