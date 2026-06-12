---
title: "Wireless card issue"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by nomaan on 2007-10-04
**Laptop** 
Acer Travelmate 2483NWXMi

**Wifi**
Atheros AR5005G

I installed Ubuntu 7.04 using wubi. It detected my wifi card, but I couldn't get wifi to work. I somehow uninstalled the drivers in order to use madwifi. Madwifi is now installed, but my wifi card is AWOL in the network settings.

* lshw -C network gives me this

```
*-network UNCLAIMED
       description: Ethernet controller
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
       resources: iomemory:d0000000-d000ffff irq:255

```

* sudo iwconfig gives me this

```

lo        no wireless extensions.
eth0      no wireless extensions.

```

* lspci gives me this

```

0a:03.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

```

* System -> Hardware Information also shows AR5005G listed.

* System -> Restriced Drivers Manager lists the Atheros HAL as enabled but **Not in use**. EDIT --> after a few reboots, now it shows in use

I've gone through the forums but can't seem to find an answer for this.

How do I get it back so that I can have another go at configuring it?
Thanks in advance

---

### Post by autek on 2007-10-05
Try as sudo  ifup eth0. If that works look and make sure that "auto eth0" is in the /etc/network/interfaces file.

Ed

---

### Post by nomaan on 2007-10-06
Something odd, I ran that command and it said it is already up. I did ifconfig and got this;

```

ath0      Link encap:Ethernet  HWaddr 00:19:7D:CC:CC:E6  
          inet addr:192.168.0.178  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:fecc:cce6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-CC-CC-E6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91931 errors:0 dropped:0 overruns:0 frame:3
          TX packets:87342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3211347 (3.0 MiB)  TX bytes:2971050 (2.8 MiB)
          Interrupt:18 

```

How did this come up? Anyways, I have the wireless back in my 'Network Settings window'. Now that I have configured it, it is still not connecting to the internet. I've tried setting manual IP and also DHCP. With DHCP, I don't get an IP assigned. I am using WEP Shared.

What is the next step? Is there a graphical utility that shows me the APs present? See the signal strength? etc

Thanks again for the help!

---

