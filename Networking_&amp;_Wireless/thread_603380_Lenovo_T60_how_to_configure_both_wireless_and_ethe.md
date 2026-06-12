---
title: "Lenovo T60 how to configure both wireless and ethernet to work in the same time"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by realthor on 2007-11-05
Is there a way to be able to access both my home lan with wired connection and wireless router under gutsy gibbon? In windows i can do that as you have the alternative connection option but in linux with network manager you have very few option. If i configure wireless then only that works and the same for wired connection, if I configure that only that works.

Please help.

Thanks,
     realthor.

---

### Post by dysolve on 2007-11-05
I have just one question for you, why would you want/need this? I have been asked by customer for this but I do not understand why, they could not explain why they wanted this they where just told they should have it.

---

### Post by kevdog on 2007-11-05
You can have them up at the same time however what do you want to do??

Options are either network bonding (for some applications), or put one of the interfaces on a different subnet (for example one interface talks to LAN, and the other to WAN).

Both interfaces can not be on the same subnet, and of course appropriate routing statements need to be setup.  It just really depends on the application you want.

---

### Post by realthor on 2007-11-05
Hello, I somehow managed to get it working, after a few restarts it remmembered correctly both configurations and both of them worked. Only that it doesn't show the wired connection when you click the network manager icon. It only shows the wireless networks it finds, even if a wired connection is up and running. Actually you can't see the wired connection as running anywhere. You can only see it when you open the Network Settings.

As about why using it...err I have a home network not connected to the internet and there are a few free intenet hot-spots around to which I use to surf the net. To the home lan I connect to access local data cause my laptop's hdd is only 60Gb. 

Cheers,
    realthor.

---

### Post by charles_316 on 2007-11-15
im on a lenovo t60 and it doesn't detect my wireless card? any ideas?

---

### Post by charles_316 on 2007-11-18
bump

---

### Post by charles_316 on 2007-11-30
bump

---

### Post by charles_316 on 2007-12-17
for some reason when i use the command LSHW -C network, i can see that my wireless is disabled:

*-network DISABLED
description: Wireless interface
product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wifi0
version: 01
serial: 00:16:cf:b2:3f:20
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci mul

How do i enable it?

---

