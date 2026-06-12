---
title: "rtl8180 wifi crashes dhclient"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by iainmackay85 on 2008-05-20
i have just installed fluxbuntu, and have been trying to set up wifi for the past few days, the rtl8180 driver seems to work as i can discover my essid through the gui, however when i connect to it after entering my key it crashes, my conclusion is that it crashes on dhclient, after the socket/fallback line. if someone could tell me where to look to fix this, it would be much appriciated.

i'm not too good at linux.

thanks

---

### Post by iainmackay85 on 2008-05-21
I cannot believe no one else is suffering this problem, i have searched the internet to no joy. if i run dhclient without setting wlan0 essid or key dhclient works connecting eth0, but if i setup wlan0 iwconfig wlan0 essid, key when dhclient runs the computer freezes and the caps lock and shift lock indicators flash until i hold the power.

there must be someone that knows the answer, or atleast something i can try to do to solve it.

---

