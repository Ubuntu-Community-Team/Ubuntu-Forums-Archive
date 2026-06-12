---
title: "No network access after resuming from hibernate (DHCP fails)"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Dave.G on 2008-10-26
New install of Kubuntu 8.04.1 (fully updated) on a Dell Inspiron 5100 laptop with Broadcom integrated ethernet (detected as BCM4401 100Base-T rev 01)

I just recently switched to Kubuntu from Mandriva, and I'm quite impressed at how much works out-of-the-box in comparison. Hibernate works from the start (which is nice) but I have one rather big problem on resume: no network access. The little applet in the system tray stalls halfway through its little progress bar and can't get the IP. After a while it gives up and shows as 0.0.0.0. KInfoCenter shows the IP address for eth0 as 169.254.8.121. It should be 10.0.0.2 as assigned by the DHCP in my router.

Things I've tried after hibernating:
unplugging the cable and then back again
manually configuring IP address
running dhclient (or automatically via /etc/acpu/resume.d/64-dhclient.sh)
running /etc/init.d/networking restart
adding dhcp3-server to STOP_SERVICES in /etc/default/acpi-support
adding networking to STOP_SERVICES in /etc/default/acpi-support

Only thing that works is a reboot. (ideas above were from [here]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/64988"), [here]("https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/48212"), [here]("http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/"); I don't think any were directly applicable)

Boot times are quite nice here, but I would like to be able to suspend to disk again. Without Internet access on resume it's not really usable. What needs to be reset on resume and where do I set it?

If anyone can at least point me in the right direction, it would be much appreciated.

---

### Post by cob on 2008-10-27
Dave,

Have you tried unloading and reloading the module?

```
sudo rmmod b44
modprobe b44
```

---

### Post by Dave.G on 2008-10-27
> **cob said:**
> Have you tried unloading and reloading the module?

```
sudo rmmod b44
modprobe b44
```
Just gave that a try, and no, it doesn't work. I tried unloading/reloading after hibernation and then rebooted and tried unloading before hibernation then reloading afterward. Neither fixed it.

Just in case anyone thought it might be my router's fault, it's not. I also installed Kubuntu 8.04.1 on an old desktop wired into the same router and it works perfectly after resuming from hibernation.

Any other suggestions?

---

### Post by cob on 2008-10-27
Can you post your kernel logs after hibernation?  /var/log/kern.log

---

### Post by Dave.G on 2008-10-27
/var/log/kern.log from hibernation to resume:
```
Oct 27 04:58:54 dave-laptop kernel: [  344.345042] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 27 04:58:54 dave-laptop kernel: [  344.457023] ACPI: PCI interrupt for device 0000:02:01.0 disabled
Oct 27 04:58:55 dave-laptop kernel: [  345.776834] PM: suspend-to-disk mode set to 'platform'
Oct 27 04:58:55 dave-laptop kernel: [  345.777273] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
Oct 27 04:58:55 dave-laptop kernel: [  345.777281] swsusp: Basic memory bitmaps created
Oct 27 04:59:44 dave-laptop kernel: [  345.777283] Syncing filesystems ... done.
Oct 27 04:59:45 dave-laptop kernel: [  345.780012] Freezing user space processes ... (elapsed 0.00 seconds) done.
Oct 27 04:59:45 dave-laptop kernel: [  345.781083] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Oct 27 04:59:45 dave-laptop kernel: [  345.781141] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^Hdone (55064 pages freed)
Oct 27 04:59:45 dave-laptop kernel: [  347.164341] Freed 220256 kbytes in 1.38 seconds (159.60 MB/s)
Oct 27 04:59:45 dave-laptop kernel: [  347.164344] Suspending console(s)
Oct 27 04:59:45 dave-laptop kernel: [  347.368182] sd 1:0:0:0: [sda] Synchronizing SCSI cache
Oct 27 04:59:45 dave-laptop kernel: [  347.384512] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
Oct 27 04:59:45 dave-laptop kernel: [  347.384655] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Oct 27 04:59:45 dave-laptop kernel: [  347.384754] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Oct 27 04:59:45 dave-laptop kernel: [  347.400222] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Oct 27 04:59:45 dave-laptop kernel: [  347.400253] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Oct 27 04:59:45 dave-laptop kernel: [  347.400283] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Oct 27 04:59:45 dave-laptop kernel: [  347.401980] Disabling non-boot CPUs ...
Oct 27 04:59:45 dave-laptop kernel: [  347.402153] swsusp: critical section: 
Oct 27 04:59:45 dave-laptop kernel: [  347.417532] swsusp: Need to copy 62997 pages
Oct 27 04:59:45 dave-laptop kernel: [  347.417537] swsusp: Normal pages needed: 62997 + 1024 + 14, available pages: 67920
Oct 27 04:59:45 dave-laptop kernel: [   23.383596] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 27 04:59:45 dave-laptop kernel: [   23.383604] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Oct 27 04:59:45 dave-laptop kernel: [   23.383647] usb usb1: root hub lost power or was reset
Oct 27 04:59:45 dave-laptop kernel: [   23.383664] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 27 04:59:45 dave-laptop kernel: [   23.383670] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Oct 27 04:59:45 dave-laptop kernel: [   23.383710] usb usb2: root hub lost power or was reset
Oct 27 04:59:45 dave-laptop kernel: [   23.383726] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 27 04:59:45 dave-laptop kernel: [   23.383732] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Oct 27 04:59:45 dave-laptop kernel: [   23.383772] usb usb3: root hub lost power or was reset
Oct 27 04:59:45 dave-laptop kernel: [   23.398796] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Oct 27 04:59:45 dave-laptop kernel: [   23.398803] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Oct 27 04:59:45 dave-laptop kernel: [   23.398846] usb usb4: root hub lost power or was reset
Oct 27 04:59:45 dave-laptop kernel: [   23.402725] ehci_hcd 0000:00:1d.7: debug port 1
Oct 27 04:59:45 dave-laptop kernel: [   23.402731] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Oct 27 04:59:45 dave-laptop kernel: [   23.402751] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20020200, writing 20060200)
Oct 27 04:59:45 dave-laptop kernel: [   23.402768] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 27 04:59:45 dave-laptop kernel: [   23.402832] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800003, writing 2800007)
Oct 27 04:59:45 dave-laptop kernel: [   23.402843] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 27 04:59:45 dave-laptop kernel: [   23.402849] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Oct 27 04:59:45 dave-laptop kernel: [   23.403098] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2900007, writing 2900003)
Oct 27 04:59:45 dave-laptop kernel: [   23.403112] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
Oct 27 04:59:45 dave-laptop kernel: [   23.403119] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Oct 27 04:59:45 dave-laptop kernel: [   23.583236] ata2.00: configured for UDMA/100
Oct 27 04:59:45 dave-laptop kernel: [   23.583284] sd 1:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
Oct 27 04:59:45 dave-laptop kernel: [   23.583300] sd 1:0:0:0: [sda] Write Protect is off
Oct 27 04:59:45 dave-laptop kernel: [   23.583302] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 27 04:59:45 dave-laptop kernel: [   23.583324] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 27 04:59:45 dave-laptop kernel: [   24.022953] ata1.00: configured for UDMA/33
Oct 27 04:59:45 dave-laptop kernel: [   24.416130] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 27 04:59:45 dave-laptop kernel: [   24.416175] PM: Writing back config space on device 0000:02:04.0 at offset f (was 74001ff, writing 5c001ff)
Oct 27 04:59:45 dave-laptop kernel: [   24.416193] PM: Writing back config space on device 0000:02:04.0 at offset 3 (was 822008, writing 82a820)
Oct 27 04:59:45 dave-laptop kernel: [   24.430567] PM: Writing back config space on device 0000:02:04.1 at offset f (was 4020100, writing 402010b)
Oct 27 04:59:45 dave-laptop kernel: [   24.430583] PM: Writing back config space on device 0000:02:04.1 at offset 5 (was 0, writing faff8000)
Oct 27 04:59:45 dave-laptop kernel: [   24.430588] PM: Writing back config space on device 0000:02:04.1 at offset 4 (was 0, writing faffd800)
Oct 27 04:59:45 dave-laptop kernel: [   24.430592] PM: Writing back config space on device 0000:02:04.1 at offset 3 (was 800000, writing 802008)
Oct 27 04:59:45 dave-laptop kernel: [   24.430598] PM: Writing back config space on device 0000:02:04.1 at offset 1 (was 2100000, writing 2100116)
Oct 27 04:59:45 dave-laptop kernel: [   24.480247] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Oct 27 04:59:45 dave-laptop kernel: [   25.642311] sd 1:0:0:0: [sda] Starting disk
Oct 27 04:59:45 dave-laptop kernel: [   25.668467] PM: Image restored successfully.
Oct 27 04:59:45 dave-laptop kernel: [   25.689804] Restarting tasks ... done.
Oct 27 04:59:45 dave-laptop kernel: [   25.710395] swsusp: Basic memory bitmaps freed
Oct 27 04:59:46 dave-laptop kernel: [   27.141847] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
Oct 27 04:59:46 dave-laptop kernel: [   27.161409] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
Oct 27 04:59:46 dave-laptop kernel: [   27.161419] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
Oct 27 04:59:46 dave-laptop kernel: [   27.161425] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
Oct 27 04:59:46 dave-laptop kernel: [   27.197964] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
Oct 27 04:59:46 dave-laptop kernel: [   27.197996] b44.c:v2.0
Oct 27 04:59:46 dave-laptop kernel: [   27.218605] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:32:d9:c1
Oct 27 04:59:46 dave-laptop kernel: [   27.313071] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 27 04:59:46 dave-laptop kernel: [   27.646834] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 27 04:59:49 dave-laptop kernel: [   30.723487] b44: eth0: Link is up at 100 Mbps, full duplex.
Oct 27 04:59:49 dave-laptop kernel: [   30.723493] b44: eth0: Flow control is off for TX and off for RX.
Oct 27 04:59:49 dave-laptop kernel: [   30.724725] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 27 05:00:00 dave-laptop kernel: [   41.651406] eth0: no IPv6 routers present
```

---

### Post by Dave.G on 2008-10-27
Here's what I get if I run dhclient after resuming from hibernation:
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0d:56:32:d9:c1
Sending on   LPF/eth0/00:0d:56:32:d9:c1
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.2 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
Trying recorded lease 10.0.0.2
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.

--- 10.0.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```
I think it may be that it's failing because it can't access the interface at all. (10.0.0.1 is the router)

---

### Post by cob on 2008-10-27
Maybe try:

```
sudo rmmod ssb
sudo rmmod b44
sudo insmod ssb
sudo insmod b44
```

---

### Post by Dave.G on 2008-10-27
> **cob said:**
> Maybe try:

```
sudo rmmod ssb
sudo rmmod b44
sudo insmod ssb
sudo insmod b44
```
Thanks for trying, but it doesn't work either.

Looks like you have to rmmod b44 first, otherwise you get:
"ERROR: Module ssb is in use by b44"
The insmod command also gives errors:
"insmod: can't read 'b44': No such file or directory"
"insmod: can't read 'ssb': No such file or directory"
The modprobe command seems to put things back, though it doesn't fix the problem.

---

### Post by cob on 2008-10-27
Ah, ok.  So it should have been more like:

> sudo rmmod b44
sudo rmmod ssb
sudo modprobe ssb
sudo modprobe b44

If you've already tried that and it isn't working, then I'm fresh out of ideas, sorry.

---

