---
title: "Problem connecting to netgear router"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by schitzowolf on 2007-01-18
I'm having problems connecting automatically to a netgear router with my wireless connection.  I can connect fine with my dsl router and WPA, but I often use my laptop at a friends house who has an unencrytpted netgear router.  the network manager can see the network, but fails to connect.  I _can_ connect manually by opening a terminal and doing```
sudo dhclient wlan0
```  This is a relatively minor inconvenience, but I would still like to get it to connect automatically through network manager if possible. I haven't had a chance to try any other unencrypted routers as I haven't found any in my neighborhood (only 3 - 4 encrypted ones).  if I can find another open network somewhere, I'll try to find out if this is a problem with this specific router or something else.  Let me know if you need any more information.

---

### Post by phossal on 2007-01-18
Why do you want to use network manager?

---

### Post by schitzowolf on 2007-01-18
I started using network manager when I first installed ubuntu because I was having problems configuring the WPA for my router at home manually.  I'm still not quite sure what I was doing wrong initially, but I installed network manager and it "just worked" (essentially, it was the quickest route to a working wireless connection)  I'm not necessarily opposed to removing network manager and configuring everything manually though if that will be easier as long as my ultimate goal of connecting to whichever router I'm close to automatically when I boot up is accomplished.

---

