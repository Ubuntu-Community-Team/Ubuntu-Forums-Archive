---
title: "BCM43XX, Feisty live"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by tajreed on 2007-06-07
Using BCM43XX-FWcutter and Feisty live, I am unable to pick up my home network. Should I be able to function wirelessly using Feisty Live? 
My security is set to WPA-personal, yet this does not appear on the drop down list when I attempt to configure manually. 
In Feisty admin/Hardware info the wireless driver is shown as BCM43xx.

Any ideas?

---

### Post by spd106 on 2007-06-08
Yes, you can use the wireless card from the live environment.

Network Manager should be able to detect the type of encryption, certainly if you have not disabled ssid broadcast on the AP.

You could try forcing it to connect using the "connect to other network" option and typing in the ssid.

NB Network-admin, the utility in System -> Admin -> Network, does not support WPA at this time.

---

### Post by tajreed on 2007-06-08
My feisty/BCM43xxx does even detect the wireless network. Any thoughts on that?

Thanks

---

