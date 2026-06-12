---
title: "intel wifi link 4965AGN issues"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Dougie187 on 2008-08-17
Hey everyone. I am having a really weird and irritating problem. Sometimes when I reboot, my wireless will not work.

It's kind of hard to describe, but basically I have my computer working great, and then I will turn it off and Turn it back on (for whatever reason) and then when it turns back on, wireless doesn't see any network and can't connect if I manually enter the information for my network. Usually when the it's working, I see about 6-9 wireless networks in my area, and then all of a sudden it craps out and I don't see anything.

One other thing, is that I can almost never see any networks when I do an iwlist scan. It usually take 10-15 times to see 1 network doing that, even when network-manager-applet sees 8.

I am going to try to compile the Intel driver from their site, but any help from you guys would be appreciated. Thanks!

---

### Post by pytheas22 on 2008-08-17
It sounds like a problem with the iwl4965 driver.  The next time you can't get wireless to work after rebooting, please (before tinkering with anything else) post the output of:
```

dmesg | grep -e iwl -e eth -e wlan
lshw -C Network
```

---

### Post by Dougie187 on 2008-08-24
Ok, so it happened again. Here are those logs you were looking for.

lshw -C Network
```
  *-network
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:86:58:a2:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:50:68:a3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
```

dmesg | grep -e iwl -e eth -e wlan
```
[   17.314408] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   17.995002] Driver 'sd' needs updating - please use bus_type methods
[   18.112670] Driver 'sr' needs updating - please use bus_type methods
[   22.220350] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25
[   22.220354] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   22.289105] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   22.521754] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   26.622279] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   26.654294] Registered led device: iwl-phy0:RX
[   26.654331] Registered led device: iwl-phy0:TX
[   26.665815] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.712106] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

I did notice the odd things from dmesg that say 'sd' or 'sr' needs updating, but I don't know what those are, and that the links are not ready. Also the using an ethernet cable works fine to get internet. just the wireless doesn't work.

EDIT: Also, something else that is weird, if I plug in an ethernet cable and get an ip, then I unplug that cable, the wireless works.

---

### Post by pytheas22 on 2008-08-24
Thanks for the information.

Unfortunately dmesg doesn't really say anything useful.  I was hoping it would mention why the connection is crashing, but it doesn't say much.

The best advice I can give at this point is to try running these commands:
```

sudo rmmod iwl4965
sudo modprobe iwl4965
sudo ifconfig wlan0 up
```

the next time you have trouble; that may fix it.  Please let me know.

Your other option is to use ndiswrapper instead of the native Linux driver, of course, but unless this is a major problem, I'd recommend sticking with iwl4965.

Also, don't worry about the 'sr' and 'sd' warnings; those drivers don't have to do with wireless.

---

### Post by Dougie187 on 2008-09-02
I tried these yesterday afternoon, and they didn't do anything.

It seems like the only way to make it work, easily at least, is to hardline it, and allow it to get an ip. Then when I disconnect the ethernet cable the wifi works as it should normally.

---

### Post by pytheas22 on 2008-09-02
> It seems like the only way to make it work, easily at least, is to hardline it, and allow it to get an ip. Then when I disconnect the ethernet cable the wifi works as it should normally.

You mean it works if you get an IP using the wired connection, then unplug the wire and connect wirelessly?  That's weird.  I'm trying to think of why the ethernet would have anything to do with the wireless' ability to function...you didn't do anything unusual (like bridge the interfaces or something), did you?

---

