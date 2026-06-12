---
title: "Wireless Home Network Issues"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by thewho443 on 2008-05-31
My wife just got a new laptop and I installed Studio Ubuntu on it and our wireless router has been acting up since I set her computer up.  We have a NETGEAR WGR614 v6 router set up with WPA security.  I have been using a HP dv600 with Gutsy for several months without any problems.  My wife got a Gateway ML6720 and I set it up yesterday with Studio Ubuntu.  I downloaded the driver and set it up with ndiswrapper without any problems.  When I try to connect to our router it will connect and show a strength of about 95% for a few seconds and then the connection drops to zero.  The strange thing is that the connection on my HP will drop out when I try to connect hers.  I don't think it's the wireless card on her computer because it works fine on the neighbor's connection (yay for people who don't encrypt their wireless routers).  I've never seen anything like this happen before and was curious if it was because I've got two Ubuntu pcs on the same network or if the router is rejecting hers for some reason.

---

### Post by paulphillips on 2008-05-31
So what you're saying is:

On your router, your wife's new laptop won't connect properly and when you do  - your laptop connection dies as well.

On your neighbour's router, both laptops connect with no problems.

You're right - sounds like it's the router, not your ubuntu installs.  Have you done any research on the router?

---

### Post by thewho443 on 2008-05-31
My computer works fine on my router, but when I try to connect my wife's computer it dumps them both.

---

### Post by thewho443 on 2008-06-01
Ok, So I thought that maybe it was the router since both our computers work fine on the neighbor's network.  I bought a Belkin F5D8233-4v3.  Just as before, my computer connects without any problems, but as soon as I try to connect my wife's the whole thing shuts down again.  Both laptops are using ndiswrapper to run their wireless drivers.  My laptop has the Broadcom BCM94311MCG which uses the bcmwl5 driver through ndiswrapper, my wife's computer has a  Realtek RTL8101E and uses the net81187b driver through ndiswrapper.  Anyone have any ideas on what might be going on?

---

