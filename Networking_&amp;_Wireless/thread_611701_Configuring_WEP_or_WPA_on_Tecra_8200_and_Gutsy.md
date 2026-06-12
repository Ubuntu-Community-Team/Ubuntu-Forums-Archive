---
title: "Configuring WEP or WPA on Tecra 8200 and Gutsy"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by IanRats on 2007-11-13
I have successfully connected to my home wireless network from a Tecra 8200 with the standard in-built wireless modem after the alternate cd install of Gutsy.

In order to do so, I was forced to disable encryption on this network, which of course I don't want!

Currently, looking at the Active Connection Information:

Interface: Wireless Ethernet (eth1)
Speed: 11 Mb/s
Driver: orinoco_cs

When my network was encrypted (WPA) I did not have an option to connect using WPA in Network Manager, 

I followed instructions at [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html), but there was no change, so I changed my network to WEP-128. However, no matter how I entered the password (as a passphrase or hex) the system would not connect to the network.

I also tried installing ndiswrapper, which I *thought* I did correctly, thought to be honest I'm not sure since I would have expected the driver to be wltos48 (the W2K driver) and not orinoco_cs.

The only other thing I know that is there is that the boot is with the "noacpi" parameter if that means anything.

Thanks for any help.

---

### Post by brazso on 2008-01-12
Hi,

I'm a gentoo linux user and I know nothing about Gutsy. However as a Tecra 8200 owner I know that the builtin wlan card does not support WPA mode (physically). But WEP works flawlessy, I use that at home without any problem. 

Regards,
Brazso

---

### Post by some1l8 on 2008-05-27
by updating to the latest driver, it does support WPA. at lease in windows for me. Quite a few people did it in the forum by compiling their own driver.

---

