---
title: "Problem: DHCP Working, getting an IP but cant even ping access point"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Gohalien on 2007-04-29
Hello, I am new in ubuntu, I am trying to set up the wireless from the pass 2 days with no success.
I have a [TP-Link -WN551G ]("http://www.tp-link.com/products/product_des.asp?id=41"), in ubuntu it is as ath0, my wireless conection is appearing to select the SSID correctly, I set it up and DHCP gives me an IP. I try to ping 192.168.0.1 (my access point) and host unreachable.
in iwconfig the info looks like correct, I cant paste here because I am using 6.06 LTS x64 and I have not ntfs-3g to install because I cant download it for obvious reasons.
"route" also looks like correct.
I run dhclient and it connects to my access point and bound a new ip correctly.
I ping localhost and it is working.
in lspci ath says unknown device, but in network configuration ath0 is correct and configurable.

I dont know what else to try.
I installed ndiswrapper, I created the driver for my wireless card, it says something like hardware present, so I think that is correct, but I dont know how to bind that driver with my wireless card or I dont know if I need that.
I tried setting in access point as open conection without asking me a WEP key.
I tried too with WEP key.

Still no success....

---

