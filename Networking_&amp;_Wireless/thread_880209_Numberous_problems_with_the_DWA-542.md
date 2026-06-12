---
title: "Numberous problems with the DWA-542"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2008-08-04
Okay, I'm using Hardy Heron on a desktop. I've gotten the DWA-542 to work with ndiswrapper. The problem is though every time I restart my computer, this wireless card only works like one out of ten times. Most of the times I restart my computer and try to scan wireless networks with WICD nothing comes up. It's so random and erratic.

Also, since I've installed this wireless card, sometimes at the login  screen those drums you hear get stuck in an audio infinite loop. Even after I log in and get to my desktop. The drums just keep on going on and on and on. I never had this problem before I installed this wireless card.

Any ideas how to fix these? Especially the connection problem. It's a real nuisance. I can't get much of anything done without internet.

---

### Post by pytheas22 on 2008-08-04
Please do a fresh reboot.  If the connection is broken at that point, please run these commands and post the output:
```

iwconfig
iwlist scan
dmesg | grep -e ndis -e wlan
lshw -C Network
ndiswrapper -l
```

Hopefully with that information we can trace the problem down.

---

### Post by mahasmb on 2008-09-07
```
maha@maha-ubuntudesk:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11g  ESSID:"Basheikh"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:58:FD:61:FB   
          Bit Rate=300 Mb/s   
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

maha@maha-ubuntudesk:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan2     Scan completed :
          Cell 01 - Address: 00:13:F7:AC:55:4E
                    ESSID:"Jay"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1B:5B:77:D2:09
                    ESSID:"BELL793"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1C:F0:F5:EF:04
                    ESSID:"SWLink"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:21:29:C3:5F:EE
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:21:7C:AE:64:59
                    ESSID:"BELL924"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:1E:58:FD:61:FB
                    ESSID:"Basheikh"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:18:39:61:C7:50
                    ESSID:"linksys_SES_32270"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:1F:33:26:EB:11
                    ESSID:"791"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:18:F8:C0:C5:4E
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 10 - Address: 00:13:10:6D:84:4C
                    ESSID:"Kyle-Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 11 - Address: 00:1B:5B:87:0C:29
                    ESSID:"BELL944"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 12 - Address: 00:13:F7:01:38:92
                    ESSID:"SMC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 13 - Address: 00:13:F7:BC:BE:A0
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

maha@maha-ubuntudesk:~$ dmesg | grep -e ndis -e wlan
[   48.302415] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   49.797846] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
[   51.959779] ndiswrapper: using IRQ 22
[   52.166926] wlan0: ethernet device 00:19:5b:53:bd:95 using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
[   52.225698] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   52.235981] usbcore: registered new interface driver ndiswrapper
[   53.566482] ndiswrapper: changing interface name from 'wlan0' to 'wlan2'
[   53.566579] udev: renamed network interface wlan0 to wlan2
[   59.669623] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  106.402929] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  106.519264] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  106.793122] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  117.563000] wlan2: no IPv6 routers present
[ 1897.844059] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 1909.734416] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 1909.857726] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 1913.310270] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[ 1923.926195] wlan2: no IPv6 routers present
[11663.872485] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[11664.001888] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[11674.691688] wlan2: no IPv6 routers present
[13650.932434] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[13651.026118] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[13654.377321] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[13664.999249] wlan2: no IPv6 routers present
[13782.332825] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[13782.460390] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[13792.690327] wlan2: no IPv6 routers present
[14493.115058] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[14493.243482] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[14503.830288] wlan2: no IPv6 routers present
[14580.823439] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[14580.998772] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[14591.502576] wlan2: no IPv6 routers present
maha@maha-ubuntudesk:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:e0:4d:7b:51:0c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: wlan2
       version: 01
       serial: 00:19:5b:53:bd:95
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,08/28/2006,6.0.1.75 latency=128 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
maha@maha-ubuntudesk:~$ sudo lshw -C Network
[sudo] password for maha: 
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:e0:4d:7b:51:0c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: wlan2
       version: 01
       serial: 00:19:5b:53:bd:95
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,08/28/2006,6.0.1.75 latency=128 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
maha@maha-ubuntudesk:~$ ndiswrapper -l
net5416 : driver installed
	device (168C:0023) present
sis163u : driver installed
maha@maha-ubuntudesk:~$ 
```

---

### Post by pytheas22 on 2008-09-07
How often does this problem keep occurring?  When it does happen, can you make the wireless work again by using these commands:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

Wait a few seconds, and see if you can connect again.

I don't see anything in the output above that definitely indicates what's wrong, but hopefully simply reinserting the ndiswrapper module (using the commands above) will be enough to fix this problem.

---

### Post by mahasmb on 2008-09-14
When I reboot the computer and it doesn't show any wireless networks (and thus doesn't let me connect), I try to open terminal but... Well, terminal takes a few minutes to actually open up and when it does, it just disappears from the screen in a second. I also sometimes can't even click on the Logout icon at the upper right hand corner of the screen to restart. It seems to me that something very strange is going on. And the only way I know to get wireless working again, is to log into Windows, get myself connected to my network on Windows (it never connects automatically. I always have to go to 'repair connection' in Network Magic) and then reboot and only then can I connect in Ubuntu. It is very strange. Very strange and annoying.

If anyone can help me out with this, I'd very much appreciate it.

---

### Post by pytheas22 on 2008-09-14
Your terminal should not be crashing.  It sounds like there's a major problem.  Perhaps it would be simplest just to reinstall Ubuntu--it only takes half an hour, which is probably a lot less time than you'd need to fix the existing installation.

If you do want to try to fix the existing system, the first place to look is the system logs (System>Administration>System Log).  Does it mention any errors?  If you're not sure what you're looking at, you can copy the log here by pressing alt-F2, typing "gedit /var/log/syslog," and copying the file that opens up here.

---

### Post by mahasmb on 2008-09-24
Here's my syslog file:

```
Sep 24 16:03:27 maha-ubuntudesk syslogd 1.5.0#1ubuntu1: restart.
Sep 24 16:03:27 maha-ubuntudesk anacron[5612]: Job `cron.daily' terminated
Sep 24 16:03:27 maha-ubuntudesk anacron[5612]: Normal exit (1 job run)
Sep 24 16:07:10 maha-ubuntudesk kernel: [  928.513382] operapluginwrap[9813]: segfault at 00000029 eip b76c4a8b esp bfe4f5e0 error 4
```

Also, running "sudo rmmod ndiswrapper" totally and completely freezes up my computer. I've tried it twice, and both times it froze everything. I couldn't type anything or click on anything.

> **pytheas22 said:**
> How often does this problem keep occurring?  When it does happen, can you make the wireless work again by using these commands:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

Wait a few seconds, and see if you can connect again.

I don't see anything in the output above that definitely indicates what's wrong, but hopefully simply reinserting the ndiswrapper module (using the commands above) will be enough to fix this problem.

---

### Post by pytheas22 on 2008-09-24
Is that your whole syslog file?  Generally the file is much, much larger, so this reinforces the conclusion that something is seriously wrong with your system.

If you press alt-F2 and type:
```

dmesg > ~/Desktop/dmesg.log
```

a file should appear on your desktop called 'dmesg.log'.  Could you please post the contents of that here?  That would further help to figure out what's wrong.

Again, though, if I were you I'd probably just consider reinstalling Ubuntu (check the installation CD for defects first), unless you have a lot of work and data already invested in your existing installation.

---

### Post by mahasmb on 2008-09-26
I'd really rather not re-install. It would take me forever to get everything back to the way I want it and I simply don't have that time right now.

Also, pressing alt+F2, pasting "dmesg > ~/Desktop/dmesg.log", and pressing "run"... does nothing...

Can you be sure this is indeed a software problem? Because if it's hardware, reinstalling would just be a waste of time. But if you really think reinstalling would really help I can give it a try in a week or so.

Edit: However, "gedit ~/Desktop/dmesg.log" supplies me with the following

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3d60
[    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261856
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261856
[    0.000000] On node 0 totalpages: 261856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F50 checksum 0
[    0.000000] ACPI: RSDP 000F7F50, 0014 (r0 P4M900)
[    0.000000] ACPI: RSDT 3FEE3000, 0034 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEE3080, 0074 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEE3100, 62D0 (r1 P4M900 AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 3FEE0000, 0040
[    0.000000] ACPI: HPET 3FEE94C0, 0038 (r1 P4M900 AWRDACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 3FEE9500, 003C (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEE9400, 0090 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 5, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfe800000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259811
[    0.000000] Kernel command line: root=UUID=35c7a991-155a-459a-a6bf-6c69d95057e7 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3000.035 MHz processor.
[   24.049996] Console: colour VGA+ 80x25
[   24.050000] console [tty0] enabled
[   24.050342] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.050705] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.077709] Memory: 1026328k/1047424k available (2157k kernel code, 20420k reserved, 998k data, 364k init, 129920k highmem)
[   24.077718] virtual kernel memory layout:
[   24.077719]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.077720]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.077721]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.077722]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.077723]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   24.077724]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   24.077725]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   24.077728] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.077770] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   24.077867] hpet clockevent registered
[   24.157792] Calibrating delay using timer specific routine.. 6004.68 BogoMIPS (lpj=12009368)
[   24.157815] Security Framework initialized
[   24.157821] SELinux:  Disabled at boot.
[   24.157837] AppArmor: AppArmor initialized
[   24.157841] Failure registering capabilities with primary security module.
[   24.157850] Mount-cache hash table entries: 512
[   24.157992] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   24.158003] monitor/mwait feature present.
[   24.158005] using mwait in idle threads.
[   24.158012] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   24.158014] CPU: L2 cache: 1024K
[   24.158017] CPU: Physical Processor ID: 0
[   24.158019] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   24.158031] Compat vDSO mapped to ffffe000.
[   24.158048] Checking 'hlt' instruction... OK.
[   24.174235] SMP alternatives: switching to UP code
[   24.176150] Early unpacking initramfs... done
[   24.470537] ACPI: Core revision 20070126
[   24.470597] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.475073] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   24.475094] SMP alternatives: switching to SMP code
[   24.475897] Booting processor 1/1 eip 3000
[   24.486009] Initializing CPU#1
[   24.565381] Calibrating delay using timer specific routine.. 6000.00 BogoMIPS (lpj=12000013)
[   24.565391] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   24.565398] monitor/mwait feature present.
[   24.565405] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   24.565408] CPU: L2 cache: 1024K
[   24.565411] CPU: Physical Processor ID: 0
[   24.565413] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   24.565792] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   24.565839] Total of 2 processors activated (12004.69 BogoMIPS).
[   24.566177] ENABLING IO-APIC IRQs
[   24.566366] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.713375] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   24.733374] Brought up 2 CPUs
[   24.733401] CPU0 attaching sched-domain:
[   24.733405]  domain 0: span 03
[   24.733407]   groups: 01 02
[   24.733411]   domain 1: span 03
[   24.733413]    groups: 03
[   24.733416] CPU1 attaching sched-domain:
[   24.733418]  domain 0: span 03
[   24.733420]   groups: 02 01
[   24.733423]   domain 1: span 03
[   24.733425]    groups: 03
[   24.733700] net_namespace: 64 bytes
[   24.733711] Booting paravirtualized kernel on bare hardware
[   24.734365] Time:  0:04:52  Date: 09/26/08
[   24.734392] NET: Registered protocol family 16
[   24.734672] EISA bus registered
[   24.734680] ACPI: bus type pci registered
[   24.742526] PCI: PCI BIOS revision 3.00 entry at 0xfa7d0, last bus=128
[   24.742529] PCI: Using configuration type 1
[   24.742530] Setting up standard PCI resources
[   24.746099] ACPI: EC: Look up EC in DSDT
[   24.754645] ACPI: Interpreter enabled
[   24.754650] ACPI: (supports S0 S1 S4 S5)
[   24.754667] ACPI: Using IOAPIC for interrupt routing
[   24.763967] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.765943] PCI: Transparent bridge - 0000:00:13.1
[   24.765984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.766282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[   24.766413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   24.766542] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[   24.822832] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   24.822999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   24.823622] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   24.823826] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   24.824034] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
[   24.824238] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
[   24.824419] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.824597] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.824773] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.824962] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
[   24.825155] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.825200] pnp: PnP ACPI init
[   24.825209] ACPI: bus type pnp registered
[   24.830938] pnp: PnP ACPI: found 19 devices
[   24.830941] ACPI: ACPI bus type pnp unregistered
[   24.830946] PnPBIOS: Disabled by ACPI PNP
[   24.831259] PCI: Using ACPI for IRQ routing
[   24.831263] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.872072] NET: Registered protocol family 8
[   25.872075] NET: Registered protocol family 20
[   25.872119] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
[   25.872126] hpet0: 3 32-bit timers, 14318180 Hz
[   25.873169] AppArmor: AppArmor Filesystem Enabled
[   25.876058] Time: tsc clocksource has been installed.
[   25.876071] Switched to high resolution mode on CPU 0
[   25.876207] Switched to high resolution mode on CPU 1
[   25.888057] system 00:01: ioport range 0x400-0x47f has been reserved
[   25.888060] system 00:01: ioport range 0x500-0x50f has been reserved
[   25.888068] system 00:02: iomem range 0xf0001000-0xf0001fff has been reserved
[   25.888075] system 00:03: iomem range 0xf0002000-0xf0002fff has been reserved
[   25.888082] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   25.888085] system 00:04: ioport range 0x800-0x805 has been reserved
[   25.888087] system 00:04: ioport range 0x290-0x297 has been reserved
[   25.888090] system 00:04: ioport range 0x880-0x88f has been reserved
[   25.888105] system 00:0f: iomem range 0xf0000000-0xf0000fff has been reserved
[   25.888112] system 00:10: iomem range 0xe0000000-0xefffffff could not be reserved
[   25.888121] system 00:12: iomem range 0xf0000-0xfffff could not be reserved
[   25.888124] system 00:12: iomem range 0xfe800000-0xfe8000ff has been reserved
[   25.888127] system 00:12: iomem range 0x3fee0000-0x3fefffff could not be reserved
[   25.888130] system 00:12: iomem range 0xffff0000-0xffffffff could not be reserved
[   25.888133] system 00:12: iomem range 0x0-0x9ffff could not be reserved
[   25.888136] system 00:12: iomem range 0x100000-0x3fedffff could not be reserved
[   25.888139] system 00:12: iomem range 0xfec00000-0xfec00fff could not be reserved
[   25.888142] system 00:12: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.888145] system 00:12: iomem range 0xfff80000-0xfffeffff could not be reserved
[   25.918710] PCI: Bridge: 0000:00:01.0
[   25.918714]   IO window: c000-cfff
[   25.918720]   MEM window: fdc00000-fdcfffff
[   25.918725]   PREFETCH window: fdb00000-fdbfffff
[   25.918733] PCI: Bridge: 0000:00:02.0
[   25.918736]   IO window: b000-bfff
[   25.918741]   MEM window: f8000000-fbffffff
[   25.918746]   PREFETCH window: c0000000-cfffffff
[   25.918751] PCI: Bridge: 0000:00:03.0
[   25.918754]   IO window: a000-afff
[   25.918760]   MEM window: fde00000-fdefffff
[   25.918765]   PREFETCH window: fdd00000-fddfffff
[   25.918771] PCI: Bridge: 0000:00:13.1
[   25.918774]   IO window: 9000-9fff
[   25.918779]   MEM window: fda00000-fdafffff
[   25.918784]   PREFETCH window: fd900000-fd9fffff
[   25.918804] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.918827] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
[   25.918834] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.918854] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
[   25.918860] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.918875] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   25.918888] NET: Registered protocol family 2
[   25.956018] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.956334] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.956916] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.957235] TCP: Hash tables configured (established 131072 bind 65536)
[   25.957238] TCP reno registered
[   25.968112] checking if image is initramfs... it is
[   26.548819] Freeing initrd memory: 7280k freed
[   26.549797] audit: initializing netlink socket (disabled)
[   26.549816] audit(1222387492.420:1): initialized
[   26.550032] highmem bounce pool size: 64 pages
[   26.552523] VFS: Disk quotas dquot_6.5.1
[   26.552624] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.552779] io scheduler noop registered
[   26.552782] io scheduler anticipatory registered
[   26.552784] io scheduler deadline registered
[   26.552796] io scheduler cfq registered (default)
[   26.552811] PCI: VIA PCI bridge detected. Disabling DAC.
[   26.552895] Boot video device is 0000:02:00.0
[   26.553055] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.553104] assign_interrupt_mode Found MSI capability
[   26.553161] Allocate Port Service[0000:00:02.0:pcie00]
[   26.553208] Allocate Port Service[0000:00:02.0:pcie02]
[   26.553317] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   26.553373] assign_interrupt_mode Found MSI capability
[   26.553435] Allocate Port Service[0000:00:03.0:pcie00]
[   26.553481] Allocate Port Service[0000:00:03.0:pcie02]
[   26.553830] isapnp: Scanning for PnP cards...
[   26.907572] isapnp: No Plug & Play device found
[   26.945497] Real Time Clock Driver v1.12ac
[   26.945735] hpet_resources: 0xfe800000 is busy
[   26.945763] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.945898] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.946803] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.947905] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.947996] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.948147] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   26.948539] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.948546] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.971080] mice: PS/2 mouse device common for all mice
[   26.971251] EISA: Probing bus 0 at eisa.0
[   26.971295] EISA: Detected 0 cards.
[   26.971298] cpuidle: using governor ladder
[   26.971301] cpuidle: using governor menu
[   26.971384] NET: Registered protocol family 1
[   26.971417] Using IPI No-Shortcut mode
[   26.971448] registered taskstats version 1
[   26.971559]   Magic number: 8:481:52
[   26.971687] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.971690] EDD information not available.
[   26.971893] Freeing unused kernel memory: 364k freed
[   26.990195] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   28.358235] fuse init (API version 7.9)
[   28.376121] ACPI: Fan [FAN] (on)
[   28.383526] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.383541] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.385399] ACPI: Thermal Zone [THRM] (55 C)
[   29.120425] usbcore: registered new interface driver usbfs
[   29.120543] usbcore: registered new interface driver hub
[   29.121548] usbcore: registered new device driver usb
[   29.122645] SCSI subsystem initialized
[   29.153761] USB Universal Host Controller Interface driver v3.0
[   29.153874] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 18
[   29.153891] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   29.154178] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   29.154215] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000e000
[   29.154416] usb usb1: configuration #1 chosen from 1 choice
[   29.154456] hub 1-0:1.0: USB hub found
[   29.154467] hub 1-0:1.0: 2 ports detected
[   29.165838] libata version 3.00 loaded.
[   29.257779] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 19
[   29.257801] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   29.257845] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   29.257878] uhci_hcd 0000:00:10.1: irq 19, io base 0x0000dc00
[   29.258053] usb usb2: configuration #1 chosen from 1 choice
[   29.258094] hub 2-0:1.0: USB hub found
[   29.258105] hub 2-0:1.0: 2 ports detected
[   29.285346] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   29.285358] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   29.361974] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 20
[   29.362027] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   29.362136] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.362211] uhci_hcd 0000:00:10.2: irq 20, io base 0x0000d800
[   29.362597] usb usb3: configuration #1 chosen from 1 choice
[   29.362644] hub 3-0:1.0: USB hub found
[   29.362654] hub 3-0:1.0: 2 ports detected
[   29.441584] Floppy drive(s): fd0 is 1.44M
[   29.462682] FDC 0 is a post-1991 82077
[   29.465526] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 21
[   29.465543] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   29.465580] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   29.465612] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[   29.465784] usb usb4: configuration #1 chosen from 1 choice
[   29.465825] hub 4-0:1.0: USB hub found
[   29.465834] hub 4-0:1.0: 2 ports detected
[   29.497409] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   29.570393] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 20
[   29.570419] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   29.570464] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   29.570515] ehci_hcd 0000:00:10.4: irq 20, io mem 0xfdfff000
[   29.625231] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.625419] usb usb5: configuration #1 chosen from 1 choice
[   29.625461] hub 5-0:1.0: USB hub found
[   29.625474] hub 5-0:1.0: 8 ports detected
[   29.729342] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 20
[   29.729413] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   29.730570] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 21
[   29.734892] eth0: VIA Rhine II at 0xfdffe000, 00:e0:4d:7b:51:0c, IRQ 21.
[   29.735603] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[   29.737016] pata_via 0000:00:0f.1: version 0.3.3
[   29.741939] scsi0 : pata_via
[   29.742483] scsi1 : pata_via
[   29.744163] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[   29.744167] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[   29.951510] ata1.01: ATA-8: WDC WD5000AAKB-00YSA0, 12.01C02, max UDMA/100
[   29.951517] ata1.01: 976773168 sectors, multi 16: LBA48 
[   29.965655] ata1.01: configured for UDMA/100
[   30.027862] usb 1-1: device not accepting address 2, error -71
[   30.447740] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL13, max UDMA/33
[   30.447769] ata2.01: ATAPI: CD-ROM CDU701-F, 1.0r, max MWDMA2
[   30.620687] ata2.00: configured for UDMA/33
[   30.791263] ata2.01: configured for MWDMA2
[   30.791416] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 12.0 PQ: 0 ANSI: 5
[   30.795200] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL13 PQ: 0 ANSI: 5
[   30.796107] scsi 1:0:1:0: CD-ROM            SONY     CD-ROM CDU701-F  1.0r PQ: 0 ANSI: 5
[   30.796520] sata_via 0000:00:0f.0: version 2.3
[   30.796539] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 20
[   30.796584] sata_via 0000:00:0f.0: routed to hard irq line 11
[   30.796646] scsi2 : sata_via
[   30.796896] scsi3 : sata_via
[   30.799082] ata3: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 20
[   30.799087] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 20
[   31.002809] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   31.214590] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   31.242763] Driver 'sd' needs updating - please use bus_type methods
[   31.242888] sd 0:0:1:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.242920] sd 0:0:1:0: [sda] Write Protect is off
[   31.242927] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   31.242977] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.243068] sd 0:0:1:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.243085] sd 0:0:1:0: [sda] Write Protect is off
[   31.243089] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   31.243118] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.243124]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   31.248844]  sda1 sda2 sda3 sda4
[   31.260203] sd 0:0:1:0: [sda] Attached SCSI disk
[   31.266673] sd 0:0:1:0: Attached scsi generic sg0 type 0
[   31.266718] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   31.266751] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   31.278798] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.278807] Uniform CD-ROM driver Revision: 3.20
[   31.278910] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   31.282674] sr1: scsi3-mmc drive: 14x/32x cd/rw xa/form2 cdda tray
[   31.282761] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   31.597226] Attempting manual resume
[   31.597230] swsusp: Resume From Partition 8:3
[   31.597232] PM: Checking swsusp image.
[   31.597463] PM: Resume from disk failed.
[   31.638808] kjournald starting.  Commit interval 5 seconds
[   31.638817] EXT3-fs: mounted filesystem with ordered data mode.
[   31.642172] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   31.820727] usb 1-1: configuration #1 chosen from 1 choice
[   32.061730] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   32.239318] usb 1-2: configuration #1 chosen from 1 choice
[   32.242225] hub 1-2:1.0: USB hub found
[   32.244198] hub 1-2:1.0: 3 ports detected
[   32.562883] usb 1-2.1: new full speed USB device using uhci_hcd and address 6
[   32.700863] usb 1-2.1: configuration #1 chosen from 1 choice
[   37.799958] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.860304] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.305070] input: Power Button (FF) as /devices/virtual/input/input2
[   38.331256] ACPI: Power Button (FF) [PWRF]
[   38.331643] input: Power Button (CM) as /devices/virtual/input/input3
[   38.359306] ACPI: Power Button (CM) [PWRB]
[   38.359444] input: Sleep Button (CM) as /devices/virtual/input/input4
[   38.395274] ACPI: Sleep Button (CM) [SLPB]
[   40.041444] eth0: link down
[   40.438290] Linux agpgart interface v0.102
[   40.708938] Bluetooth: Core ver 2.11
[   40.767878] NET: Registered protocol family 31
[   40.767883] Bluetooth: HCI device and connection manager initialized
[   40.767889] Bluetooth: HCI socket layer initialized
[   40.816836] Bluetooth: HCI USB driver ver 2.9
[   40.819678] usbcore: registered new interface driver hci_usb
[   41.011319] nvidia: module license 'NVIDIA' taints kernel.
[   41.469159] usbcore: registered new interface driver hiddev
[   41.521293] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   41.572102] input: Saitek PLC Cyborg Force Rumble Pad as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/input/input6
[   41.572148] input,hidraw0: USB HID v1.10 Joystick [Saitek PLC Cyborg Force Rumble Pad] on usb-0000:00:10.0-1
[   41.572180] usbcore: registered new interface driver usbhid
[   41.572187] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.572380] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   41.647937] NET: Registered protocol family 17
[   42.360001] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
[   42.360354] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 17 (level, low) -> IRQ 22
[   42.836855] ndiswrapper: using IRQ 22
[   42.908112] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   42.962771] parport_pc 00:0c: reported by Plug and Play ACPI
[   42.962890] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.092017] wlan0: ethernet device 00:19:5b:53:bd:95 using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
[   43.157793] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   43.157892] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 23
[   43.157907] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   43.158135] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   43.159836] ACPI: PCI Interrupt 0000:80:01.0[A] -> GSI 17 (level, low) -> IRQ 22
[   43.159868] PCI: Setting latency timer of device 0000:80:01.0 to 64
[   43.243463] usbcore: registered new interface driver ndiswrapper
[   44.494357] ndiswrapper: changing interface name from 'wlan0' to 'wlan2'
[   44.494539] udev: renamed network interface wlan0 to wlan2
[   44.879251] lp0: using parport0 (interrupt-driven).
[   44.948381] Adding 1574360k swap on /dev/sda3.  Priority:-1 extents:1 across:1574360k
[   45.510539] EXT3 FS on sda2, internal journal
[   47.507802] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.004831] No dock devices found.
[   50.075697] NET: Registered protocol family 10
[   50.076208] lo: Disabled Privacy Extensions
[   50.077073] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.077560] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   50.313136] ppdev: user-space parallel port driver
[   50.496462] audit(1222401917.767:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5371 profile="/usr/sbin/cupsd" namespace="default"
[   50.547259] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.547266] apm: disabled - APM is not SMP safe.
[   51.268947] Bluetooth: L2CAP ver 2.9
[   51.268954] Bluetooth: L2CAP socket layer initialized
[   51.394025] Bluetooth: RFCOMM socket layer initialized
[   51.394048] Bluetooth: RFCOMM TTY layer initialized
[   51.394053] Bluetooth: RFCOMM ver 1.8
[   58.665756] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   58.785143] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   59.174263] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[   60.077465] hda-intel: Invalid position buffer, using LPIB read method instead.
[   69.231711] wlan2: no IPv6 routers present
[ 4895.493850] operapluginwrap[6540]: segfault at 000022d9 eip b76bda8b esp bfe380d0 error 4
```

---

### Post by pytheas22 on 2008-09-26
Since you're having weird issues regarding several different parts of your hardware (wireless card unreliable, infinite audio loop, windows not opening), I would be likely to conclude that it's a software issue.  Generally if you're dealing with hardware failure, you should only see problems with one particular piece of hardware (unless more than one is failing, which is unlikely).

However I did see this message in your dmesg output:

```
via-rhine: Broken BIOS detected, avoid_D3 enabled.

```

I googled a bit for that and it seems to be not necessarily a hardware problem as much as a kernel bug.  Someone in [this thread]("http://ubuntuforums.org/archive/index.php/t-629054.html") for example says:
> 
I've scanned through your dmesg output, and found one potential issue:


[ 26.016546] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[ 26.016606] via-rhine: Broken BIOS detected, avoid_D3 enabled.
I have had a look into the forums for a couple of other distributions, and it would appear Mepis and others are having a problem with the latest 2.6 kernels and Via Rhine chipsets and BIOS, as well. If your motherboard's BIOS has an option for a Plug-n-Play (PNP) OS, try enabling that and see if that helps the problem any. This option tells the BIOS to allow the operating system to initialize non-boot devices instead of the bugged MB BIOS.

UPDATE: It would appear to indeed be a kernel bug (in the 2.6.18 - 2.6.22 kernels). Here's a link ([http://lists.debian.org/debian-kernel/2007/09/msg00285.html](http://lists.debian.org/debian-kernel/2007/09/msg00285.html)) to the Debian lists page regarding poor Via SATA performance with this issue.

My advice, if this solution doesn't work (or there's no supporting BIOS option), is to revert to 6.06 LTS and stick with it until a few months after 8.04 LTS is released in April. The LTS (Long-Term Support) releases have their main focus in the stability department, whereas the others are usually technology preview and non-critical improvement releases, and many have stability issues to boot.

Another option would be using Windows to download and apply a firmware update to your BIOS chip (WARNING: This is very risky. If the power goes out or another problem interrupts the BIOS update, your machine could be unusable until the chip's replaced. Proceed with caution.)

So you may want to try what that user recommends to see if it makes a difference.  Otherwise, the best thing I can recommend is to reinstall, but that's only because I don't have any other good ideas.  Nothing else in your 'dmesg' output suggests a problem.

---

