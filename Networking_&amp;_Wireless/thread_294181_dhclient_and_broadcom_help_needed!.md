---
title: "dhclient and broadcom help needed!"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by dennis1200 on 2006-11-06
I have been having quite the headache with my wireless. Though I can get it to work no problem - it's annoying. Here's the way it is:

I have a Broadcom 4318 driver, with ndiswrapper and bcmwl5.inf (indicator light works correctly) installed, on a WEP protected network.

Every time I boot the computer the Acer wireless light blinks (acquiring) and then holds (has an address). However, the symbol in my panel lists the network as disconnected, with full signal. I have to type in "sudo dhclient" to get an address assigned to the network. This little bootup routine gets it connected and the wireless internet works. However, if I do a *specific* command, i.e. "sudo dhclient *eth1*"OR "sudo ifup *eth1*", the connection activates, BUT signal bar goes down to zero and I can give up any hope of getting an IP address this time around. This means a reboot to get it back up. Mere attempts to do dhclient again yield zero signal and no internet connection.

Wifi-radar crashes the signal without fail, so I'm not too keen on trying that.Also, attempts to simply write in dhclient to "startup programs" or rc.local don't do anything. So right now I have firestarter giving me an error message every time I boot "device eth1 not ready" and gnome-terminal opening automatically so I can enter the sudo dhclient bit. I've fiddled with /etc/network/interfaces, ndiswrapper has an alias to eth1 in the modprobe.d folder - any ideas? Even just getting dhclient to run automatically?

I realize this card has been the subject of many a thread and I apologize if I'm duplicating something else here. There are so many posts it's impossible to wade through them all.

P.S. Here's my /etc/network/interfaces file (so as not to really delete anything, i just commented out the superfluous entries - there is neither wlan0, ath0 or eth2):
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid XXXXX
wireless-key XXXXXX

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

---

### Post by spd106 on 2006-11-07
You don't appear to have the lines for automating the interfaces eth0 and eth1. I.e. there should be **auto eth0** and **auto eth1**, like there are for lo, eth2, ath0 and wlan0

---

### Post by dennis1200 on 2006-11-08
That did it! Thanks a million.

---

### Post by ckonrad on 2006-11-08
try adding these 3 lines to your interfaces file, then save the file and restart your system.

wireless_mode managed
wireless_keymode open

auto eth1

---

