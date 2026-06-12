---
title: "wireless card turns off before loading desktop"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by Tank5489 on 2008-08-25
so this winter Grub completely stopped working so i just re-installed the updated Ubuntu (8.04 Hardy Heron) everything was working until about a week ago when i was downloading some torrent's and poof, no wireless. after restarting a couple of times  i found that the wireless card LED would light up (like in normal use) but as soon as i would log in it would turn off. once the desk top loaded i was able to turn the card on using the terminal but when i went to select a network it showed none. I then Dmesg and received the message 

[   39.184674] ppdev: user-space parallel port driver 
[   39.350738] audit(1219675090.292:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5152 profile="/usr/sbin/cupsd" namespace="default" 
[   41.098981] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   41.160572] input: b43-phy0 as /devices/virtual/input/input9 
[   41.248709] Bluetooth: Core ver 2.11 
[   41.252786] NET: Registered protocol family 31 
[   41.252793] Bluetooth: HCI device and connection manager initialized 
[   41.252797] Bluetooth: HCI socket layer initialized 
[   41.331378] Bluetooth: L2CAP ver 2.9 
[   41.331384] Bluetooth: L2CAP socket layer initialized 
[   41.427631] Bluetooth: RFCOMM socket layer initialized 
[   41.427649] Bluetooth: RFCOMM TTY layer initialized 
[   41.427651] Bluetooth: RFCOMM ver 1.8 
[   41.495094] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02) 
[   42.454764] b43-phy0 debug: Chip initialized 
[   42.455246] b43-phy0 debug: 32-bit DMA initialized 
[   42.457636] Registered led device: b43-phy0:tx 
[   42.457872] Registered led device: b43-phy0:rx 
[   42.458061] Registered led device: b43-phy0:radio 
[   42.458156] b43-phy0 debug: Wireless interface started 
[   42.464837] b43-phy0: Radio hardware status changed to DISABLED 
[   42.466461] b43-phy0 debug: Adding Interface type 2 
[   42.469722] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   44.691720] [drm] Initialized drm 1.1.0 20060810 
[   44.696515] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17 
[   44.696526] PCI: Setting latency timer of device 0000:00:02.0 to 64 
[   44.696620] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[   63.200531] b43-phy0 debug: Removing Interface type 2 
[   63.264539] b43-phy0 debug: Wireless interface stopped 
[   63.264657] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64 
[   63.264704] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128 
[   63.272340] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128 
[   63.280337] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128 
[   63.288331] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128 
[   63.296307] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128 
[   63.304310] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128 
[  468.328465] input: b43-phy0 as /devices/virtual/input/input10 
[  468.479873] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02) 
[  469.723934] b43-phy0 debug: Chip initialized 
[  469.724435] b43-phy0 debug: 32-bit DMA initialized 
[  469.745693] Registered led device: b43-phy0:tx 
[  469.745967] Registered led device: b43-phy0:rx 
[  469.746129] Registered led device: b43-phy0:radio 
[  469.746223] b43-phy0 debug: Wireless interface started 
[  469.783856] b43-phy0: Radio hardware status changed to DISABLED 
[  469.788185] b43-phy0 debug: Adding Interface type 2 
[  469.791456] ADDRCONF(NETDEV_UP): wlan0: link is not ready 

so if anybody has any ideas that would be great, Thanks!

---

