---
title: "WiFi doesn't work on a new install"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by rvickers on 2006-11-09
I just installed Ubuntu this afternoon and I can get the wired lan to work but not the wireless. WiFi radar sees the Linksys router and there's no wep key to worry about. Can someone plz help?
Thanks

---

### Post by FrodoB on 2006-11-09
Publish all of you details.  Wireless device model and version, and FCC ID.

Outputs from dmesg, iwconfig, ifconfig, lsusb, lspci, and so on.

---

### Post by sfcwoods on 2006-11-09
I am having similar problems. I can connect with the wired lan, but not with my wireless. I have security enabled on the wireless net and I thought I configured all of that correctly, soooo here are my outputs.  This is on  Dell Inspiron 6000 with built in wireless adapter.  The adapter works fine in Windows.

dmesg:
[17179653.616000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179653.616000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179653.616000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179653.616000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179653.616000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179653.664000] input: PS/2 Mouse as /class/input/input1
[17179653.684000] input: PC Speaker as /class/input/input2
[17179653.684000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179653.916000] ts: Compaq touchscreen protocol output
[17179653.988000] pccard: PCMCIA card inserted into slot 0
[17179654.268000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179654.268000] sdhci: Copyright(c) Pierre Ossman
[17179654.976000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179654.976000] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
[17179654.976000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 177
[17179654.976000] mmc0: SDHCI at 0xdfdfc700 irq 177 DMA
[17179654.984000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 193
[17179654.984000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179655.316000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x377
[17179655.316000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7
[17179655.320000] cs: IO port probe 0x820-0x8ff: clean.
[17179655.320000] cs: IO port probe 0xc00-0xcf7: clean.
[17179655.320000] cs: IO port probe 0xa00-0xaff: clean.
[17179655.320000] cs: memory probe 0xdfd00000-0xdfdfffff: excluding 0xdfd00000-0xdfd0ffff 0xdfdf0000-0xdfdfffff
[17179655.324000] pcmcia: registering new device pcmcia0.0
[17179655.804000] intel8x0_measure_ac97_clock: measured 55482 usecs
[17179655.804000] intel8x0: clocking to 48000
[17179655.816000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179655.816000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179657.140000] NET: Registered protocol family 17
[17179659.068000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179659.068000] b44: eth0: Flow control is off for TX and off for RX.
[17179663.812000] NET: Registered protocol family 10
[17179663.812000] lo: Disabled Privacy Extensions
[17179663.812000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179663.812000] IPv6 over IPv4 tunneling driver
[17179663.956000] ACPI: AC Adapter [AC] (on-line)
[17179664.260000] ACPI: Battery Slot [BAT0] (battery present)
[17179664.308000] ACPI: Lid Switch [LID]
[17179664.308000] ACPI: Power Button (CM) [PBTN]
[17179664.308000] ACPI: Sleep Button (CM) [SBTN]
[17179664.492000] ibm_acpi: ec object not found
[17179664.556000] pcc_acpi: loading...
[17179664.704000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179664.704000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179664.704000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179669.216000] [drm] Initialized drm 1.0.1 20051102
[17179669.244000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179669.244000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179669.700000] lp: driver loaded but no devices found
[17179670.608000] ppdev: user-space parallel port driver
[17179674.516000] eth0: no IPv6 routers present
[17179678.988000] apm: BIOS not found.
[17179694.728000] Bluetooth: Core ver 2.8
[17179694.728000] NET: Registered protocol family 31
[17179694.728000] Bluetooth: HCI device and connection manager initialized
[17179694.728000] Bluetooth: HCI socket layer initialized
[17179694.980000] Bluetooth: L2CAP ver 2.8
[17179694.980000] Bluetooth: L2CAP socket layer initialized
[17179695.872000] Bluetooth: RFCOMM socket layer initialized
[17179695.872000] Bluetooth: RFCOMM TTY layer initialized
[17179695.872000] Bluetooth: RFCOMM ver 1.7
[17179891.644000] ieee80211_crypt: registered algorithm 'WEP'
[17179891.844000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180979.068000] b44: eth0: Link is down.
[17181117.384000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[17181117.384000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17181117.384000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[17181898.824000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17181901.820000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17181901.820000] b44: eth0: Flow control is off for TX and off for RX.
[17181901.820000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17181912.216000] eth0: no IPv6 routers present
ubuntu@ubuntu:~$ 

iwconfig:
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"HomeSecNet"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ifconfig:
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D0:18:47  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fed0:1847/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1900803 (1.8 MiB)  TX bytes:353926 (345.6 KiB)
          Interrupt:201 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:74:A1:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xa000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11960 (11.6 KiB)  TX bytes:11960 (11.6 KiB)

lsusb:
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

lspci:
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

lshw -C network:
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:d0:18:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 ip=192.168.1.103 multicast=yes
       resources: iomemory:dfdfe000-dfdfffff irq:201
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:74:a1:21
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 multicast=yes wireless=unassociated
       resources: iomemory:dfdfd000-dfdfdfff irq:177

---

### Post by FrodoB on 2006-11-09
sfcwoods;

Have you looked at:

[http://www.ubuntuforums.org/showthread.php?t=294431&highlight=2200BG](http://www.ubuntuforums.org/showthread.php?t=294431&highlight=2200BG)

[http://www.ubuntuforums.org/showthread.php?t=265237&highlight=2200BG](http://www.ubuntuforums.org/showthread.php?t=265237&highlight=2200BG)

There seem to be a lot of folks solving issues with your device.

---

### Post by dnljgrg on 2006-11-09
sfcwoods...i had a similiar issue last week, i had my key index set to 4 using wep and once i changed it to key index 1, that solved my issue.  just a suggestion.

---

### Post by sfcwoods on 2006-11-09
okay, my network manager gui doesn't give me any options.  This is, I must let you know, my first attempt at using this OS so I don't know how to edit files and make changes.. :-)
any help would be much appreciated.

---

### Post by featherking on 2006-11-10
when using network manager you first have to go to System > admin > networking and hit properties for all your adapters listed there and then clear the "enable this connection" checkbox. Network Manager takes control of the configuration of your network adapters, so you cant configure them here anymore (which means you also cant use static addressing). Once you have disabled the devices there, close network manager and restart it by running nm-applet from the run command (alt-F2).

With the adapters disabled you should now see a few wireless networks when you click on the Network Manager icon

---

### Post by rvickers on 2006-11-10
I lost all my networks so I cleaned my disks and reinstalled. I'm reluctant to reload Network Manager since my wired now works. At work, I use static IP and wired. At home, I use wireless dhcp. Is it possible to use Network Manager for my wireless at home and then use system->networking for work?
Is there much risk in trying? I really hosed my laptop up yesterday monkeying with Network Manager, Wifi Radar and system->networking. :rolleyes: 
Thx

---

### Post by featherking on 2006-11-13
is there much risk trying? > for me Network Manger is the best for doing wireless networks and since im rarely on a wire (unless im copying large files) and never on a static ip, its a no-brainer. Nothing is easier (IMHO) for managing your wifi networks. You just have to look at what your primary uses are. If you are at work w/ a static ip most of the time, then maybe its not the best for you. Having said that however:

Switching between (static ip/wired) and (dhcp/wireless) should work fine, when you go to work before you plug in your ethernet, quit the nm-applet up by the clock and it will ask if you want it to start again next time you start your computer, tell it you do and then when it quits go into the system>admin>networking and just enable your ethernet and set your static ip, then before you leave work just disable the adapter. It should retain all your settings it basically just comments them out. So when you get home and start your laptop nm-applet runs like normal. then when you go back to work quit nm-applet, tell it you want it to load when you restart, enable your ethernet(with settings already there this time) and you are good to go. Disable ethernet before you leave work, when you get back home start comput...

Wash, Rinse, Repeat...

---

