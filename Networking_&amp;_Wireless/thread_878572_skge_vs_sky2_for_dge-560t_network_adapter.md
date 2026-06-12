---
title: "skge vs sky2 for dge-560t network adapter"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by MelkorBauglir on 2008-08-03
Hello All, 

I have a machine with 3 network adapters (head node of cluster)

I am experiencing the following issue with d-link dge-560t card: 
After the initial installation it works OK: 

```

% dmesg
...
[   27.868813] skge 1.13 addr 0xdfff8000 irq 18 chip Yukon-Lite rev 9
[   27.869061] skge eth1: addr 00:17:9a:06:97:14
...
```

but after the reboot I've got the following: 

```

% dmesg
...
[   42.407675] sky2 0000:01:07.0: unsupported chip type 0xff
[   42.407838] ACPI: PCI interrupt for device 0000:01:07.0 disabled
[   42.407854] sky2: probe of 0000:01:07.0 failed with error -95
...
```

and card marked as "unclaimed" and inerface won't up. 

So the idea is that system chooses proper driver at fist (skge) and then tries to use another one (sky2)

However that card is recognizing by the system:
% lspci
```
01:07.0 Ethernet controller: D-Link System Inc DGE-560T PCI Express Gigabit Ethernet Adapter (rev 11)
```

and it is properly configured in /etc/udev/rules.d/70-persistent-net.rule
```

# PCI device 0x1186:0x4b00 (skge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:9a:06:97:14", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
```

I have tried to blacklist sky2 module in /etc/modprobe.d/blacklist but without any success. In his case card won't be detected at all. :(

Any ideas how to resolve this?

---

### Post by MelkorBauglir on 2008-08-04
Hey, guys. 
I really need your help, please. 

It is real headache!

---

### Post by MelkorBauglir on 2008-08-09
Hello

Bump! 

Still no guesses?

---

### Post by smileypaul on 2008-11-17
did you resolve this? im having the same issue

---

### Post by MelkorBauglir on 2008-11-18
> **smileypaul said:**
> did you resolve this? im having the same issue

Hi, 

Hopefully yes. I had wasted a lot of time playing with drivers/modules and reading forums. Frankly speaking I'd lost the hope. :)

Actually in my case this problem was not related to modules. In blank despair I knocked machine down thinking of burned-out hardware. 

I had swapped two network cards in neighbour PCI slots and since then everything was fine. Ubuntu selected right drivers and I was able to make things up and running. 

So, try to swap the cards in the PCI slots. 

Hope this helps. 

If not, please post here the output of 
```

% lshw -c network

```

Kind regards

---

