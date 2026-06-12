---
title: "Network-Manager wired and wireless"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by Palmstroem on 2008-08-27
Hi folks,

I could not find a way to persuade Network-Manager to configure my "business" and "home" networks correctly. "Business" is static IP, eth0, and "home" is dhcp router, wlan0. Both networks work but I have to manually set up the parameters every time.

I played a bit with roaming mode and resolvconf: no success.

Any help welcome!

---

### Post by Vishal Agarwal on 2008-08-27
There is a save option in network manager. Using that u save different  configurations for network card. I am not very confident about your case, but in my laptop I had 3 different configurations saved. As per the location requirement i choose the configuration.

---

### Post by Vishal Agarwal on 2008-08-28
Is your problem solved ?

---

### Post by Palmstroem on 2008-09-01
Thanks, Vishal,

I did that already (i.e. manually switching to a saved network configuration with Network-Manager).

However, I was looking for an automatic switching: use the wired eth0 whenever connected and the wireless wlan0 when eth0 is not available.

---

