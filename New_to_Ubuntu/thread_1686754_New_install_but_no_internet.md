---
title: "New install but no internet?"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by rom3lol on 2011-02-12
I just installed Ubuntu 10.10 on my friends pc but their is no Internet.
When I right click the network icon it says "Wireless Disabled".
But the network on the laptop is on.

```
udo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:7d:bf:f1
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:57:fe:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:92600000-9260ffff
```

Like I mention the wireless switch is on. What can I do?

---

### Post by rustutzman on 2011-02-12
Is it a built in wireless adapter? If so check BIOS and make sure it is enabled there.

---

### Post by thefasterblueone on 2011-02-12
If you are using NetworkManager (default to Ubuntu 10.10) right click on the icon and select "enable wireless" and let us know .

---

### Post by rom3lol on 2011-02-12
> **rustutzman said:**
> Is it a built in wireless adapter? If so check BIOS and make sure it is enabled there.

Yes it's a built in adapter. I checked Bios and the adapter was disabled so I enabled it but I still have the same problem.
Even If I connect a wireless adapter I have the same issue.
The option to enable wireless is greyed out.

I tried the following:
```
sudo ifconfig wlan0 up
```
```
SI0CSIFFLAGS: Operation not possible due to RF-Kill
```I don't know what that means?

---

### Post by rom3lol on 2011-02-12
> **thefasterblueone said:**
> If you are using NetworkManager (default to Ubuntu 10.10) right click on the icon and select "enable wireless" and let us know .

Hey yes im using it but that option is grayed out?

---

### Post by rustutzman on 2011-02-12
Try this command
```
rfkill unblock wifi
```
edit: Might need this one too:
```
ifconfig wlan0 up
```


Russ

---

### Post by rom3lol on 2011-02-12
> **rustutzman said:**
> Try this command
```
rfkill unblock wifi
```edit: Might need this one too:
```
ifconfig wlan0 up
```Russ

I tried that but it didn't work.
I tried the following:
```
iwconfig wlan0 up
wlan0 IEE 802.11bg ESSID:off/any
         Mode:Managed  Access Point: Not-Associated    Tx-Power=20 dBm
         Retry long limit:7 RTS thr:off Fragment thr:off
         Power Management:off
```

---

### Post by thefasterblueone on 2011-02-12
Try this link:

[http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html]("http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html")

---

### Post by rom3lol on 2011-02-13
> **thefasterblueone said:**
> Try this link:

[http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html](http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html)

Hey thank you very much this did the job :popcorn:
But when I restart im back at the same place?
Is it possible to edit the rfkill configuration file? So that I can log in and get too using the internet right away. 

Thanks

---

### Post by rom3lol on 2011-02-13
Well I managed too fix it. After rebooting the wireless internet wasnt working again so I followed all the directions again but ran everyting as SUDO and I got it working now :)

Love the Forum alot of good people and great help!!

---

