---
title: "What's wrong with KNetworkManager?"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by inflamous on 2007-08-17
I have a Broadcom Dell Wireless 1390 WLAN Mini-card on a Inspiron 1501, the driver installs properly on kubuntu, but KNetworkManager doesn't show any wireless networks at all.  I know the driver works because I can turn on or off my wifi and when I do ```
iwlist scanning
```, it shows all the networks nearby.  But when I open KNetworkManager, it only shows Wired Devices even though I don't have an ethernet cable plugged in.

I would go to the manual configuration but for some reason, I can't enter that, using my password or the root password, it always returns a > "Conversation with su failed"

Can anybody tell me why KNetworkManager isn't letting me connect to my router?

---

### Post by Jamie Jackson on 2007-08-17
Give [this]("http://ubuntuforums.org/showthread.php?t=475963") a shot.

---

### Post by inflamous on 2007-08-17
I've used ndiswrapper last time, but it sort of worked randomly for me.  After a few minutes of working, it just stopped and it wouldn't connect to my router.  When I rebooted I had the problem where no wireless networks showed up on KNetworkManager, and my wifi light didn't turn on anymore, so I used the native linux driver from this site:
[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

The wifi light turned on and iwlist scanning worked, but I still can't see any of my networks.

Right now I'm on windows because I can't use the internet in linux, but I want my linux to work :(

---

### Post by kevdog on 2007-08-17
Can you post 

iwlist scan
lshw -C network

---

### Post by inflamous on 2007-08-19
```
iwlist scan
```
eth0      Scan completed :
          Cell 01 - Address: 00:13:46:3F:D6:04
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-48 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 172ms ago
          Cell 02 - Address: 00:13:46:3F:D6:04
                    ESSID:"aph"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-49 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 184ms ago

```
lshw -C network
```

  *-network
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:fc:a7:8e:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0203fff irq:18
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth1
       version: 02
       serial: 00:19:b9:7f:dd:95
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 latency=64 link=no multicast=yes port=twisted pair
       resources: iomemory:c0300000-c0301fff irq:21

---

### Post by Jamie Jackson on 2007-08-19
My guess is that you need to remove the interfaces (from /etc/network/interfaces) that you want to be controlled by NetworkManager.

If you've got entries in there besides the two for "lo," you'll want to comment those out, and restart NetworkManager.

Here's a way to do all this in one shot:
```

sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo /etc/dbus-1/event.d/25NetworkManager restart

```

---

### Post by inflamous on 2007-08-19
Thanks jamie, my internet works perfect now :D

---

### Post by Jamie Jackson on 2007-08-19
> **inflamous said:**
> Thanks jamie, my internet works perfect now :D

No problem, and thanks for the link to the native driver installation blog. I tried it myself today, and the installation couldn't have been any easier, but for some reason, my [throughput is terrible, and the connection is flaky]("http://ubuntuforums.org/showpost.php?p=3219122&postcount=123").

I've left the blogger a comment. If I can get these problems figured out, then the native driver method might become my favorite.

---

