---
title: "Airplane mode activates automatically and disables bluetooth, and wifi does not work"
date: 2020-11-18
forum: Networking &amp; Wireless
---

### Post by guiinow on 2020-11-18
I'm using a HP laptop running the new **Ubuntu 20.10 groovy gorilla**


My **kernel version is 5.8.0-29-generic**


Everything was fine until today, when airplane mode started to turn on automatically and disable bluetooh, or if I turn the bluetooh on, the airplane mode turns of. 


But the main problem is that the wifi doesn't work, it doesn't show on the configurations UI. 


The output for rfkill list all is: 
```
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```


And for iwconfig is: 
```
lo        no wireless extensions.


enx00a0c6000000  no wireless extensions.
```
And also for sudo lshw -C network is: 
```
*-network UNCLAIMED       
       description: Network controller
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:df100000-df10ffff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:2
       logical name: enx00a0c6000000
       serial: 00:a0:c6:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=ZTE CDC Ethernet Device ip=192.168.1.179 link=yes multicast=yes


```


Any help would be very welcome.

---

