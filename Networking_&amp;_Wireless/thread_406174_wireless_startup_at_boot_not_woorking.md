---
title: "wireless startup at boot not woorking"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by bean66 on 2007-04-10
I have a wireless card installed...
After booting the device does not initialised. If I stop it and start it manually everything works fine.. 
Any ideas on how to get the device up the first time ?

Here is the dmesg output, including the ending lines where its reconfigured:

   36.710091] ath_hal: module license 'Proprietary' taints kernel.
[   36.710738] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   36.729576] wlan: 0.8.4.2 (svn r2256)
[   36.738782] ath_pci: 0.9.4.5 (svn r2256)
[   36.739293] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   36.739297] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 58
[   37.355737] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.377761] ath_rate_sample: 1.2 (svn r2256)
[   37.381042] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   37.381047] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   37.381053] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   37.381056] wifi0: mac 7.8 phy 4.5 radio 5.6
[   37.381060] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   37.381061] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   37.381063] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   37.381064] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   37.381066] wifi0: Use hw queue 8 for CAB traffic
[   37.381067] wifi0: Use hw queue 9 for beacons
[   37.444370] wifi0: Atheros 5212: mem=0xfdee0000, irq=58
[   37.450907] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   37.450911] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [AAZA] -> GSI 21 (level, low) -> IRQ 50
[   37.451049] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   38.070544] NET: Registered protocol family 17
[   38.093367] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   38.255535] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[   38.484106] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   38.484111] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 58
[   38.484119] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   38.484239] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9755  Mon Feb 26 23:16:31 PST 2007
[   38.485704] flexcop-pci: will use the HW PID filter.
[   38.485710] flexcop-pci: card revision 2
[   38.486219] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   38.486224] GSI 22 sharing vector 0x52 and IRQ 22
[   38.486230] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 82
[   38.503276] DVB: registering new adapter (FlexCop Digital TV device).
[   38.504720] b2c2-flexcop: MAC address = 00:d0:d7:30:1e:39
[   38.504896] b2c2-flexcop: i2c master_xfer failed
[   38.711118] b2c2-flexcop: i2c master_xfer failed
[   38.711515] b2c2-flexcop: i2c master_xfer failed
[   38.711518] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -121)
[   38.711520] Unknown/Unsupported NXT chip: 00 00 00 00 00
[   38.711793] b2c2-flexcop: i2c master_xfer failed
[   38.711796] lgdt330x: i2c_read_demod_bytes: addr 0x59 select 0x02 error (ret == -121)
[   38.711920] bcm3510: Revision: 0x1, Layer: 0xb.
[   38.734523] b2c2-flexcop: found the bcm3510 at i2c address: 0x0f
[   38.734526] DVB: registering frontend 0 (Broadcom BCM3510 VSB/QAM frontend)...
[   38.734557] b2c2-flexcop: initialization of 'Air2PC/AirStar 2 ATSC 1st generation' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
[   38.813441] lp0: using parport0 (interrupt-driven).
[   38.842378] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   38.842382] ieee1394: sbp2: Try serialize_io=0 for better performance
[   38.873142] Adding 8024k swap on /dev/disk/by-uuid/798d7edc-bade-404b-970a-3fe0a8a61d8d.  Priority:-1 extents:1 across:8024k
[   38.925832] EXT3 FS on sda1, internal journal
[   39.096336] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   39.096531] SGI XFS Quota Management subsystem
[   39.141988] XFS mounting filesystem sda3
[   39.241209] Ending clean XFS mount for filesystem: sda3
[   41.624770] ACPI: Power Button (FF) [PWRF]
[   41.624778] ACPI: Power Button (CM) [PWRB]
[   41.704953] ibm_acpi: ec object not found
[   41.740668] pcc_acpi: loading...
[   41.962601] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   41.962628] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0xc (1250 mV)
[   41.962632] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xe (1200 mV)
[   41.962634] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x10 (1150 mV)
[   41.962637] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0x10 (1150 mV)
[   41.962639] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[   41.962642] cpu_init done, current fid 0x10, vid 0xc
[   43.927935] NET: Registered protocol family 10
[   43.928016] lo: Disabled Privacy Extensions
**[   43.928060] ADDRCONF(NETDEV_UP): ath0: link is not ready**
[   43.928081] IPv6 over IPv4 tunneling driver
[  549.883849] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[  549.899585] ts: Compaq touchscreen protocol output
[COLOR="Magenta"][  839.228736] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  840.145233] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  844.591221] ath0: no IPv6 routers present[/COLOR]

---

### Post by Alibloke on 2007-04-10
I have the exact same problem on both my ipw3945 card in my vaio and my 2200 in my HP - after some searching it seems to be a little more widespread....however no solutions yet:

[http://ubuntuforums.org/showthread.php?t=237420&highlight=link+is+not+ready](http://ubuntuforums.org/showthread.php?t=237420&highlight=link+is+not+ready)

Ali.

---

### Post by bean66 on 2007-04-10
Any others?

Any help appreciated....

Ken

---

### Post by bean66 on 2007-04-11
Resolved:

Modified the file /etc/rc.local adding the following:

/etc/init.d/networking restart 

What a hack!

---

### Post by Alibloke on 2007-04-12
Hmm, I have already added it to my rc.local  - I'd really rather not though (what a hack indeed).

Ali.

---

### Post by Alibloke on 2007-04-15
Everything seems to work as it should now after the latest update today - both the 2200 and the 3945.  Well done ubuntu developers again!

Ali.

---

