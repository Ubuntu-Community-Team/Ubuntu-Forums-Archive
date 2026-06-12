---
title: "Problems connection ASUS USB-N13 USB Wireless adapter. Disconnection after few minut"
date: 2017-04-30
forum: Networking &amp; Wireless
---

### Post by alek87 on 2017-04-30
Hi all,
On my home case i have installed Ubuntu 16.04 LTS and i tried to use a ASUS USB-N13 for my wi-fi connection.
The connection is fine but i see that after some minutes my wi-fi network to Internet does not response anymore.
Is JUST like my USB or wi-fi card go in sleep mode :(
The funny thing is that all seems ok my wi-fi icon but trying to ping my router destination become unreachable.
Any time i need to reconnect i just click on wi-fi icon and then on my SSID home network.
When i buy it i see that was linux compatible but is not working well. 

Anyone can give me some advices?

Thanks in advance.

---

### Post by alek87 on 2017-05-05
anyone can help please?

---

### Post by jeremy31 on 2017-05-05
Try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
It will disable wifi power management as that causes some similar issues, reboot
If it doesn't make an improvement see the wireless script link in my signature and post results

---

### Post by praseodym on 2017-05-07
Please show:
```

lsusb
lsmod
```

---

