---
title: "Network Manager deleted, can't go online"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by maximovna on 2014-09-15
Hello together,
yesterday my WiFi connection disappeared and the  Network Manager said that the WiFi was switched off by a hardware  switch, which was not the case. I restarted the computer many times  pressing the hardware switch, but nothing helped. then by mistake I  deleted the Network Manager by running
sudo apt-get remove --purge network-manager-gnome network-manager
big mistake... now I'm offline and can't reinstall the programme. 
I've  downloaded the "NM".deb and "NM-gnome".deb packages and tried  installing them with the Ubuntu Software Center, but I can't install the  -gnome.deb package, because of lacking dependency ("Dependency is not  satisfiable: libnm-gtk0(=0.9.8.8-ubuntu7)").
I'm not sure that I will be able to go online after installing the Network Manager, but at the moment it seems so. 
I'm using Ubuntu 14.04LTS, 64-bit
will be extremely grateful, if you could help me.
thanks a lot!
I.

---

### Post by steeldriver on 2014-09-15
You should be able to get online using old fashioned "ifup/down" networking. If you have access to a wired ethernet connection and a router providing DHCP/DNS configuration, that should be as simple as

```

sudo ifconfig eth0 up

sudo dhclient -v eth0

```

If your primary wired interface is named differently than eth0 you can check what it's called using ifconfig or by looking at the contents of the /sys/class/net directory.

If you only have wireless, or if for example your router supplies DHCP addresses but no DNS information, it will be slightly more complicated but still doable. Once you're online you should be able to reinstall network-manager and all its dependencies in the normal way via the software center or apt-get.

---

### Post by maximovna on 2014-09-15
I don't have a wired connection unfortunately. 
I was thinking on repairing the software with a bootable usb. this should reinstall the network manager, right?

---

### Post by steeldriver on 2014-09-15
Unless you mean a complete re-install, I'm not familiar with repairing from a bootable usb

I'd suggest trying to get a wireless connection from within your existing installation first - you could reboot into recovery mode, then select the 'Enable networking' option and see if it will lead you through the wireless setup (i.e. entering your SSID and credentials). 

Alternatively you could create a minimal /etc/network/interfaces file for wireless with the equivalent info - e.g. for WPA with DHCP that would be something like

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid mynetworkname
    wpa-psk mysecretpassphrase

```

and then 

```

sudo service networking restart

```

If your DHCP does not supply DNS info, you can add that to the interface definition as well e.g.

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid mynetworkname
    wpa-psk mysecretpassphrase
dns-nameservers 8.8.8.8 8.8.4.4

```

---

