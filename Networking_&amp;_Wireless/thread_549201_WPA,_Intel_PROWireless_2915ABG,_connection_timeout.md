---
title: "WPA, Intel PRO/Wireless 2915ABG, connection timeout"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by kaktuskatta on 2007-09-12
Hi! As you can see from the title my problem is related to connectionproblems. I am unable to connect to my wireless router that has WPA enabled. I manage to find and enter the WPA-key to the network, but the two "dots" in the upper right corner of the screen that indicates connectionprogress stays gray, and I never connect! The wireless card used to work on another network that had WPA, the only difference is that the keyring-manager isn't popping up anymore. I logged in to the keyring manager and deleted all keys inside, but it didn't help. I found out that the config file under /etc/network/interfaces was unchanged from the old network, so I followed this guide: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539). That didn't do any good, so I tried another one: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html). No solution to my problem. :confused:

Here is a piece of my dmesg:


[   23.484000] Bluetooth: Core ver 2.11
[   23.484000] NET: Registered protocol family 31
[   23.484000] Bluetooth: HCI device and connection manager initialized
[   23.484000] Bluetooth: HCI socket layer initialized
[   23.488000] Bluetooth: L2CAP ver 2.8
[   23.488000] Bluetooth: L2CAP socket layer initialized
[   23.500000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   23.548000] Adding 2377612k swap on /dev/disk/by-uuid/69e3b729-ba40-4800-b5ff-5696cbb30460.  Priority:-1 extents:1 across:2377612k
[   23.600000] EXT3 FS on sda2, internal journal
[   25.248000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   25.312000] NTFS volume version 3.1.
[   25.324000] Adding 2377612k swap on /dev/disk/by-uuid/69e3b729-ba40-4800-b5ff-5696cbb30460.  Priority:-2 extents:1 across:2377612k
[   26.248000] ACPI: AC Adapter [ACAD] (off-line)
[   26.408000] ACPI: Battery Slot [BAT1] (battery present)
[   26.456000] input: Power Button (FF) as /class/input/input6
[   26.456000] ACPI: Power Button (FF) [PWRF]
[   26.492000] input: Lid Switch as /class/input/input7
[   26.496000] ACPI: Lid Switch [LID0]
[   26.528000] input: Power Button (CM) as /class/input/input8
[   26.532000] ACPI: Power Button (CM) [PWRB]
[   26.564000] input: Sleep Button (CM) as /class/input/input9
[   26.568000] ACPI: Sleep Button (CM) [SLPB]
[   26.584000] Using specific hotkey driver
[   26.608000] No dock devices found.
[   26.640000] ibm_acpi: ec object not found
[   26.708000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   26.744000] pcc_acpi: loading...
[   28.748000] r8169: eth0: link down
[   30.640000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   30.644000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   30.644000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   30.712000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.072000] ppdev: user-space parallel port driver
[   34.224000] [fglrx] total      GART = 130023424
[   34.224000] [fglrx] free       GART = 114032640
[   34.224000] [fglrx] max single GART = 114032640
[   34.224000] [fglrx] total      LFB  = 134086656
[   34.224000] [fglrx] free       LFB  = 74395648
[   34.224000] [fglrx] max single LFB  = 74395648
[   34.224000] [fglrx] total      Inv  = 0
[   34.224000] [fglrx] free       Inv  = 0
[   34.224000] [fglrx] max single Inv  = 0
[   34.224000] [fglrx] total      TIM  = 0
[   34.780000] apm: BIOS not found.
[   35.912000] /dev/vmmon[5067]: Module vmmon: registered with major=10 minor=165
[   35.912000] /dev/vmmon[5067]: Module vmmon: initialized
[   36.544000] Bluetooth: RFCOMM socket layer initialized
[   36.544000] Bluetooth: RFCOMM TTY layer initialized
[   36.544000] Bluetooth: RFCOMM ver 1.8
[   50.252000] NET: Registered protocol family 10
[   50.252000] lo: Disabled Privacy Extensions
[   50.252000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.896000] eth1: no IPv6 routers present
[   86.340000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   86.388000] NET: Registered protocol family 17
[   87.040000] ieee80211_crypt: registered algorithm 'TKIP'
[   97.240000] eth1: no IPv6 routers present
[   99.468000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  111.976000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  124.524000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  137.036000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  149.548000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  162.064000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  174.580000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  187.088000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  199.604000] TKIP: replay detected: STA=00:19:5b:01:a8:a3 previous TSC 000000000000 received TSC 000000000000
[  209.476000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  476.468000] r8169: eth0: link up
[  476.468000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  494.240000] eth0: no IPv6 routers present

So, as you can see, I feel like I've tried everything. The card is able to connect just like that when the encryption is disabled, and I'm able to connect to the network with WPA through windows...

Help me please

---

### Post by kaktuskatta on 2007-09-27
Hello again all! I've finally managed to solve this problem, all on my own :) It turned out to be something stupid that I could've checked a long time ago, but for some reason this idea never occured to me until now. It turned out to be lack of support for WPA2 in linux, which ended in a timeout each time I tried to connect. It's fully possible that this is mentioned somewhere out there, but it never passed my eyes :P Anyhow....I solved the problem by logging in to the router and change the encryption type to WPA-PSK, and BANG, I'm logged in. The best part is that I don't have to enter any key on the keyring on each logon to  the net, this goes automaticly :D I have a D-link DI-524 router. Hope this is useful for others than me aswell ....

---

