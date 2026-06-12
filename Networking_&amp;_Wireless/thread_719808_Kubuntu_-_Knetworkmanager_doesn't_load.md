---
title: "Kubuntu - Knetworkmanager doesn't load"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by fuhreal on 2008-03-09
Hey all....

I just got finished installing kubuntu and for some reason knetworkmanager doesn't load.

I click it and nothing happens.  If i launch it from console, there is no output, console just goes down to the next line.

Everything else is working great... anyone come accross knetworkmanager not loading at all?

My wireless is active and pulling an IP from unencrypted networks without an issue however I'm planning to use this laptop when mobile (laptop mobile :P) anyhow .... 

Anyone got something i should look into?

---

### Post by raul_ on 2008-03-10
Is networkmanager daemon running?

---

### Post by fuhreal on 2008-03-10
> **raul_ said:**
> Is networkmanager daemon running?

Not sure.....

How can I check?

When I look through the app list (Add/Remove programs) networkmanager is not even installed however I did try to install it but knetworkmanager wouldn't run still..

So back to the how can i check to see if the daemon for networkmanager is running?

---

### Post by raul_ on 2008-03-10
I'm not sure in Ubuntu, but it should be something like

sudo /etc/rc.d/networkmanager start

if it says FAIL, then it's already running. I just remembered that Knetworkmanager should still run. Nm-applet crashes when the networkmanager is not running, but Knetworkmanager doesn't. Still, it doesn't hurt to check

---

### Post by fuhreal on 2008-03-18
Found WICD which seems to be working wonders.... so no need for Knetworkmanger 

Thanks for the responses though :)

---

