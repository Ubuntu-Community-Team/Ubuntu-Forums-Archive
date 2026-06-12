---
title: "Please help with Hawking Wireless-300N USB adapter"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Domas on 2008-10-07
Hi all,

I stucked on making my wifi card work on Ubuntu and I really need help. I have Hawking Wireless-300N USB adapter, which has netr28u.inf driver. So far my card is detected and drivers seems to be installed well, but I cant get it work and I have been trying to make it work for a long time, but without luck. This is what I did so far and have no idea what else I could try:

sudo ndiswrapper -i /home/domas/Desktop/Wireless\ Tools/MANO\ Hawking\ XP\ driver/netr28u.inf 
installing netr28u ...

domas@com:~$ ndiswrapper -l

netr28u : driver installed
	device (0E66:0001) present

domas@com:~$ lsusb
Bus 005 Device 005: ID 0e66:0001 Hawking 
Bus 005 Device 004: ID 145f:0090  
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00a4 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
domas@com:~$

domas@com:~$ uname -m

i686

sudo gedit /etc/modprobe.d/blacklist

added these two lines at the end:

blacklist ath_pci
blacklist sky2

Rebooted.

root@com:~# lshw -C Network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 14
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
root@com:~#

root@com:~# sudo depmod -a
root@com:~# sudo modprobe ndiswrapper
root@com:~# lsmod | grep ndis
ndiswrapper           192920  0 
usbcore               146028  7 snd_usb_audio,snd_usb_lib,ndiswrapper,usbhid,ehci_hcd,uhci_hcd


root@com:~# dmesg | grep -e ndis -e ath0
[   39.004446] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.456450] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   39.456474] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   39.456484] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   39.456500] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   39.456510] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   39.456519] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   39.456568] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   39.456582] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   39.456592] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   39.456609] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   39.456618] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   39.456628] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   39.456638] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   39.456648] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   39.456657] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   39.456667] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   39.456686] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   39.456693] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   39.456697] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netr28u'
[   39.457197] ndiswrapper (load_wrap_driver:112): couldn't load driver netr28u; check system log for messages from 'loadndisdriver'
[   39.457230] usbcore: registered new interface driver ndiswrapper
root@com:~#

root@com:~# tail /var/log/messages
Oct  7 15:21:53 com kernel: [   49.196637] Bluetooth: RFCOMM TTY layer initialized
Oct  7 15:21:53 com kernel: [   49.196639] Bluetooth: RFCOMM ver 1.8
Oct  7 15:21:56 com kernel: [   52.638585] [drm] Initialized drm 1.1.0 20060810
Oct  7 15:21:56 com kernel: [   52.642911] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  7 15:21:56 com kernel: [   52.643004] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct  7 15:22:12 com kernel: [   68.671903] NET: Registered protocol family 10
Oct  7 15:22:12 com kernel: [   68.672337] lo: Disabled Privacy Extensions
Oct  7 15:39:56 com kernel: [ 1130.973026] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
Oct  7 15:39:56 com kernel: [ 1130.973033] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
Oct  7 15:39:56 com kernel: [ 1130.973037] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.

root@com:~# sudo tail -f /var/log/messages
Oct  7 16:21:15 com kernel: [ 1197.705564] usb 5-3.4: new high speed USB device using ehci_hcd and address 7
Oct  7 16:21:15 com kernel: [ 1197.814510] usb 5-3.4: configuration #1 chosen from 1 choice
Oct  7 16:21:15 com kernel: [ 1197.917247] usb 5-3.4: reset high speed USB device using ehci_hcd and address 7
Oct  7 16:21:15 com loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netr28u

root@com:~# iwconfig
lo        no wireless extensions.

root@com:~# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113000 (110.3 KB)  TX bytes:113000 (110.3 KB)

root@com:~#


Wireless is turned on, reinstalled ndiswrapper from source, this wifi card works perfectly on Vista and I have tried Vista's and XP drivers on Ubuntu, so far no luck. 

Using Ubuntu 8.04, Kernel 2.6.24-19-generic

I would appreciate if someone can give me some help making this card working on my Linux, card is pretty expensive, so I really want to make it work and not only on crappy Vista...

---

### Post by Domas on 2008-10-07
Anyone?

---

### Post by linux4909 on 2008-10-17
I have the Hawking Technology wireless 150n(HWDN2) and ran into the same issue on another distro. There are linux drivers for this device that are available for free. Check links below for driver and instructions for installation in Linux. 

[http://www.opendrivers.com/driver/283911/ralink-rt2870usb-rt2870webui-wireless-driver-1.3.1.0-linux-free-download.html](http://www.opendrivers.com/driver/283911/ralink-rt2870usb-rt2870webui-wireless-driver-1.3.1.0-linux-free-download.html)

instructions on installing driver
[http://www.mattpacker.com/?p=19](http://www.mattpacker.com/?p=19)

---

### Post by guitar2007 on 2009-01-05
> **linux4909 said:**
> I have the Hawking Technology wireless 150n(HWDN2) and ran into the same issue on another distro. There are linux drivers for this device that are available for free. Check links below for driver and instructions for installation in Linux. 

[http://www.opendrivers.com/driver/283911/ralink-rt2870usb-rt2870webui-wireless-driver-1.3.1.0-linux-free-download.html](http://www.opendrivers.com/driver/283911/ralink-rt2870usb-rt2870webui-wireless-driver-1.3.1.0-linux-free-download.html)

instructions on installing driver
[http://www.mattpacker.com/?p=19](http://www.mattpacker.com/?p=19)




Did this actually work for your 150-n?  Because I'm still having trouble with mine.

---

### Post by jualin on 2009-07-09
Did you get yours working?

---

