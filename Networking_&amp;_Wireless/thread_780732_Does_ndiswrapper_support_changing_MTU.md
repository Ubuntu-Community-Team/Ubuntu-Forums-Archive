---
title: "Does ndiswrapper support changing MTU?"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by caljohnsmith on 2008-05-03
I'm using ndiswrapper with my TEW-423PI wireless card, and I can't seem to change the MTU. I can do:
sudo ifconfig wlan0 mtu 1492
And that doesn't work, nor does setting the MTU in my /etc/network/interfaces file. 

So is it just my card and Windows driver, or does ndiswrapper simply not support changing MTU? I would be curious if any other ndiswrapper users can change their MTU. Thanks for any help. :)

---

