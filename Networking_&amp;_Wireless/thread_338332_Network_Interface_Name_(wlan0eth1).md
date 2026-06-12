---
title: "Network Interface Name (wlan0/eth1)"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by Vil on 2007-01-14
My issue is that nearly every time I restart my desktop computer, the wireless network interface name alternates between eth1 and wlan0. There are no issues with connecting or it working, but only because I figured out how to work around the name changing by duplicating everything I had configured for wlan0 for eth1 (the /etc/network/inferfaces file shown below, for example). It isn't a huge problem, but it does get annoying since I have to change a couple configurations each time I restart. I am using a Linksys PCI card, and I have to use ndiswrapper to get it to work. I thought that might be related, but nothing I have found led me to an answer.

This is "/etc/network/interfaces", It took some trial and error to get everything connecting right because it did switch names on a restart (which is why I have the same configuration for both eth1 and wlan0).
> 
auto lo

iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Home

iface wlan0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Home

auto wlan0

auto eth1



Here is "/etc/modprobe.d/ndiswrapper". I added the second alias for eth1 when I changed the interfaces file, I never actually tested it without the following change from when I configured ndiswrapper to begin with.
> 
alias wlan0 ndiswrapper
alias eth1 ndiswrapper



If there are any other files that you think might help in figuring this out, I will be more than glad to post them. :) Thanks for looking & any help or ideas you might have. :)

---

### Post by phossal on 2007-01-14
You probably want to make an /etc/iftab entry, which can pin down an interface name based on mac address.
```
sudo  gedit /etc/iftab 
```
Copy and Paste (edit as necessary):
```
 # This file assigns persistent names to network interfaces..
 wlan1 mac XX:XX:xX:XX:Xx:xX
```

---

### Post by Vil on 2007-01-14
I bet this was the problem the whole time, then:

> # This file assigns persistent names to network interfaces.

# See iftab(5) for syntax.



eth0 mac 00:0e:a6:92:ae:4e arp 1

eth1 mac 00:0f:66:1d:19:7d arp 1

I'll just change it from eth1 to wlan0

Thank you :)

---

