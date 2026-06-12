---
title: "Static Ip help"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by Night on 2005-11-25
So I set my static IP in networking and thats all good but then I go look at network tools or gtkwifi and it says my ip is that of what I would ahve if i used DHCP. Also evrey so often my internet just cuts out and stops working does this have any connection to my ip beign weird.

---

### Post by Lambert on 2005-11-25
Post your /etc/network/interfaces file here. You can blank out any keys or personal data.

---

### Post by Night on 2005-11-25
```
mapping hotplug
	script grep
	map eth0

iface wlan0 inet static
wireless-essid linksys
address 192.168.1.22
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0

```

Hmm its what I set for my static but it still dosent show up in network tools.

---

### Post by Lambert on 2005-11-25
If you run the command ifconfig it it should match and have the 1.22 end to the ip address.

Do you have a setting on your router where a specific mac address is given a specific ip? Do you know if that was ever set?

I don't use gtkwifi so not sure what that's looking at or how it works.

If you have another computer on the network try to ping both addresses to see if one is bogus?

But it is possible to set up a device with dual ip addresses but when you run iwconfig or ifconfig you would see wlan0, wlan1 which would point to the same device. I don't think this can automatically be set up. Something manual that has to be done.

---

