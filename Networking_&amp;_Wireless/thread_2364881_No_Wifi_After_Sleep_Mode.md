---
title: "No Wifi After Sleep Mode"
date: 2017-06-29
forum: Networking &amp; Wireless
---

### Post by emilward on 2017-06-29
I was using Xubuntu 16.04 and I would always loose my wireless connection after waking up from sleep mode. So I switched to Ubuntu Gnome and my wireless works just fine. I want to go back to Xubuntu 16.04 but not if I am going to have the same wifi issue. What is Ubuntu Gnome doing that Xubuntu isn't?

---

### Post by vocx on 2017-06-30
> **emilward said:**
> I was using Xubuntu 16.04 and I would always loose my wireless connection after waking up from sleep mode. So I switched to Ubuntu Gnome and my wireless works just fine. I want to go back to Xubuntu 16.04 but not if I am going to have the same wifi issue. What is Ubuntu Gnome doing that Xubuntu isn't?
This could be a bug in the network-manager of that particular desktop environment. Xubuntu and Ubuntu Gnome are not particularly different, basically just a few things in appearance are different, but internally, the drivers and utilities which really control your network card should be the same.

I haven't used XFCE or Gnome lately to have experienced what you describe, but I did have the same issue while using Unity.

Several threads online suggest it is a problem with "network-manager" so a simple fix is just to restart that service after resuming
```
sudo service network-manager restart
```

Of course, this is bothersome, so people create scripts to restart the network manager automatically after resuming. I did not experience the problem any more after some updates, because problems like this are typically tackled by developers quickly, so in many cases nothing is to be done.

Examples:
[LIST]
[*][https://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues](https://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues)  In this thread they suggest adding some options to the kernel driver SUSPEND_MODULES="iwlwifi" where instead of "iwlwifi", you use the driver for your specific card
[*][https://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade](https://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade)
[/LIST]

Run the following code to see which card and driver you are using
```
lshw -c network
```

```

*-network
       description: Wireless interface
       **product: Wireless 7265**
       **vendor: Intel Corporation**
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 59
       serial: XX:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=iwlwifi** driverversion=4.4.0-83-generic firmware=19.324151.0 ip=192.168.1.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f2000000-f2001fff

```

---

