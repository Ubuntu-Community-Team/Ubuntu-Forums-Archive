---
title: "Wifi Slow"
date: 2017-04-09
forum: Networking &amp; Wireless
---

### Post by Tony_Palermo on 2017-04-09
I am using Ubuntu and my wifi in Ubuntu only downloads at around 150 kb a second.  In Windows it's downloading at like around 10 mbps.  I'm searched the web and found a lot of people having this issue but I don't know how to even check to see what wireless card is in my computer.  I should mention I am new Ubuntu and i'm using it on  a live USB drive.  I did this because I was not sure all my hardware would work in Ubuntu.  I've tried Linux Mint, Fedora, and a few of Linux versions but they all have the same slow wifi issues.  

Do I have to install Ubuntu to fix this issue or can I do something with the live USB to make sure it works with my system?

Thank you,

Tony

---

### Post by kc1di on 2017-04-10
Hello Tony_Palermo and Welcome to Ubuntu,

You may have to do an install to activate the correct driver for you machine. It depends a lot on the machine and the wifi card involved. 
If you go to a terminal and type this command ```
 lshw -C network
``` post the output here and it will help others tell you what to do.

---

### Post by Tony_Palermo on 2017-04-10
Here is the information that came up when I inputted  "[COLOR=#000000][FONT=&quot]lshw -C network"[/FONT][/COLOR]

[FONT=arial]WARNING: you should run this program as super-user.[/FONT]
[FONT=arial]  *-network               [/FONT]
[FONT=arial]       description: Wireless interface[/FONT]
[FONT=arial]       product: RTL8723BE PCIe Wireless Network Adapter[/FONT]
[FONT=arial]       vendor: Realtek Semiconductor Co., Ltd.[/FONT]
[FONT=arial]       physical id: 0[/FONT]
[FONT=arial]       bus info: pci@0000:01:00.0[/FONT]
[FONT=arial]       logical name: wlp1s0[/FONT]
[FONT=arial]       version: 00[/FONT]
[FONT=arial]       serial: 2c:33:7a:0b:00:f1[/FONT]
[FONT=arial]       width: 64 bits[/FONT]
[FONT=arial]       clock: 33MHz[/FONT]
[FONT=arial]       capabilities: bus_master cap_list ethernet physical wireless[/FONT]
[FONT=arial]       configuration: broadcast=yes driver=rtl8723be driverversion=4.8.0-36-generic firmware=N/A ip=192.168.43.132 latency=0 link=yes multicast=yes wireless=IEEE 802.11[/FONT]
[FONT=arial]       resources: irq:43 ioport:3000(size=256) memory:f0b00000-f0b03fff[/FONT]
[FONT=arial]  *-network[/FONT]
[FONT=arial]       description: Ethernet interface[/FONT]
[FONT=arial]       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT]
[FONT=arial]       vendor: Realtek Semiconductor Co., Ltd.[/FONT]
[FONT=arial]       physical id: 0[/FONT]
[FONT=arial]       bus info: pci@0000:02:00.0[/FONT]
[FONT=arial]       logical name: enp2s0[/FONT]
[FONT=arial]       version: 10[/FONT]
[FONT=arial]       serial: 68:f7:28:56:68:80[/FONT]
[FONT=arial]       size: 10Mbit/s[/FONT]
[FONT=arial]       capacity: 1Gbit/s[/FONT]
[FONT=arial]       width: 64 bits[/FONT]
[FONT=arial]       clock: 33MHz[/FONT]
[FONT=arial]       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT]
[FONT=arial]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT]
[FONT=arial]       resources: irq:35 ioport:2000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff[/FONT]
[FONT=arial]WARNING: output may be incomplete or inaccurate, you should run this program as super-user.[/FONT]

---

### Post by kc1di on 2017-04-10
Here's what I think the problem might be that card has two antennas and you need to select ant 2.  But I don't think you can do that in live mode since it requires a reboot to take affect.
and the setting would not be saved in live.  So you would have to do a hard drive install.

---

### Post by jeremy31 on 2017-04-10
> **kc1di said:**
> Here's what I think the problem might be that card has two antennas and you need to select ant 2.  But I don't think you can do that in live mode since it requires a reboot to take affect.
and the setting would not be saved in live.  So you would have to do a hard drive install.

A reboot is not required, however HP laptops are the only computers affected that we know of
```
iwlist scan | egrep -i 'ssid|quality'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
```

Compare the first iwlist scan result to the second, if it is much improved the ant_sel=1 is likely the correct setting, if it is the same
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

Then see how the scan results look with ant_sel=2

---

### Post by Tony_Palermo on 2017-04-10
I will try it out right now.  Just so you know this is a Lenovo laptop.  Thank you for the help.

---

### Post by Tony_Palermo on 2017-04-10
I did the command, "[COLOR=#000000][FONT=&quot]iwlist scan | egrep -i 'ssid|quality'" [/FONT][/COLOR]Is it normal for it to say,

"[FONT=arial]enp2s0    Interface doesn't support scanning.[/FONT]

[FONT=arial]lo        Interface doesn't support scanning.[/FONT]

[FONT=arial]                    Quality=68/70  Signal level=-42 dBm  [/FONT]
[FONT=arial]                    ESSID:"Palermo""

[/FONT]

---

### Post by jeremy31 on 2017-04-11
Since it is a Lenovo
```
sudo modprobe -r rtl8723be
sodo modprobe rtl8723be fwlps=N
```

---

