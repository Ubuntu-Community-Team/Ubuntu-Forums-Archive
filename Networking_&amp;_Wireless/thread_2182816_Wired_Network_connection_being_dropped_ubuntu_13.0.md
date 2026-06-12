---
title: "Wired Network connection being dropped ubuntu 13.04 RTL8111/8168"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by bsamim on 2013-10-22
[COLOR=#333333][FONT=UbuntuRegular]Network connection being dropped even after updating the driver to the latest realtek one r8168-8.037.00. I am running Ubuntu 13.04 [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I need to usually reboot my router to fix and or the cable modem also. Other systems connected don't have this problem.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][LINUX driver for kernel 3.x and 2.6.x and 2.4.x]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Also I added the following as well.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]ctrl-alt-T[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]echo on | sudo tee /sys/class/net/eth0/device/power/control[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Below shows my lspci -v output I put in bold the Ethernet item in question[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 03) Subsystem: Hewlett-Packard Company Device 1449 Flags: bus master, fast devsel, latency 0, IRQ 45 I/O ports at 2000 [size=256] Memory at d1004000 (64-bit, prefetchable) [size=4K] Memory at d1000000 (64-bit, prefetchable) [size=16K] Expansion ROM at d1010000 [disabled] [size=64K] Capabilities: Kernel driver in use: r8169**[/FONT][/COLOR]

---

### Post by praseodym on 2013-10-22
If you installed driver r8168 you need to blacklist r8169. Check on-the-fly:
```

sudo modprobe -rfv r8169
sudo modprobe -v r8168
```

---

