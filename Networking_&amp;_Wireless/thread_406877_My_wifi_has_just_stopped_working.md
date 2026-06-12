---
title: "My wifi has just stopped working"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by AlexBryan on 2007-04-11
I installed Edgy about a week ago and up until last night my wireless connection had worked out of the box. Last night I ran an update which installed 3 small things, and this morning and all of today my wifi hasn't worked. I've tried to get it to connect, but the ath0 card doesn't even show up under networks and when I can find it and select enable, its disabled itself the next time I open it. 
Would it be worth updating to the beta of feisty fawn via cd and see if the advanced networking stuff fixs the problem or is it a simple fix? I'm dual booting with xp so I can access the internet through that to download stuff.

---

### Post by spd106 on 2007-04-11
There was a kernel update a couple of days ago, but that shouldn't have changed anything because the kernel ABI wasn't changed.

Could you please post the output of the following cli commands? ```
sudo lshw -class network
``````
lsmod | grep ath
```

---

### Post by AlexBryan on 2007-04-11
sudo lshw -class network:

*-network DISABLED
descrition:Wireless interface
product: AR5212 802.11abg NIC
vendor: Atheros Communications, Inc.
physical id: b
bus info: pci@2:0b.0
logical name: wifi0
version: 01
serial: 00:09:5b:ec:la:fa
width: 32 bits
clock: 33MHZ
capabilities: bus_master cap_list logical ehternet physical wireless
configuration: broadcast-yes driver=ath_pci driverversion=0.9.4.5 (0.9.2.1) multicast=yes wireless=IEEE 802.11b
resources: iomemory:feae0000-feaeffff irq:193

lsmod | grep ath:

ath_pci    97184    0
ath_rate_sample    15616    1    ath_pci
wlan    204764    4    wlan_scan_sta, ath_pci, ath_rate_sample
ath_hal    192080    3    ath_pci, ath_rate_sample

---

### Post by AlexBryan on 2007-04-11
Thanks for the help, but I just got it working!

---

### Post by xRoninx on 2007-04-11
This is exactly what happened to me. Can you please share what ended up fixing it?

If I should start a new thread with my own problem, let me know.

Thanks

**Edit:** Tried what someone said in another thread about typing in the ESSID name manually. As soon as I did, the internet started working again. Was i being automatically connected to the wrong network or something?

---

### Post by AlexBryan on 2007-04-12
yeah, that's what fixed my problem too. I don't know why it stopped connecting automatically, but once I manually entered my ESSID it connected again.

---

