---
title: "Intel Centrino Advanced-N 6200 / Dell XPS 15"
date: 2013-10-08
forum: Networking &amp; Wireless
---

### Post by Vivek_Saxena on 2013-10-08
Hi,

I've been struggling with WiFi on my Ubuntu 13.04 installation on my Dell XPS 15 laptop. I hate to admit, but there are no issues in Windows. On the other hand, in Ubuntu (and even Arch) I find that I have to press Ctrl + R and reload every website a few times to get rid of the "page could not be displayed" or "cannot connect to the internet" messages from the browser.

My university has 2 kinds of connections -- a "secure" and an "open" connection. The open connection is usually unavailable and is slow, whereas the secure connection doesn't work well with Linux.

Tech support at the university supports only Windows and Macs. I cannot get a Mac just to get support from the university's techies.

I'd appreciate any inputs about this. If it means anything, the connection is called WolfieNet :-)

PS -- People at the university seem to be switching to Mac and Windows because Linux isn't officially supported. I feel strongly about this...enough to want to pitch in and figure out a fix for admittedly dwindling population of Linux users like us.

---

### Post by Amorphous Serendipity on 2013-10-08
Hi Vivek_Saxena,

Can you confirm what wireless card you are  using? I thought the XPS15 came with the Intel Centrino Wireless-n 1030  (working in kernel 2.6.36 and up). If this is true you really shouldn't  be having wireless issues in Linux. You may want to investigate the  possibility of browser issues. Clear out your history, cache, etc [not  /etc]. and try an alternate browser.

I hope this helps!

---

### Post by Vivek_Saxena on 2013-10-08
Here's the output from lshw -C network

```

vivek@farpoint:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: **Centrino Advanced-N 6200**
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 58:94:6b:5d:4b:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-31-generic firmware=9.221.4.1 build 25532 ip=172.31.155.136 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:56 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 06
       serial: f0:4d:a2:5d:f3:88
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:54 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
vivek@farpoint:~$ 



```

The problem is universal...it affects Chrome as well as Firefox. And this particular installation is only about 2-3 days old.

---

### Post by Amorphous Serendipity on 2013-10-08
> **Vivek_Saxena said:**
> Here's the output from lshw -C network

```

vivek@farpoint:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: **Centrino Advanced-N 6200**
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 58:94:6b:5d:4b:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-31-generic firmware=9.221.4.1 build 25532 ip=172.31.155.136 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:56 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 06
       serial: f0:4d:a2:5d:f3:88
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:54 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
vivek@farpoint:~$ 



```

The problem is universal...it affects Chrome as well as Firefox. And this particular installation is only about 2-3 days old.


Well the good news is your wireless card is definitely supported. The only thing I can think of is you have a poor connection and the Windows driver is handling any exceptions better than the Linux one.


[LIST]
[*]You could try unloading and reloading the iwlwifi driver (very unlikely it will resolve your issue, but I suppose it is worth a try)
[*]I would also work with iwconfig to check your link quality, signal level, and noise level (if you have a poor connection, than sadly your issue is most likely due to what I said above)
[/LIST]

I know this isn't a complete solution to your question, but I hope it helps.

If anyone has any ideas, please chime in.

---

### Post by chili555 on 2013-10-09
Please open a terminal and do:```
sudo -i
echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us have your report.

---

### Post by buzzingrobot on 2013-10-09
How is the wireless connection elsewhere, away from the university?

---

