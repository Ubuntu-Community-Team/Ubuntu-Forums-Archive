---
title: "Howto fix up my network-manager?"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by 3str on 2007-07-04
I'm running feisty on my box. The network-manager will uses DHCP to get a IP for me each time I boot. But I'm using a static IP and I didn't find where to use static IP with nm, so I modified the /etc/interface file to save my static IP and deleted anything else in this file except lo. Then I have my static IP right, but the nm seems dead. If I click on its icon, only "Manual configuration" is displayed.

The matter is, I'm moving my box to a new position which uses PPPoE dial-up network. I tried to bring the nm back. 
```

sudo rm /etc/interface
suod dpkg-reconfigure network-manager
```

Then it seems the nm is back again and found a dynamic IP for me. When I reboot my machine, another problem arose. Then Gnome can't start! After the X server starts and nVidia driver loads, the screen is stuck. Only mouse point appears on the screen. This seems network-manager's fault. Because if I switch to a text console and kill the network-manager, the Gnome is running again.

Anyone can help me? Thx!

---

