---
title: "Wireless shenanigans"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by Hologeye on 2008-10-04
Hi all. I just installed ubuntu, but wireless doesn't work. I have a linksys wireless card WMP54GS with speedbooster. Ubuntu was able to load the firmware all on it's own, and I am able to view all the wireless networks in my area. However, when I try to connect to my network, it hangs on Waiting for network key for the wireless network. I have read so many different articles about how to get wireless working with ubuntu, and nothing seems to work. Most of them are about getting the windows wireless driver, or getting the firmware, but I can already see networks. I also don't have any .inf file for ndiswrapper, but the card already sees all my networks, so I'm not really sure if I need it. Any help would be appreciated. Thanks!

---

### Post by kforum on 2008-10-05
i dont know much about your card specifically, it may be a driver issue yes, but...
i would guess your router has something to do with it, post a little more info about 'your network', and if you're using static ip of dhcp or whatnot.

im saying that because if it hangs on the waiting for the key part, it prob means your network isnt asking your card for it, otherwise a window pops up asking you to input a key.
if you get this far, the its a static ip issue, and oyu gotta set that manually in the network manager.


cheers

---

### Post by Hologeye on 2008-10-05
I am using a telus router. It uses dhcp, and has wep encryption. But when I disable encryption, ubuntu still can't connect. And I have a laptop with ubuntu installed, and it works fine with my wireless router. Whenever I try to use a static ip address for my wlan0 connection, I can no longer find any wireless networks because wireless just disappears from my network manager.

---

### Post by kforum on 2008-10-05
ok, normally i've used kde, so im not 100% on how this is gonna go for gnome but...

you need to click on some option like 'manual config', then you need to set your ip, the routers ip(gateway) the mask(probably 255.255.255.0) and maybe it will also require you to set dns(set your router's ip too).
-all of this in the network manager-

then you should be able to see and/_or_ connect to the desired network.

cheers.

---

