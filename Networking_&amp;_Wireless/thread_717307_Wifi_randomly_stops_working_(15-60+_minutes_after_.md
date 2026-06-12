---
title: "Wifi randomly stops working (15-60+ minutes after startup)"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by zachalexander on 2008-03-06
Hi there,
**Background: **So I bought my first Linux machine a few months ago, and since I knew very little about it (just a little from shell access to my webhost), I figured I'd go with the simplest installation option -- i.e. no installation, by getting a Dell with 7.04 preinstalled -- an Inspiron 1420, as it happens.

It's been working mostly fine, aside from some things not working after standby > resume,  but nothing beyond minor annoyance. 

**Issue: **But ever since I upgraded to 7.10, the wifi will stop working after the computer has been running for about an hour or so. Once it stopped working as soon as 20 minutes, but usually it seems to be after two hours or more. Until then, the wireless it works perfectly -- it'll automatically detect and connect when the computer is started up, and works at a normal speed until it fails. 

When that happens, it'll switch from the signal strength bars to the swirling "trying to connect" icon, and apparently be trying to reconnect to the same network. Neither of the green "LEDs" will light up, and eventually it'll revert to the standard icon for when you can't connect (a blank computer monitor with a little orange error box icon if I recall). 

Once this happens, the LED by the manual wifi I/O switch will stay on, even if you turn the wireless off manually or from the panel.

The only way to get it working again is to reboot -- though the wireless doesn't seem to quit, so you have to do a hard reset. It'll mostly shut down, and then usually say "NetworkManager <WARN> : nm_signal_handler(): Caught signal 15, shutting down manually.", or that it's trying to shut down eth0, and then just sit there with a cursor. 

(I imagine once the wireless failure is fixed, the need for hard resets will disappear.)

Thanks in advance for your help and ideas on this. In case it's useful, these three threads are on a similar topic, though I wasn't sure how to apply any of them to my case directly:

[http://ubuntuforums.org/showthread.php?t=579579](http://ubuntuforums.org/showthread.php?t=579579) ("Wifi stays connected but stops working after minutes or hours")
[http://ubuntuforums.org/showthread.php?t=306569](http://ubuntuforums.org/showthread.php?t=306569) ("wireless works for a few minutes, then stops working")
[http://ubuntuforums.org/showthread.php?t=290873](http://ubuntuforums.org/showthread.php?t=290873) ("NDISWrapper stops working after 10 minutes")

---

### Post by wieman01 on 2008-03-06
It would help if you mentioned the hardware you have got. Easiest way to find out is by issuing the following terminal command:
> sudo lshw -C network

---

### Post by zachalexander on 2008-03-06
Thanks -- wasn't sure the best way to determine that. The card appears to be a Broadcom "NetLink BCM5906M Fast Ethernet PCI Express."

```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:16:c5:ac
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.47 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:f8:58:cf
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 latency=0 link=no module=tg3 multicast=yes port=twisted pair
```

---

### Post by wieman01 on 2008-03-06
But your wireless is a "PRO/Wireless 3945ABG Network Connection"... a fairly new chipset. I have very little experience with it but it is a good starting point for a search. I have noticed that other users have issues with it as well.

Do you have access to your router? Do you see a setting called "beacon interval" or something like that? What's the current value?

Also, there might be interference with other wireless networks around your place. Try to switch to a wireless channel that is not used by others.

---

### Post by zachalexander on 2008-03-06
> **wieman01 said:**
> 
Do you have access to your router? Do you see a setting called "beacon interval" or something like that? What's the current value?

Also, there might be interference with other wireless networks around your place. Try to switch to a wireless channel that is not used by others.

Well yes, at least in the sense that it's in the building. I'll go check it out right now and report back. 

I'm not sure I can configure it beyond flipping switches on the box, etc. though. "Beacon interval" and channel switching wouldn't be in that category, I suppose...?

---

### Post by zachalexander on 2008-03-06
Hm, don't see those options on the router itself, though I can inquire about other ways to configure...

---

### Post by wieman01 on 2008-03-06
> **zachalexander said:**
> Hm, don't see those options on the router itself, though I can inquire about other ways to configure...
You need to log on to it via the IP address & the browser. Most routers come with a browser GUI nowadays. There are no physical switcheds for this kind of setting.

---

### Post by Capsid84 on 2008-03-06
I was having the identical problem with my HP Pavilion Elite m9040n with an integrated Intel wireless chipset. I just finished installing Ubuntu 8.04 Alpha 6 and it seemed to solve the problem.

---

### Post by zachalexander on 2008-03-07
> **wieman01 said:**
> You need to log on to it via the IP address & the browser. Most routers come with a browser GUI nowadays. There are no physical switcheds for this kind of setting.

Yes, I thought it would be something like that. 

If I'm able to access it, what would I want to do with the beacon interval?

---

### Post by wieman01 on 2008-03-07
What's the current value of beacon interval? I would reduce it to 20 or 40, respectively. See how it goes after that.

Second option is changing the wireless channel.

If all this does not help, then I guess #8 you need to follow the advice given in post #8... :-(

---

