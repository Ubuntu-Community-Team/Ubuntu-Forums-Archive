---
title: "Trendnet TEW-423PI / Realtek 8185"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by wintermute115 on 2008-11-10
I'm trying to configure a wireless card on 64-bit Hardy, and everything I can see seems to say that, if it doesn't just work, ndiswrapper ought to make it work without too much effort. But I'm getting stuck somewhere.

The card is a Trendnet TEW-423PI and it seems to have a Realtek 8185 chipset.

I'm new to this so, let me know if I'm doing something obviously wrong.
When I run [FONT="Courier New"]lspci[/FONT], I get the following output:
```
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

I've installed ndiswrapper, and used that to install the Win XP drivers (I've also tried the Vista64 drivers, in case it's a 64 bit issue, but with the same results). [FONT="Courier New"]ndiswrapper -l[/FONT] tells me:
```
net8185 : driver installed
	device (10EC:8185) present
```

However, wireless networking isn't... well, working. [FONT="Courier New"]iwconfig[/FONT] only reveals:
```
lo        no wireless extensions.
eth0      no wireless extensions.
```

I'm stuck as to what I'm doing wrong. Any suggestions?

Thanks.

---

### Post by caljohnsmith on 2008-11-10
Sorry, I misread what you posted. My original post was then irrelevant.

---

### Post by wintermute115 on 2008-11-10
lshw -C network gives me:
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32

```

---

### Post by wintermute115 on 2008-11-12
OK, I've reinstalled 32bit Intrepid, and it seems to be supported natively. No need for ndiswrapper now.

---

