---
title: "Wired network suddenly stopped working after reboot"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by skipx on 2014-01-06
My system got stuck, I had to shut it down with the powerbutton. After booting it again my wifi works but wired seems stuck. It does try to connect and all, but no luck. 
Using MBP 13.10 on an MacBook Pro. Upgrading to Ubuntu 13.11 did not solve the problem. Neither did disabling IPV6 (that helped me once with a diferent PC with a similar problem).

tail -f /var/log/syslog gives me (in a loop):

```
Jan  6 22:31:32 abort-mbp NetworkManager[5595]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  6 22:31:32 abort-mbp dhclient: Listening on LPF/eth0/00:23:32:cb:a9:2a
Jan  6 22:31:32 abort-mbp dhclient: Sending on   LPF/eth0/00:23:32:cb:a9:2a
Jan  6 22:31:32 abort-mbp dhclient: Sending on   Socket/fallback
Jan  6 22:31:32 abort-mbp dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xe55a8b9)
Jan  6 22:31:35 abort-mbp dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 (xid=0xe55a8b9)
Jan  6 22:31:39 abort-mbp dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 (xid=0xe55a8b9)
Jan  6 22:31:44 abort-mbp dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 (xid=0xe55a8b9)
Jan  6 22:31:56 abort-mbp dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 (xid=0xe55a8b9)
Jan  6 22:32:08 abort-mbp dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 (xid=0xe55a8b9)
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <warn> (eth0): DHCPv4 request timed out.
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> (eth0): canceled DHCP transaction, DHCP client pid 5952
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> Marking connection 'duhs' invalid.
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <warn> Activation (eth0) failed for connection 'duhs'
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan  6 22:32:17 abort-mbp NetworkManager[5595]: <info> (eth0): deactivating device (reason 'none') [0]

```

$ uname -a
```
Linux abort-mbp 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

$ lspci

```

00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: NVIDIA Corporation G96M [GeForce 9600M GT] (rev a1)
03:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400M] (rev b1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 06)

```

---

### Post by varunendra on 2014-01-08
Please post -
```
sudo lshw -numeric -C network
```

If the driver happens to be 'forcedeth', try this -
```
sudo modprobe -rv forcedeth
sudo modprobe -v forcedeth msi=0 msix=0
```
Post back if it returns any errors. If not, can you connect with above? The above is a temporary change that will be lost at next boot. It can be made permanent if helps.

---

### Post by skipx on 2014-01-11
I got (snibit):
```

capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s

```

And thus followed your advice without errors. 
But then the error keeps returning..
BUT i also seem to get some kind of kernel panic. And after testing in OS X (dual installation but rarely using OS X) the card seem to have the same problem. It shows it exist but can't get a working connection. When I use an USB ethernet dongle with the same ethernet cable all works flawlessly. So maybe my ethernet port is just damaged..

EDIT: the kernel panic had to do with the advice above, after reboot it disappeared.

```

Jan 11 10:40:18 abort-mbp kernel: [150604.269160] Hardware name: Apple Inc. MacBookPro5,1/Mac-F42D86C8, BIOS    MBP51.88Z.007E.B06.1202061253 02/06/12
Jan 11 10:40:18 abort-mbp kernel: [150604.269163]  0000000000000009 ffff88022d8bbd88 ffffffff816e7335 0000000000000000
Jan 11 10:40:18 abort-mbp kernel: [150604.269168]  ffff88022d8bbdc0 ffffffff81061dcd ffff88023f78d000 ffff88022c890480
Jan 11 10:40:18 abort-mbp kernel: [150604.269172]  0000000000000097 ffff88022c8903c0 0000000000000001 ffff88022d8bbdd0
Jan 11 10:40:18 abort-mbp kernel: [150604.269176] Call Trace:
Jan 11 10:40:18 abort-mbp kernel: [150604.269186]  [<ffffffff816e7335>] dump_stack+0x45/0x56
Jan 11 10:40:18 abort-mbp kernel: [150604.269192]  [<ffffffff81061dcd>] warn_slowpath_common+0x7d/0xa0
Jan 11 10:40:18 abort-mbp kernel: [150604.269197]  [<ffffffff81061eaa>] warn_slowpath_null+0x1a/0x20
Jan 11 10:40:18 abort-mbp kernel: [150604.269217]  [<ffffffffa00b5409>] cfg80211_roamed+0x89/0x90 [cfg80211]
Jan 11 10:40:18 abort-mbp kernel: [150604.269264]  [<ffffffffa02edea5>] wl_bss_connect_done.isra.21+0x105/0x1b0 [wl]
Jan 11 10:40:18 abort-mbp kernel: [150604.269304]  [<ffffffffa02ee14c>] wl_notify_connect_status+0x1fc/0x410 [wl]
Jan 11 10:40:18 abort-mbp kernel: [150604.269345]  [<ffffffffa02ed445>] wl_event_handler+0x55/0x1f0 [wl]
Jan 11 10:40:18 abort-mbp kernel: [150604.269385]  [<ffffffffa02ed3f0>] ? wl_cfg80211_scan+0x350/0x350 [wl]
Jan 11 10:40:18 abort-mbp kernel: [150604.269391]  [<ffffffff81084740>] kthread+0xc0/0xd0
Jan 11 10:40:18 abort-mbp kernel: [150604.269395]  [<ffffffff81084680>] ? kthread_create_on_node+0x120/0x120
Jan 11 10:40:18 abort-mbp kernel: [150604.269401]  [<ffffffff816f716c>] ret_from_fork+0x7c/0xb0
Jan 11 10:40:18 abort-mbp kernel: [150604.269405]  [<ffffffff81084680>] ? kthread_create_on_node+0x120/0x120
Jan 11 10:40:18 abort-mbp kernel: [150604.269408] ---[ end trace 8b617a2f4b12a4a1 ]---
Jan 11 10:40:18 abort-mbp kernel: [150604.468161] ------------[ cut here ]------------
Jan 11 10:40:18 abort-mbp kernel: [150604.468206] WARNING: CPU: 1 PID: 406 at /build/buildd/linux-3.11.0/net/wireless/sme.c:795 cfg80211_roamed+0x89/0x90 [cfg80211]()
Jan 11 10:40:18 abort-mbp kernel: [150604.468209] Modules linked in: forcedeth asix usbnet mii hidp pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) parport_pc ppdev rfcomm bnep binfmt_misc btusb bluetooth coretemp hid_generic kvm_intel kvm hid_appleir hid_apple joydev snd_hda_codec_realtek applesmc input_polldev nls_iso8859_1 bcm5974 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev nvidia(POF) lib80211_crypt_tkip usbhid snd_hda_intel hid snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq_midi wacom wl(POF) snd_seq_midi_event snd_rawmidi snd_seq microcode snd_seq_device snd_timer pcspkr lib80211 snd cfg80211 shpchp soundcore i2c_nforce2 apple_gmux video mac_hid apple_bl lp parport firewire_ohci firewire_core ahci crc_itu_t libahci [last unloaded: forcedeth]
Jan 11 10:40:18 abort-mbp kernel: [150604.468273] CPU: 1 PID: 406 Comm: wl_event_handle Tainted: PF       W  O 3.11.0-15-generic #23-Ubuntu
Jan 11 10:40:18 abort-mbp kernel: [150604.468275] Hardware name: Apple Inc. MacBookPro5,1/Mac-F42D86C8, BIOS    MBP51.88Z.007E.B06.1202061253 02/06/12
Jan 11 10:40:18 abort-mbp kernel: [150604.468278]  0000000000000009 ffff88022d8bbdd0 ffffffff816e7335 0000000000000000
Jan 11 10:40:18 abort-mbp kernel: [150604.468283]  ffff88022d8bbe08 ffffffff81061dcd ffff88023f78d000 ffff88022c890d80
Jan 11 10:40:18 abort-mbp kernel: [150604.468287]  0000000000000097 ffff88022c890180 ffff88023f7929f8 ffff88022d8bbe18
Jan 11 10:40:18 abort-mbp kernel: [150604.468292] Call Trace:
Jan 11 10:40:18 abort-mbp kernel: [150604.468301]  [<ffffffff816e7335>] dump_stack+0x45/0x56
Jan 11 10:40:18 abort-mbp kernel: [150604.468308]  [<ffffffff81061dcd>] warn_slowpath_common+0x7d/0xa0
Jan 11 10:40:18 abort-mbp kernel: [150604.468312]  [<ffffffff81061eaa>] warn_slowpath_null+0x1a/0x20
Jan 11 10:40:18 abort-mbp kernel: [150604.468333]  [<ffffffffa00b5409>] cfg80211_roamed+0x89/0x90 [cfg80211]
Jan 11 10:40:18 abort-mbp kernel: [150604.468379]  [<ffffffffa02edd1c>] wl_notify_roaming_status+0xac/0x130 [wl]
Jan 11 10:40:18 abort-mbp kernel: [150604.468420]  [<ffffffffa02ed445>] wl_event_handler+0x55/0x1f0 [wl]
Jan 11 10:40:18 abort-mbp kernel: [150604.468460]  [<ffffffffa02ed3f0>] ? wl_cfg80211_scan+0x350/0x350 [wl]
Jan 11 10:40:18 abort-mbp kernel: [150604.468466]  [<ffffffff81084740>] kthread+0xc0/0xd0
Jan 11 10:40:18 abort-mbp kernel: [150604.468470]  [<ffffffff81084680>] ? kthread_create_on_node+0x120/0x120
Jan 11 10:40:18 abort-mbp kernel: [150604.468476]  [<ffffffff816f716c>] ret_from_fork+0x7c/0xb0
Jan 11 10:40:18 abort-mbp kernel: [150604.468480]  [<ffffffff81084680>] ? kthread_create_on_node+0x120/0x120
Jan 11 10:40:18 abort-mbp kernel: [150604.468483] ---[ end trace 8b617a2f4b12a4a2 ]---
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <warn> (eth0): DHCPv4 request timed out.
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <info> (eth0): canceled DHCP transaction, DHCP client pid 25235
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <warn> Activation (eth0) failed for connection 'duhs'
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 11 10:40:19 abort-mbp NetworkManager[862]: <info> (eth0): deactivating device (reason 'none') [0]
Jan 11 10:40:19 abort-mbp avahi-daemon[902]: Withdrawing address record for fe80::223:32ff:fecb:a92a on eth0.
Jan 11 10:40:19 abort-mbp avahi-daemon[902]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::223:32ff:fecb:a92a.
Jan 11 10:40:19 abort-mbp avahi-daemon[902]: Interface eth0.IPv6 no longer relevant for mDNS.
Jan 11 10:40:19 abort-mbp whoopsie[1138]: offline

```

---

### Post by varunendra on 2014-01-13
Can you try a lower speed and see if it can let you connect?

If you wish to try, please install 'ethtool' (while being connected via wifi) -
```
sudo apt-get install ethtool
```

Then run the following -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
Any improvement? If not, please post back the full output of -
```
sudo ethtool eth0
```

**PS:**
You may try only one of the parameters at a time. That is, either "msi=0" or "msix=0" with the modprobe commands. It is supposed to disable interrupts handling by the card, so kernel panic may occur. If it does, simply reboot and it should be fine on next boot (since the change was temporary).

---

### Post by skipx on 2014-01-14
Thanks. I tried but no luck..

```

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:23:32:cb:a9:2a  
          inet6 addr: fe80::223:32ff:fecb:a92a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14483 (14.4 KB)  TX bytes:37848 (37.8 KB)

```
```

$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: off
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes

```

---

### Post by varunendra on 2014-01-15
Have you tried manually assigning a valid IP yet? To do that permanently, choose "Manual" method in the Network Manager settings for your connection, and save relevant settings manually (IP, Gateway, DNS) there.

To try just connectivity with a valid IP temporarily -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.200
```
..where the address "192.168.1.200" is just an example. Change it to a valid and available (that is, not in router's DHCP pool, not already assigned to another device on the network) IP address on your local network.

---

