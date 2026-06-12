---
title: "Setting static ip on Wlan0 adapter not working."
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by Taylor_Martin on 2014-06-18
Hello, i have been trying to set up a static ip on my wlan adapter and i can not get it working. I had it done through the GUI but it was causing all kinds of issues and the ip wasnt sticking after restart for some reason. So i disabled the GUI manager and decided to do it through the terminal. I edited the /etc/network/interfaces file and added:

auto wlan0
iface wlan0 inet static
address 192.168.1.6
gateway 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
wpa-ssid <my network name>
wpa-psk <my converted pw to hex>

any help would be greatly appreciated, thank you.

---

### Post by chili555 on 2014-06-18
I suggest you change the file to:```
auto wlan0
iface wlan0 inet static
address 192.168.1.106 
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
wpa-ssid <my network name>
wpa-psk <my pw NOT converted to hex>
```I suggest the IP address of x.106 since x.6 may cause a collision with an address assigned by the DHCP server in the router; many routers protect from this, but not all.

Second, you are responsible for DNS nameservers, as well as the address, netmask, et al. 

Finally, in the context of /etc/network/interfaces, the WPA password is expected to be in clear text; not converted to hex or ASCII or Klingon.

---

