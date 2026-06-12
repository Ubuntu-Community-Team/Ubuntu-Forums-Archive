---
title: "Open networks work OK, WAP does not"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by jonkanon on 2007-08-28
**WPA problems with Feisty**.

I recently bought a D-Link DWL-G650+ pc card since it was said to work "out of the box" according to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink") wiki.

And it does, with open networks. The problem is WPA I've spent too many hours now reading different threads. No luck so far. I tried the fix with the line ENABLED=0. No luck. People seem to have the same problem and there's even rumors about a bug. Anyway, this post is a cry for help...

My Network Manager simply lack the option of "WPA Personal" which should be there. Only three different WEP options is visible.

I tried Wicd instead, with no success. In fact, Wicd identifies the network as a "WEP" although I know it is a WPA. Isn't that a bit weird? I try to connect (of course I have the key) -- but I never recieve an IP-adress. Unfourtunatley, I cannot change the settings of the router.

Btw: I connect to a few different networks so I mustn't have a static solution.

Thanks

---

### Post by moore.bryan on 2007-08-28
[I]according to the d-link tech-specs [page]("http://www.dlink.com.sg/products/resource.asp?sec=&pid=307&rid=1021") for that card, it doesn't seem to support wpa; alas, there's the rub.

is there any particular reason why you can't change the router settings?

it's a long-shot and i'm not exactly sure what good it would do, but do you have the wpa_supplicant package installed?
[/I]

---

### Post by imdano on 2007-08-28
What's the output of ```
sudo lshw -C network
```Odds are you're using the ACX100 chipset, which means no WPA.  I think that you can get WPA in Windows with newer drivers, but I don't know if that translates to WPA support in Linux with Ndiswrapper.

Wicd reports the network as WEP because the driver only reports that encryption is on (not what type), which wicd defaults to WEP.

---

### Post by jonkanon on 2007-08-28
Thanks a lot for answers.

"according to the d-link tech-specs page for that card, it doesn't seem to support wpa; alas, there's the rub."

I guess that explains things. Seems like I purchased the wrong card, then.

"what's the output of 'sudo lshw -C network'"

Here goes:

```
jon@jon-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:a5:b6:c5:91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.123.163 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:40100000-40100fff ioport:2800-283f irq:11
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 3
       bus info: pci@03:00.0
       logical name: wlan0
       version: 00
       serial: 00:11:95:6d:62:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:2c020000-2c021fff iomemory:2c000000-2c01ffff irq:11
```

-- Is it impossible to connect to WPA with this card?

**EDIT:** I found [this]("http://ubuntuforums.org/showthread.php?t=75451") post from Oct, 2005:* "Tonight, I made it. My DLINK DWL-G650 is working in WPA-PSK as I am writing these lines ! I "*  I'll give that fix a try, although my card is a DWL-G650**+**.

---

### Post by imdano on 2007-08-28
No! Don't give that a try!  Your card has a different chipset that will not work with madwifi drivers, and will likely leave you worse off than you are now.  Even though the model numbers are similar, the hardware is very different.

---

### Post by jonkanon on 2007-08-28
> **imdano said:**
> No! Don't give that a try!  Your card has a different chipset that will not work with madwifi drivers, and will likely leave you worse off than you are now.

All right, thanks. DWL-G650 is said to work with WAP; sadly enough, I have DWL-G650+ and it seems like that card does not support WPA.

Should I look for another card or does anyone know a way of getting the WPA going with this card (DWL-G650+)?

---

### Post by imdano on 2007-08-28
There's a possibility that the card will work with Windows drivers using ndiswrapper, but I don't know if that's actually the case.  Search around the forums a bit (which I'm sure you've been doing anyway).

---

