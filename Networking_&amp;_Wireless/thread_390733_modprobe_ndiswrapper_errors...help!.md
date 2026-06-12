---
title: "modprobe ndiswrapper errors...help!"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by lwpack on 2007-03-22
Greetings and good day. I'm running Ubuntu 6.10 and trying to get my Netgear WG111v2 USB adapter to work (which is supposed to be plug and play with the native driver, but it isn't.) The problem comes when I type modprobe ndiswrapper. The system log says, "couldn't load driver net111v2" and also gives me a whole bunch of other errors. Below I posted the result of some commands that might help as well as posting the relevant portion of the system log. Any ideas? 

One last thing, even though it says the driver r8187 is present, it has been blacklisted. 

Thanks! 


root@lwpack-pc:~# ndiswrapper -v 
utils version: 1.9 
driver version: 1.38 
vermagic: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1 
root@lwpack-pc:/Downloads/Netgear# ndiswrapper -l 
net111v2 : driver installed 
device (0846:6A00) present (alternate driver: r8187) 
root@lwpack-pc:/Downloads/Netgear# lsusb 
Bus 002 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2) 
Bus 002 Device 004: ID 413c:5116 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 002: ID 413c:2005 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000 
root@lwpack-pc:~# modprobe ndiswrapper 
root@lwpack-pc:~# less /var/log/syslog 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.144000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes) 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.292000] usb 2-8: reset high speed USB device using ehci_hcd and address 6 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer 
AndNetBufferList' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveN 
etBufferLists' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisGetVersion' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniport 
Driver' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMinipo 
rtDriver' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList 
Pool' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer 
ListPool' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferLis 
tsComplete' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttri 
butes' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer 
AndNetBufferList' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveN 
etBufferLists' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisGetVersion' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniport 
Driver' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMinipo 
rtDriver' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList 
Pool' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer 
ListPool' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferLis 
tsComplete' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttri 
butes' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList 
' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComple 
te' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfiguration 
Ex' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx 
' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWit 
hTagPriority' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkIte 
m' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: WDFLDR.SYS:'WdfVersionBind' 
Mar 22 07:21:04 lwpack-pc loadndisdriver: loadndisdriver: load_driver(359): couldn't load driver net111v2 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (import:245): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.428000] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net111v2' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.440000] ndiswrapper (load_wrap_driver:118): couldn't load driver net111v2; check 
system log for messages from 'loadndisdriver' 
Mar 22 07:21:04 lwpack-pc kernel: [17220253.440000] usbcore: registered new driver ndiswrapper

---

### Post by tgalati4 on 2007-03-22
Try booting with a Dapper 6.06.1 Live CD and see if the hardware is detected and works out of the box.  This may give you a clue as to what went wrong.

Post the output of:

lspci

---

### Post by lwpack on 2007-03-22
Post the output of lspci in edgy or dapper?  My USB adapter is supposed to work out of box in edgy but not in dapper.  I'll give it a go with dapper anyways.

---

### Post by tgalati4 on 2007-03-26
Boot your machine with a Live Dapper 6.06.1 disk.  Keep the USB adapter unplugged.
Open a terminal shell.  Run dmesg and note the last few lines.  Probably bluetooth stuff like:

[17179665.328000] NET: Registered protocol family 31
[17179665.328000] Bluetooth: HCI device and connection manager initialized
[17179665.328000] Bluetooth: HCI socket layer initialized
[17179665.500000] Bluetooth: L2CAP ver 2.8
[17179665.500000] Bluetooth: L2CAP socket layer initialized
[17179665.720000] Bluetooth: RFCOMM socket layer initialized
[17179665.720000] Bluetooth: RFCOMM TTY layer initialized
[17179665.720000] Bluetooth: RFCOMM ver 1.7

Then plug your USB adapter in and run dmesg again.  Post the output beyond what you saw originally.  This will give us a clue as to how the Hardware Abstraction Layer (HAL) detects your adapter.

Edgy and Feisty have some network architecture changes that are supposed to be improvements in how network hardware interacts with the kernel.  Dapper has a legacy network architecture.  It's helpful to the community to see the difference between the two--with different types of hardware.

Also, since you said you blacklisted the r8187 driver, was it done correctly?  Perhaps a typo in the driver name?

I get the following: (under Dapper)

rjgalati@jarhead1:~$ locate r8187
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/rtl8187/r8187.ko
/lib/modules/2.6.15-28-386/kernel/drivers/net/wireless/rtl8187/r8187.ko
/usr/src/linux-source-2.6.15/drivers/net/wireless/rtl8187/r8187.h
/usr/src/linux-source-2.6.15/drivers/net/wireless/rtl8187/r8187_core.c

Perhaps blacklist rtl8187?  This assumes that your USB dongle has a Realtek 8187 chip.  Have you researched it?

I'm curious as to the output of ndiswrapper -l.  Under Dapper, I get:

rjgalati@jarhead1:~$ ndiswrapper -l
Installed ndis drivers:
mrv8000c                driver present, hardware present

I am using an Airlink 101, pcmcia wireless card with a windows driver, blacklisting the mrv8k driver (that is supposed to work, but doesn't).

Based your your ndis errors, I would say that the ndiswrapper took a dump.

What Windows version of the drivers did you use?  Sometimes using a Windows 98SE or Win2000 driver will work better than a WinXP driver.

Good luck.

---

### Post by j0sh0 on 2007-03-27
try disabling the alternate driver (r8187) - this might be overriding the ndiswrapper driver. edit the /etc/modprobe.d/blacklist file and append it to the end of the list. reboot and hopefully it will work.

---

