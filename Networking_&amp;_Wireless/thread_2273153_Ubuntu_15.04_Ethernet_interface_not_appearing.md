---
title: "Ubuntu 15.04 Ethernet interface not appearing"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by hedm5643 on 2015-04-11
All of a sudden Ethernet stopped working.  Originally the network dropdown in the panel said 

```

Ethernet Networks
Ethernet Connection 1
Disconnect

```

with all three lines grayed out and unselectable.

Well, I started with the turn it off and back on again, and that did nothing.  After searching and performing most of what I could find on the forums, still nothing.

Command outputs:

```
paul@serenity:~$ ifconfig -alo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:807128 (807.1 KB)  TX bytes:807128 (807.1 KB)


wlan0     Link encap:Ethernet  HWaddr 1c:3e:84:94:82:27  
          inet addr:10.16.137.25  Bcast:10.19.255.255  Mask:255.252.0.0
          inet6 addr: fe80::1e3e:84ff:fe94:8227/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148510352 (148.5 MB)  TX bytes:10746712 (10.7 MB)



```

Originally:

```
paul@serenity:~$ cat /etc/network/interfaces# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

But at the advice of the forums I edited and it is now:

```

paul@serenity:~$ cat /etc/network/interfaces# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

```
paul@serenity:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```


```
paul@serenity:~$ sudo lshw -C network[sudo] password for paul: 
  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:e0400000-e0403fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 1c:3e:84:94:82:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.19.0-12-generic firmware=610.812 ip=10.16.137.25 link=yes multicast=yes wireless=IEEE 802.11bgn



```

```
paul@serenity:~$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
```

```
paul@serenity:~$ grep -i 'eth' /var/log/syslog | tail -20Apr 10 22:13:26 serenity dhclient: Error getting hardware address for "eth0": No such device
Apr 10 22:13:26 serenity networking[685]: Error getting hardware address for "eth0": No such device
Apr 10 22:13:26 serenity networking[685]: Failed to bring up eth0.
Apr 10 22:13:30 serenity NetworkManager[874]: <info> guessed connection type (eth0) = 802-3-ethernet
Apr 10 22:13:30 serenity NetworkManager[874]: <info> update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Apr 10 22:13:30 serenity NetworkManager[874]: <info> adding eth0 to connections
Apr 10 22:13:30 serenity NetworkManager[874]: <info> adding iface eth0 to eni_ifaces
Apr 10 22:13:30 serenity kernel: [   41.245373] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 10 22:13:31 serenity NetworkManager[874]: <info> new connection /etc/NetworkManager/system-connections/Ethernet connection 1
Apr 10 22:13:31 serenity NetworkManager[874]: <info> new connection /etc/NetworkManager/system-connections/Auto Ethernet
Apr 10 22:41:17 serenity networking[5222]: Cannot find device "eth0"
Apr 10 22:41:17 serenity dhclient: Error getting hardware address for "eth0": No such device
Apr 10 22:41:17 serenity networking[5222]: Error getting hardware address for "eth0": No such device
Apr 10 22:41:17 serenity networking[5222]: Failed to bring up eth0.
Apr 10 22:42:07 serenity NetworkManager[5475]: <info> guessed connection type (eth0) = 802-3-ethernet
Apr 10 22:42:07 serenity NetworkManager[5475]: <info> update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Apr 10 22:42:07 serenity NetworkManager[5475]: <info> adding eth0 to connections
Apr 10 22:42:07 serenity NetworkManager[5475]: <info> adding iface eth0 to eni_ifaces
Apr 10 22:42:07 serenity NetworkManager[5475]: <info> new connection /etc/NetworkManager/system-connections/Ethernet connection 1
Apr 10 22:42:07 serenity NetworkManager[5475]: <info> new connection /etc/NetworkManager/system-connections/Auto Ethernet



```


Any assistance would be greatly appreciated.

---

### Post by chili555 on 2015-04-11
```
paul@serenity:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
```We see no ethernet device there at all! It seems that there are a few possibilities. First, is it one of the few devices that are not PCI but USB and attached to an internal USB bus? Let's look:```
lsusb
```Second, look around in the BIOS and see if there are any settings related to PCI or ethernet that need to be reset to show the device.

Next, I'd ordinarily suggest checking to see if the PCI card was properly seated in it's slot; however, I believe this is a laptop. The ethernet device is, I believe integrated into the motherboard and not a separate PCI card.

Finally, the last possibility is that the card has failed.

---

### Post by hedm5643 on 2015-04-12
After shutting down and leaving it down for a few hours, I brought it back up and it started working again.  Very strange.

---

