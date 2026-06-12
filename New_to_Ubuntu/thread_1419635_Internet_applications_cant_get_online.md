---
title: "Internet applications cant get online"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by folabiklan on 2010-03-02
Hi pls i just did a clean install of jaunty and i use a usb modem to connect to the internet. The modem works fine and i can establish a connection with it but i discovered that my browser and other internet apps e.g tor do not connect. Terminal doesnt too. I used d tool to ping my isp but it gives no response. Help me. What can i do? It works ok b4 d format and works fine on windows and in karmic on my laptop. Pc is a desktop

---

### Post by NightwishFan on 2010-03-02
Run this command on the machine in question and post the output here:
```
sudo lshw -C network
```

---

### Post by folabiklan on 2010-03-02
this is the output, i did this while i was ostensibly connected, at least thats what network manager says  fola@ubuntu:~$ sudo lshw -C network   *-network                       description: Wireless interface        product: AR9285 Wireless Network Adapter (PCI-Express)        vendor: Atheros Communications Inc.        physical id: 0        bus info: pci@0000:02:00.0        logical name: wmaster0        version: 01        serial: 00:26:5c:a7:a7:ab        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless        configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn        resources: irq:16 memory:d1100000-d110ffff   *-network        description: Ethernet interface        product: Atheros AR8132 / L1c Gigabit Ethernet Adapter        vendor: Attansic Technology Corp.        physical id: 0        bus info: pci@0000:08:00.0        logical name: eth0        version: c0        serial: 00:26:22:1f:9e:aa        capacity: 100MB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair        resources: irq:28 memory:d1000000-d103ffff ioport:2000(size=128)      i can see my usb connection is not listed even whilst the lan and a non-existent wireless connection is. how can i solve this.  NB: I tried it on karmic too i get the same issues.

---

### Post by folabiklan on 2010-03-02
this is the output, i did this while i was ostensibly connected, at least thats what network manager says  fola@ubuntu:~$ sudo lshw -C network   *-network                       description: Wireless interface        product: AR9285 Wireless Network Adapter (PCI-Express)        vendor: Atheros Communications Inc.        physical id: 0        bus info: pci@0000:02:00.0        logical name: wmaster0        version: 01        serial: 00:26:5c:a7:a7:ab        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless        configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn        resources: irq:16 memory:d1100000-d110ffff   *-network        description: Ethernet interface        product: Atheros AR8132 / L1c Gigabit Ethernet Adapter        vendor: Attansic Technology Corp.        physical id: 0        bus info: pci@0000:08:00.0        logical name: eth0        version: c0        serial: 00:26:22:1f:9e:aa        capacity: 100MB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair        resources: irq:28 memory:d1000000-d103ffff ioport:2000(size=128)      i can see my usb connection is not listed even whilst the lan and a non-existent wireless connection is. how can i solve this.  NB: I tried it on karmic too i now get the same issues. it worked on karmic yesterday!!

---

### Post by folabiklan on 2010-03-02
sorry thats jumbled up, it doesnt look that way when i post it!!  fola@ubuntu:~$ sudo lshw -C network   *-network                       description: Wireless interface        product: AR9285 Wireless Network Adapter (PCI-Express)        vendor: Atheros Communications Inc.        physical id: 0        bus info: pci@0000:02:00.0        logical name: wmaster0        version: 01        serial: 00:26:5c:a7:a7:ab        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless        configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn        resources: irq:16 memory:d1100000-d110ffff   *-network        description: Ethernet interface        product: Atheros AR8132 / L1c Gigabit Ethernet Adapter        vendor: Attansic Technology Corp.        physical id: 0        bus info: pci@0000:08:00.0        logical name: eth0        version: c0        serial: 00:26:22:1f:9e:aa        capacity: 100MB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair        resources: irq:28 memory:d1000000-d103ffff ioport:2000(size=128)

---

### Post by folabiklan on 2010-03-02
Sori my post all messed up. I dont know how to use the forum tools.  Anyway that output only names the lan and a wireless. (Am not sure about that too as i dont have wireless). Anyway when i put my sim in my phone and use it to dialup it works fine. The exact same settings. 


Apparently when i use the
Usb modem the computer doesnt recognise that its online. This modem works ok in windows. I need urgent help

---

### Post by J V on 2010-03-02
Repost in [noparse]```

```[/noparse] tags

And click edit rather than spam with lots of posts...

---

