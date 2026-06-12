---
title: "Where does nm-manager store its settings?"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by _Stevie_ on 2007-12-23
Hello all,

I'm running Gutsy with ndsiwrapper (sis163u). 
In the beginning I had problems with connecting.
Now that I compiled the latest version of ndiswrapper myself I can finally
connect to my wifi router. My problem is now, that I dont use DHCP and have
to configure my IP-address, gateway, etc :

iface wlan0 inet static
address xxxxxxxx
netmask xxxxxxxx
gateway xxxxxxxx

When I write those settings in /etc/networking/interfaces the nm-manager doesnt
show my wifi profile anymore, means I cant connect anymore.
Does the nm-manager obtain its settings from another config file?


Greets,

Stevie

---

### Post by schaumkeks on 2007-12-23
> **_Stevie_ said:**
> 
I'm running Gutsy with ndsiwrapper (sis163u). 
In the beginning I had problems with connecting.
Now that I compiled the latest version of ndiswrapper myself I can finally
connect to my wifi router. My problem is now, that I dont use DHCP and have
to configure my IP-address, gateway, etc :

iface wlan0 inet static
address xxxxxxxx
netmask xxxxxxxx
gateway xxxxxxxx

When I write those settings in /etc/networking/interfaces the nm-manager doesnt
show my wifi profile anymore, means I cant connect anymore.
Does the nm-manager obtain its settings from another config file?


network-manager does not manage interfaces configured in /etc/networking/interfaces at all. So you have to remove (or comment) all entries for your wlan0 device. But the point is, that [network-manager does not support static IPs]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/5364"). Now it depends on the encryption method of your access point if it's possible to configure wireless access within /etc/networking/interfaces (or via System -> Administration -> Network)

Bye, Sven

---

### Post by _Stevie_ on 2007-12-23
ah okay, that explains it. im gonna try if i get it working with "network".

nope, no luck, i cant get it working. this is so frustrating. im fiddling about a week now to get
my wifi working. the driver (apparently) works but i just cant connect.

---

### Post by schaumkeks on 2007-12-23
> **_Stevie_ said:**
> ah okay, that explains it. im gonna try if i get it working with "network".

nope, no luck, i cant get it working. this is so frustrating. im fiddling about a week now to get
my wifi working. the driver (apparently) works but i just cant connect.

Could you give some more information?
What adapter do you use? ( for PCI devices: )
```
lspci | grep -i network
```
What does iwconfig say?
What encryption does your access point use (WEP, WPA, WPA2?)
Does your AP broadcast its SSID? (I guess yes, cause otherwise nm wouldn't have shown it without manual connection)

---

