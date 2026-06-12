---
title: "asymmetric behavior"
date: 2022-01-14
forum: Networking &amp; Wireless
---

### Post by ulrichmuc2 on 2022-01-14
Two hosts, A and B.
On A I try to ping B and get "no route host".
Then I go to B and ping A: success
I go back to A and now pinging B works.

I few days later: the same game.

The two hosts  are a laptop and a Raspberry PI, both running ubuntu mate.

Any ideas?

---

### Post by TheFu on 2022-01-16
wifi involved? Perhaps the radio is turning off to save power?
Solution 
- don't use wifi
- disable power saving in all network adapters
- disable automatic sleep/hibernate/power-off modes

If it isn't those things then check the routing table on each system. How is name resolution addressed on each system?  If you use the IP address instead of the name, does it always work?  Are you using real DNS or mDNS?

---

### Post by ulrichmuc2 on 2022-01-16
The two hosts communicate via wlan. The translation from hostname to IP addresses is done via /etc/hosts
and if ping not works, it shows the correct address of the target host so using that address directly makes no difference.
Both hosts go often to sleep, but when I awake them, they reconnect automatically to wlan and can access the internet
without problems, just A cannot connect to B.
Now, two days after my post, it still works, but probably a week later not anymore.

---

### Post by TheFu on 2022-01-16
So, there are two possibilities.  
a) The power management for the wifi NIC is turning off the card automatically. You'll need to disable that, probably buries in some chip-specific settings.  I don't use wifi at home.

b) The router has a wifi setting that disconnects sleeping clients. 

I know that some wifi routers have a single-host connect mode which prevents 1 client from accessing any other client on the same subnet. I haven't used a typical home router in about 10 yrs, but I know that wifi in cafes and coffee shops are setup this way.  Since you do get some access working from time to time, I don't think the router is setup in single-host mode.  Let me look for link. I don't think I'm explaining this well.  "client isolation" is the term Cisco uses. I doubt that is enabled.

Have you looked at WoL settings for both systems?

---

