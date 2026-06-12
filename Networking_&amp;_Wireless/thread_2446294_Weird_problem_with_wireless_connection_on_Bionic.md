---
title: "Weird problem with wireless connection on Bionic"
date: 2020-06-27
forum: Networking &amp; Wireless
---

### Post by wej2 on 2020-06-27
I'm running Ubuntu on an Orange Pi Zero and I have it configured pretty well, except the wireless. I can manually bring up my wlan0 interface successfully when SSH'd over the ethernet link, but I can't get it to connect at startup. wpa_supplicant was giving me issues, but I am able to successfully configure /etc/network/interfaces file to use a wpa key and access point, along with a static IP address using the following configuration:
```

auto wlan0
iface wlan0 inet static
  address 10.10.10.140
  netmask 255.255.255.0
  gateway 10.10.10.1
  broadcast 10.10.10.255
  dns-nameservers 10.10.10.125, 10.10.10.126, 8.8.8.8
  wpa-ssid "my cool access point that works!"
  wpa-psk "my cool password that works!"

```

The strange thing that is happening is that on startup, it seems to connect to the access point and get connectivity to the network, but then disconnect almost immediately. It's then non-responsive until I plug the ethernet cable in and wait for it to get a dhcp address. I run a constant, quick timeout ping of the interface while the system is rebooting on my Windows desktop "ping ubuntu-server-ip -w 100 -t" and I watch the system come online for two pings, then it goes offline again.
```

>ping 10.10.10.140 -w 100 -t
...
Request timed out.
Reply from 10.10.10.140: bytes=32 time=2ms TTL=64
Reply from 10.10.10.140: bytes=32 time=3ms TTL=64
Request timed out.
...
```

The Orange Pi Zero has no display interface, all activity is performed over the network once the system is booted. I can't see what is going on, and I can't find anything in the normal system logs explaining why it would bring the interface up and then shortly after that take it offline. I'm _guessing_ that some conflicting service is taking over and not connecting to the access point properly (because it's not configured in whatever service is doing that), but I can't figure out what may cause that.

Does anyone know how to troubleshoot what may be causing the network interface to come online, and then quickly go back offline? Maybe point me at a log file or something?

Thanks!

PS this device is going to be on a remote part of my property that I don't have hardwired network access, otherwise I'd just plug in to old reliable ethernet. :)

---

### Post by wej2 on 2020-06-27
I think it was Network Manager causing my strife. I had it disabled using systemctl, but it was still showing up as running at startup when I checked systemd-analyze critical-chain. Now that I completely removed it with apt-get purge network-manager, my wifi settings are sticking, and it's staying online. I also found that there was some kind of weird routing loop issue when I had both the eth interface and the wlan interface on the same network segment, I fixed that with a loopback ethernet adapter plugged in to trick the system into thinking the eth is online even though it's not really connected to a switch or router or anything. :)

---

