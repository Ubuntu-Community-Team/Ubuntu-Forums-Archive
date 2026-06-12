---
title: "network-manager-gnome"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by motermouth on 2007-01-03
I'm currently running edgy and I just installed network-manager-gnome last night and It worked fine but now today after school when I turned on my computer it keeps saying no network devices found...could anyone help me out a lil?

Thanks

~Motermouth~

---

### Post by SugarDaddy on 2007-01-03
Network manager by default works when you first install it but following a reboot only works for those devices commented out in your /etc/network/interfaces file. In other words, any devices not commented out are controlled by Gnome Networking in System > Administration > Networking.

So, simply open up this file by typing in a terminal
```
sudo gedit /etc/network/interfaces
```Comment out all the devices you want network manager to control. Save and close the file then reboot. You should be up and running!

---

### Post by motermouth on 2007-01-03
What do you mean comment out??

---

### Post by SugarDaddy on 2007-01-03
Well, let's say you have the following devices listed in your /etc/network/interfaces file:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```You just need to put # symbols in front every line for each device to comment it out. But don't comment out the first two 'lo' entries

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```
Let me know if this works for you. 8)

---

