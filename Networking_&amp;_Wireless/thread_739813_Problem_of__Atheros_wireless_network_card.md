---
title: "Problem of  Atheros wireless network card"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by AndyMar on 2008-03-30
**Is there anybody can help me???Thanks**

My system is Ubuntu 7.10
network card chip is Atheros AR5211
system can recognise the card: Atheros Hardware Access Layer(HAL)  is working
but
```
 iwconfig
  lo        no wireless extensions.

  eth0      no wireless extensions.

  ppp0      no wireless extensions.

``` 
```
lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

```

```
 lspci -v
02:05.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001d (rev 01)
        Subsystem: Atheros Communications, Inc. Unknown device 2055
        Flags: medium devsel, IRQ 21
        Memory at fbff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```
How can i make the network card working?

---

### Post by Paris Heng on 2008-03-30
Dear,

Install the Madwifi driver, [http://madwifi.org/]("http://madwifi.org/"). The card need a driver. For 7.10, I haven try on Madwifi.

---

### Post by kutjara on 2008-03-30
[QUOTE
How can i make the network card working?[/QUOTE]

Here's the HowTo I used to get my card working:

[http://ubuntuforums.org/showthread.php?p=4595130](http://ubuntuforums.org/showthread.php?p=4595130)

Essentially, the Atheros entries in the "Hardware Drivers" app are misleading. Ubuntu tried its best to recognize the card, but the drivers it came up with are the wrong ones. You need to disable those drivers and install the ones provided by madwifi.

Follow the directions in the HowTo, and you should have the card working in no time!

---

