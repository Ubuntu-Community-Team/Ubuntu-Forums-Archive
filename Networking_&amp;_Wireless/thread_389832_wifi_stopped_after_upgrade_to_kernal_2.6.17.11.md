---
title: "wifi stopped after upgrade to kernal 2.6.17.11"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by gmconie on 2007-03-21
I loaded Ubuntu 6.10 kernal 2.6.17.11 on my Compaq nx9010 notebook. wifi worked well. I applied all updates and the wifi does not work. If I go into administration / networking the device is there to configure but there is no wireless network information. Ifconfig does not show the device, and setting to static IP has no effect.

If I restart and boot kernal 2.6.17.10 it all works correctly. Any help appreciated.
[B]
/etc/network/interfaces[/B]

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
address 10.1.1.23
netmask 255.0.0.0
gateway 10.1.1.1




auto wlan0

iface eth1 inet dhcp
wireless-essid not_telling
wireless-key not_telling

auto eth1

---

### Post by chili555 on 2007-03-21
What kind of wireless card is it? Native driver or ndiswrapper? If ndiswrapper, did you install from Ubuntu repositories, or the .tar.gz/make/make install method? What does lspci -v | grep -i Network tell us?

---

### Post by gmconie on 2007-03-21
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

I did no configuration or installation. It worked straight away. It also worked in a previous dapper installation.

---

### Post by chili555 on 2007-03-21
Very interesting. I am running a Prism 2.5 right now! Please do two things for me:

sudo gedit /etc/modprobe.d/blacklist and add two lines at the end:```
#chili sez no to prism2
blacklist prism2_cs
```Reboot.

Second, so the Prism 2,5 guys can find this two weeks from now, could you please edit the title of this post to "Prism 2.5 stopped after upgrade to kernal 2.6.17.11"?

Thanks and let us know.

---

### Post by gmconie on 2007-03-31
Thanks for the help,

Did the blacklist thing and no change. Because I had only loaded and done no setup I  loaded 6.06 instead. Works fine.

---

