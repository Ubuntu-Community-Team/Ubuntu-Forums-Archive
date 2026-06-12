---
title: "Ethernet Connection No Longer Working"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by warriorfrog on 2014-12-05
I just downloaded a ton of updates and my ethernet connection won't work after reboot.  I've deleted/re-added the connection, rebooted, restarted network-manager but nothing.  Ideas?

---

### Post by mikewhatever on 2014-12-06
The idea is, you post useful info to provide clues to the problem, we try and solve it.
How about we start with the outputs of:
ifconfig
lspci
rfkill list all

---

### Post by warriorfrog on 2014-12-06
Thank you for the reply.  I'm extremely new to this.

Output from ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1d:92:b6:ee:b0  
          inet6 addr: fe80::21d:92ff:feb6:eeb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:653 (653.0 B)  TX bytes:5474 (5.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11263 (11.2 KB)  TX bytes:11263 (11.2 KB)
```


output from lspci
```
00:00.0 Host bridge: NVIDIA Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: NVIDIA Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: NVIDIA Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch (rev a2)
02:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch (rev a2)
02:02.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch (rev a2)
02:03.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch (rev a2)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450]
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV620 HDMI Audio [Radeon HD 3400 Series]

```

rfkill list all returned nothing.

---

### Post by mikewhatever on 2014-12-07
Sorry, I thoghout you were not so new, since you've mentioned all those complicated things you've done.

I see no networking devices in the output of lspci. Are you sure that's all there is?

How about the output of **sudo lshw -C network** ?

---

### Post by warriorfrog on 2014-12-07
It just says 

```
cPUID (then this goes away)
PCI (sysfs)
```

...and eventually times out and returns me to the prompt.  Everything was working fine until I updated the other evening.  I probably don't know enough about linux to be running this :\.  Thank you for the reply, I really appreciate you trying to help me!

---

### Post by matt_symes on 2014-12-07
Hi

Can you post the output of

```
lsusb
```

Kind regards

---

### Post by warriorfrog on 2014-12-07
Sure!

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 04f3:0213 Elan Microelectronics Corp. 
Bus 002 Device 003: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 002 Device 002: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by matt_symes on 2014-12-07
Hi

Is this a PC or a laptop ? Make and model please. Also make of the Ethernet controller would be useful as well would be useful.

Firstly reboot into your previous kernel from the grub menu. Do you have Ethernet ?

What does the log file say after you reboot into your newest kernel ?

```
grep eth0 /var/log/syslog | tail -n 50
```

Please post the results back here

Kind regards

---

### Post by warriorfrog on 2014-12-07
Ok I rebooted into the previous kernel (xx.39).  Networking does not work.  It just keeps trying and failing :\.  Results:

```
Dec  7 16:12:23 jml-torrent dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 (xid=0x2b495403)
Dec  7 16:12:35 jml-torrent NetworkManager[1092]: <info> (eth0): IP6 addrconf timed out or failed.
Dec  7 16:12:35 jml-torrent NetworkManager[1092]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec  7 16:12:35 jml-torrent NetworkManager[1092]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec  7 16:12:35 jml-torrent NetworkManager[1092]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec  7 16:12:37 jml-torrent dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x2b495403)
Dec  7 16:12:47 jml-torrent dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x2b495403)
Dec  7 16:12:57 jml-torrent dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0x2b495403)
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <warn> (eth0): DHCPv4 request timed out.
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2497
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <warn> Activation (eth0) failed for connection 'Auto Ethernet'
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec  7 16:13:00 jml-torrent NetworkManager[1092]: <info> (eth0): deactivating device (reason 'none') [0]
Dec  7 16:13:00 jml-torrent avahi-daemon[952]: Withdrawing address record for fe80::21d:92ff:feb6:eeb0 on eth0.
Dec  7 16:13:00 jml-torrent avahi-daemon[952]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::21d:92ff:feb6:eeb0.
Dec  7 16:13:00 jml-torrent avahi-daemon[952]: Interface eth0.IPv6 no longer relevant for mDNS.
Dec  7 16:13:02 jml-torrent avahi-daemon[952]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21d:92ff:feb6:eeb0.
Dec  7 16:13:02 jml-torrent avahi-daemon[952]: New relevant interface eth0.IPv6 for mDNS.
Dec  7 16:13:02 jml-torrent avahi-daemon[952]: Registering new address record for fe80::21d:92ff:feb6:eeb0 on eth0.*.
Dec  7 16:13:06 jml-torrent NetworkManager[1092]: <info> (eth0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Dec  7 16:13:06 jml-torrent NetworkManager[1092]: <info> (eth0): cleaning up...
Dec  7 16:13:06 jml-torrent NetworkManager[1092]: <info> (eth0): taking down device.
Dec  7 16:13:06 jml-torrent avahi-daemon[952]: Interface eth0.IPv6 no longer relevant for mDNS.
Dec  7 16:13:06 jml-torrent avahi-daemon[952]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::21d:92ff:feb6:eeb0.
Dec  7 16:13:06 jml-torrent avahi-daemon[952]: Withdrawing address record for fe80::21d:92ff:feb6:eeb0 on eth0.
Dec  7 16:31:38 jml-torrent kernel: [    1.552892] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:92:b6:ee:b0
Dec  7 16:31:38 jml-torrent kernel: [   19.974162] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 16:31:41 jml-torrent NetworkManager[1089]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Dec  7 16:31:41 jml-torrent NetworkManager[1089]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  7 16:31:42 jml-torrent NetworkManager[1089]: <info> (eth0): carrier is OFF
Dec  7 16:31:42 jml-torrent NetworkManager[1089]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Dec  7 16:31:42 jml-torrent NetworkManager[1089]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  7 17:58:06 jml-torrent kernel: [    1.568892] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:92:b6:ee:b0
Dec  7 17:58:06 jml-torrent kernel: [   20.536573] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 17:58:09 jml-torrent NetworkManager[1125]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Dec  7 17:58:09 jml-torrent NetworkManager[1125]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  7 17:58:10 jml-torrent NetworkManager[1125]: <info> (eth0): carrier is OFF
Dec  7 17:58:10 jml-torrent NetworkManager[1125]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Dec  7 17:58:10 jml-torrent NetworkManager[1125]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  7 18:00:47 jml-torrent kernel: [    1.548915] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:92:b6:ee:b0
Dec  7 18:00:47 jml-torrent kernel: [   16.828582] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 18:00:51 jml-torrent NetworkManager[1084]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Dec  7 18:00:51 jml-torrent NetworkManager[1084]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  7 18:00:51 jml-torrent NetworkManager[1084]: <info> (eth0): carrier is OFF
Dec  7 18:00:51 jml-torrent NetworkManager[1084]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Dec  7 18:00:51 jml-torrent NetworkManager[1084]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
```

"Enable Networking" wasn't checked, so I checked it and grepped the log again.  
```
Dec  7 16:31:41 jml-torrent NetworkManager[1089]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Dec  7 16:31:41 jml-torrent NetworkManager[1089]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  7 16:31:42 jml-torrent NetworkManager[1089]: <info> (eth0): carrier is OFF
Dec  7 16:31:42 jml-torrent NetworkManager[1089]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Dec  7 16:31:42 jml-torrent NetworkManager[1089]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  7 17:58:06 jml-torrent kernel: [    1.568892] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:92:b6:ee:b0
Dec  7 17:58:06 jml-torrent kernel: [   20.536573] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 17:58:09 jml-torrent NetworkManager[1125]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Dec  7 17:58:09 jml-torrent NetworkManager[1125]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  7 17:58:10 jml-torrent NetworkManager[1125]: <info> (eth0): carrier is OFF
Dec  7 17:58:10 jml-torrent NetworkManager[1125]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Dec  7 17:58:10 jml-torrent NetworkManager[1125]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  7 18:00:47 jml-torrent kernel: [    1.548915] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:92:b6:ee:b0
Dec  7 18:00:47 jml-torrent kernel: [   16.828582] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 18:00:51 jml-torrent NetworkManager[1084]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Dec  7 18:00:51 jml-torrent NetworkManager[1084]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  7 18:00:51 jml-torrent NetworkManager[1084]: <info> (eth0): carrier is OFF
Dec  7 18:00:51 jml-torrent NetworkManager[1084]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Dec  7 18:00:51 jml-torrent NetworkManager[1084]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): bringing up device.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): carrier now ON (device state 20)
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): preparing device.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) starting connection 'Auto Ethernet'
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  7 18:04:21 jml-torrent NetworkManager[1084]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec  7 18:04:21 jml-torrent dhclient: Listening on LPF/eth0/00:1d:92:b6:ee:b0
Dec  7 18:04:21 jml-torrent dhclient: Sending on   LPF/eth0/00:1d:92:b6:ee:b0
Dec  7 18:04:21 jml-torrent dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x210f8023)
Dec  7 18:04:23 jml-torrent avahi-daemon[882]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21d:92ff:feb6:eeb0.
Dec  7 18:04:23 jml-torrent avahi-daemon[882]: New relevant interface eth0.IPv6 for mDNS.
Dec  7 18:04:23 jml-torrent avahi-daemon[882]: Registering new address record for fe80::21d:92ff:feb6:eeb0 on eth0.*.
Dec  7 18:04:24 jml-torrent dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 (xid=0x210f8023)
Dec  7 18:04:28 jml-torrent dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x210f8023)
```

---

### Post by matt_symes on 2014-12-08
Hi

Is the problem that you are not getting a DCHP address ? 

Give yourself a static IP address on the same subnet as your router and then try to ping it. You can do this from network manager. Can you ping the router ?

Also, what do you get logged to the terminal if you stop network manager and try to get a DHCP IP address manually ?

Try this

```
sudo service network-manager stop
sudo dhclient eth0
```

What is logged to the terminal ?

Kind regards

---

### Post by warriorfrog on 2014-12-08
I assigned a manual IP address, stopped the service and started network-manager quite a few times while monitoring eth0.  All I was able to get is:

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
```

I really don't know what I'm doing though.  I definitely can't ping the router!  Should I re-install :|?

---

### Post by matt_symes on 2014-12-09
Hi

Did you boot into an older kernel from the grub menu ?

Can we try to identify your network card using sysfs ?

Can you post the results back for these commands.

```
cat /sys/devices/pci0000:00/0000:00:14.0/{vendor,device}
```

```
lsmod
```

As for reinstalling, that depends on how quickly you need the PC back up and running.

Kind regards

---

### Post by warriorfrog on 2014-12-15
> **matt_symes said:**
> Hi

Did you boot into an older kernel from the grub menu ?

Can we try to identify your network card using sysfs ?

Can you post the results back for these commands.

```
cat /sys/devices/pci0000:00/0000:00:14.0/{vendor,device}
```

```
lsmod
```

As for reinstalling, that depends on how quickly you need the PC back up and running.

Kind regards

I had a death in the family and was gone all week :(.  I did boot into an older kernel version.  No change.  My NIC is a Realtek 8211bl.  I identified it based on my motherboard.  The NIC is built in.

```
cat /sys/devices/pci0000:00/0000:00:14.0/{vendor,device}
0x10de
0x0269


Module                  Size  Used by
cuse                   13213  3 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
nls_utf8               12493  0 
cifs                  410382  0 
fscache                56756  1 cifs
snd_hda_codec_hdmi     45440  1 
snd_hda_codec_realtek    59259  1 
joydev                 17101  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
coretemp               13195  0 
snd_rawmidi            25135  1 snd_seq_midi
snd_hda_intel          42730  5 
kvm_intel             132620  0 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   388275  1 kvm_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
radeon               1420704  3 
ttm                    72725  1 radeon
drm_kms_helper         48868  1 radeon
soundcore              12600  1 snd
drm                   244037  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
parport_pc             31981  0 
nv_tco                 13300  0 
i2c_nforce2            13037  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
mac_hid                13037  0 
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
pata_acpi              12886  0 
usb_storage            48417  1 
psmouse                91357  0 
forcedeth              62140  0 
sata_nv                23004  1 
pata_amd               13761  4 
```

---

### Post by matt_symes on 2014-12-15
Hi

I'm really sorry to hear about your loss. My condolences.

I missed a step in post #10 when checking dhcp. Can you run these commands.

```

sudo service network-manager stop
sudo ifconfig eth0 up
sudo dhclient eth0

```

then check for an IP address with

```
ifconfig eth0
```

The above will take network manager out of the equation.

I'll look up your network adaptor for my next post.

Kind regards

---

### Post by warriorfrog on 2014-12-15
This is what it gives me after running the commands.

```
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1d:92:b6:ee:b0  
          inet6 addr: fe80::21d:92ff:feb6:eeb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3601 (3.6 KB)  TX bytes:16647 (16.6 KB)
```

Thank you for helping!!

---

