---
title: "networkmanager not working for wireless"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by RobertBuzink on 2009-04-03
I installed Ubuntu 9.04 on my Acer Aspire One netbook. The network manager shows 'wireless is disabled'. The program Wifi Radar on the other hand does find the wireless card after I activated the 'ifup required' and 'commit required' options. However for some reason I can only connect to wifi networks that are not secured and network manager still says that wireless is disabled. Also, I find Wifi Radar too complicated to use. I would like to use network manager. What can I do?

iwconfig shows wmaster0 and wlan0. Only wlan0 has a wireless extension.

lshw -C network outputs

```
*-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:69:30:87:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg 
```

---

### Post by The Cog on 2009-04-03
It might be worth trying wicd instead. This will remove network-manager (you can reinstall network-manager if you're not happy with wicd). I personally prefer wicd.

---

### Post by 3rdalbum on 2009-04-03
Are you aware that with the Aspire One under Jaunty, you need to blacklist the "acer_wmi" module? Otherwise the wireless will not work properly.

Just add the line "blacklist acer_wmi" to the end of /etc/modprobe.d/blacklist.

---

### Post by RobertBuzink on 2009-04-03
> **3rdalbum said:**
> Just add the line "blacklist acer_wmi" to the end of /etc/modprobe.d/blacklist.

Thanks, I tried your suggestion. But lshm now says *-network UNCLAIMED. I think that means that there is no other driver. Does it?. Also Wifi Radar doesn't work anymore after blacklisting acer_wmi.

BTW: I also tried to activate the alternate propriety "madwifi" driver through 'hardware drivers', but that doesn't work. It does not get activated and returns no errors or warnings.

---

### Post by 3rdalbum on 2009-04-03
Which Aspire One are we talking about? The original 8.9 inch or the new 10 inch? Disabling acer_wmi and using the default ath5k driver works fine on my 8.9 inch. Note that I am using Network Manager to manage my connections.

---

### Post by buzink on 2009-04-04
> **3rdalbum said:**
> Which Aspire One are we talking about? The original 8.9 inch or the new 10 inch? Disabling acer_wmi and using the default ath5k driver works fine on my 8.9 inch. Note that I am using Network Manager to manage my connections.

I use the 8.9 inch. But it works now.

I reinstalled ubuntu jaunty, blacklisted the driver as you suggested and it worked just fine.

Many thanks for your help!

---

