---
title: "wifi adapter stops working after suspend"
date: 2019-01-05
forum: Networking &amp; Wireless
---

### Post by some-guy-with-linux on 2019-01-05
I'm on Lubuntu 18.10.

every time I suspend my laptop, when I unsuspend it, the wifi adapter stops working.
here's what systemctl logs gave me
```
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.6972] device (wlp1s0): supplicant interface state: completed -> disabled
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.7403] device (wlp1s0): supplicant interface state: disabled -> scanning
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.8683] supplicant: wpa_supplicant stopped
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.8685] device (wlp1s0): supplicant interface state: scanning -> down
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.8692] device (wlp1s0): state change: activated -> unavailable (reason 'supplicant-failed', sys-iface-state: 'managed')
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.8786] dhcp4 (wlp1s0): canceled DHCP transaction, DHCP client pid 11111
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.8786] dhcp4 (wlp1s0): state changed bound -> done
jan 05 14:17:23  NetworkManager[11072]: <info>  [1546708643.8799] dhcp6 (wlp1s0): canceled DHCP transaction
jan 05 14:17:24  NetworkManager[11072]: <info>  [1546708644.0296] manager: NetworkManager state is now DISCONNECTED
jan 05 14:17:24  NetworkManager[11072]: <warn>  [1546708644.0978] sup-iface: failed to remove network: The name :1.1556 was not provided by any .service files
```
I tried restarting the network manager service but it still didn't work, unless I rebooted
here's my wifi adapter from lshw (while adapter was working):
```
*-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 01
                serial: 9c:b7:0d:9a:96:dc
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.18.0-13-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:16 memory:fea80000-feafffff memory:fea70000-fea7ffff
```
(windows outputted AR5B125 when I checked)
I would appreciate if someone helped me in this issue, not sure if I put it on launchpad or something

---

### Post by clementc on 2019-01-05
Hi [**[COLOR=#000000]some-guy-with-linux[/COLOR]**]("https://ubuntuforums.org/member.php?u=2095656"),

According to [this page]("https://askubuntu.com/questions/869987/ubuntu-16-04-no-wifi-after-suspend"), can you please try the following:

Before suspend:
```
modprobe -r ath9k
```

Now suspend then wake up the computer, then run:
```
modprobe ath9k
service network-manager restart
```

If this works, I invite you to make permanent changes according to the instructions provided by Josh in the rest of his post.

---

### Post by jeremy31 on 2019-01-05
Moved to networking.

You might also want to try ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Network Manager might be trying to enable wifi power management at the wrong time

---

### Post by some-guy-with-linux on 2019-01-05
alright, will try.

---

