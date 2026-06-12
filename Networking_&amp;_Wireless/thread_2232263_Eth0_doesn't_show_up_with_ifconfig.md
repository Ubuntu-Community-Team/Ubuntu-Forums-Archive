---
title: "Eth0 doesn't show up with ifconfig"
date: 2014-06-30
forum: Networking &amp; Wireless
---

### Post by 4dahalibut on 2014-06-30
Hey everybody I just installed 13.04 Xubuntu on my Toshiba L745D-S4220 Laptop, and my ethernet is just not showing up. It may very well be a hardware problem, I do not know. All I know is that ifconfig only shows lo, wlan0 and wlan1, and I have an ethernet cord plugged in that works on other computers. What do you guys suggest?

---

### Post by 4dahalibut on 2014-06-30
Hey everybody I just installed 13.04 Xubuntu on my Toshiba L745D-S4220 Laptop, and my ethernet is just not showing up. It may very well be a hardware problem, I do not know. All I know is that ifconfig only shows lo, wlan0 and wlan1, and I have an ethernet cord plugged in that works on other computers. What do you guys suggest?

---

### Post by steeldriver on 2014-06-30
Hello and welcome to the forums - I've merged your threads, please don't start multiple threads on the same topic. If you think you've posted in the wrong sub-forum then you can use the 'Report Post' button to ask a mod to move it.

---

### Post by 4dahalibut on 2014-06-30
Thanks I wasn't sure about the correct procedure

---

### Post by Iowan on 2014-06-30
Could you post the results of:
```
sudo lshw -C network
```

---

### Post by 4dahalibut on 2014-06-30
*-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:82:35:c5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-35-generic firmware=N/A ip=10.2.11.199 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@4:1
       logical name: wlan1
       serial: 00:a8:2b:00:0a:34
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.8.0-35-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

---

### Post by Bashing-om on 2014-06-30
4dahalibut; Well !

Not even a hint of a wired connection !
OK -> what returns from terminal commands:
```

lspci | grep Ethernet
cat /etc/network/interfaces

```

Do the led's light up when the cat5 cable is connected to the nic (Network Interface Card, on the computer) ?

[INDENT][INDENT]gotta be a cause
[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SeijiSensei on 2014-06-30
I'd check the BIOS and make sure the Ethernet adapter is activated.

---

### Post by 4dahalibut on 2014-06-30
Yeah so the problem was in the bios. I don't know how but the LAN got turned off at some point on the computer. Thanks so much guys!

---

