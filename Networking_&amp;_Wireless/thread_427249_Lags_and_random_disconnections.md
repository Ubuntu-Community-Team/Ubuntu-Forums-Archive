---
title: "Lags and random disconnections"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by darkrad on 2007-04-29
Hello,
recently i migrated my ubuntu hdd to another hdd as i explained in [http://ubuntuforums.org/showthread.php?t=376620](http://ubuntuforums.org/showthread.php?t=376620) thread.

After that moment i noticed that the wireless connection started to show lags and disconnections. I notice it since i'm connected with securecrt from my windows pc and when i type or execute commands it randomly lags and sometimes it freeze for some secs and if i keep to type it disconnects.

I'm not sure that the problem is due to the migration, since last week i upgraded to new ubuntu distro and i had to reinstall ndiswrapper and wifi drivers and the problem is still there (i followed [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29) guide to install drivers, even the first time, when i had no lag problems).

I don't know what logs should i show you that can be of any help...
```
dmesg
```
gives:
```
.......
[17179597.028000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179597.028000] PCI: setting IRQ 11 as level-triggered
[17179597.028000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179597.292000] nvidia: module license 'NVIDIA' taints kernel.
[17179597.560000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179597.560000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179597.560000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[17179598.152000] Intel ISA PCIC probe: not found.
[17179598.352000] lp0: using parport0 (interrupt-driven).
[17179598.504000] ndiswrapper version 1.28 loaded (preempt=no,smp=yes)
[17179598.584000] ndiswrapper: driver bcmwl5 (Broadcom,02/10/2005, 3.100.35.1) loaded
[17179598.584000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179598.592000] ndiswrapper: using IRQ 11
[17179599.304000] wlan0: vendor: ''
[17179599.304000] wlan0: ethernet device 00:11:50:3d:23:16 using NDIS driver bcmwl5, 14E4:4320.5.conf
[17179599.304000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179599.308000] usbcore: registered new driver ndiswrapper
[17179599.436000] Adding 369452k swap on /dev/disk/by-uuid/4bb40acb-bcb1-4b3f-b8fe-1bbb996d93c2.  Priority:-1 extents:1 across:369452k
[17179599.932000] EXT3 FS on hda1, internal journal
[17179600.152000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179600.360000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179600.360000] md: bitmap version 4.39
[17179604.820000] ACPI: Power Button (FF) [PWRF]
[17179604.820000] ACPI: Power Button (CM) [PWRB]
[17179604.820000] ACPI: Sleep Button (CM) [SLPB]
[17179605.080000] ibm_acpi: ec object not found
[17179605.140000] pcc_acpi: loading...
[17179615.180000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179615.180000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179615.180000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179616.792000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179616.792000] apm: overridden by ACPI.
[17179639.428000] Bluetooth: Core ver 2.8
[17179639.428000] NET: Registered protocol family 31
[17179639.428000] Bluetooth: HCI device and connection manager initialized
[17179639.428000] Bluetooth: HCI socket layer initialized
[17179639.628000] Bluetooth: L2CAP ver 2.8
[17179639.628000] Bluetooth: L2CAP socket layer initialized
[17179639.896000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179640.272000] Bluetooth: RFCOMM socket layer initialized
[17179640.272000] Bluetooth: RFCOMM TTY layer initialized
[17179640.272000] Bluetooth: RFCOMM ver 1.7
[17246878.428000] SMB connection re-established (-5)
[17246878.664000] SMB connection re-established (-5)
[17246878.956000] SMB connection re-established (-5)
[17333171.292000] SMB connection re-established (-5)
[17333171.328000] SMB connection re-established (-5)
[17333171.348000] SMB connection re-established (-5)
[17419597.424000] smb_add_request: request [c59beea0, mid=2] timed out!
[17419627.424000] smb_add_request: request [c59beea0, mid=2] timed out!
[17419657.424000] smb_add_request: request [c59beea0, mid=2] timed out!
[17437836.384000] SMB connection re-established (-5)
[17481650.832000] smb_add_request: request [c3837e60, mid=141] timed out!
[17481656.000000] SMB connection re-established (-5)
[17505970.892000] SMB connection re-established (-5)
[17506000.932000] smb_add_request: request [c7266ea0, mid=153] timed out!
[17506001.312000] SMB connection re-established (-5)
[17592353.524000] SMB connection re-established (-5)
[17592353.572000] SMB connection re-established (-5)
[17592353.596000] SMB connection re-established (-5)
[17679064.916000] SMB connection re-established (-5)
[17679064.956000] SMB connection re-established (-5)
[17679064.980000] SMB connection re-established (-5)
[17765140.388000] smb_add_request: request [c30a0e60, mid=6] timed out!
[17765170.388000] smb_add_request: request [c30a0e60, mid=156] timed out!
[17765200.388000] smb_add_request: request [c30a0e60, mid=6] timed out!
[17851620.884000] SMB connection re-established (-5)
[17851625.648000] SMB connection re-established (-5)
[17851625.912000] SMB connection re-established (-5)
[17900970.988000] SMB connection re-established (-5)
[17900971.072000] SMB connection re-established (-5)
[17900974.412000] SMB connection re-established (-5)
[17902601.236000] SMB connection re-established (-5)
[17902601.492000] SMB connection re-established (-5)
[17902601.636000] SMB connection re-established (-5)
[17937998.004000] smb_add_request: request [c6a99ee0, mid=10] timed out!
[17938028.080000] smb_add_request: request [c6a99ee0, mid=160] timed out!
[17938058.136000] smb_add_request: request [c6a99ee0, mid=10] timed out!
[18024371.508000] SMB connection re-established (-5)
[18024371.740000] SMB connection re-established (-5)
[18024371.984000] SMB connection re-established (-5)
[18110733.444000] SMB connection re-established (-5)
[18110733.924000] SMB connection re-established (-5)
[18110734.040000] SMB connection re-established (-5)
[18197108.688000] SMB connection re-established (-5)
[18197108.712000] SMB connection re-established (-5)
[18197108.732000] SMB connection re-established (-5)
[18283588.284000] SMB connection re-established (-5)
[18283588.680000] SMB connection re-established (-5)
[18283594.980000] SMB connection re-established (-5)
[18369869.692000] SMB connection re-established (-5)
[18369869.732000] SMB connection re-established (-5)
[18369869.752000] SMB connection re-established (-5)
[18382187.700000] SMB connection re-established (-5)
[18385797.452000] SMB connection re-established (-5)
[18456309.416000] smb_add_request: request [c2589e60, mid=3540] timed out!
[18456309.752000] SMB connection re-established (-5)
[18456309.856000] SMB connection re-established (-5)
```
the fstab has those SMB mounts:
```
//192.168.0.2/dir1      /home/xx/Desktop/Shared/dir1 smbfs   username=xx,password=xxx 0       0
//192.168.0.2/dir2 /home/xx/Desktop/Shared/dir2 smbfs   username=xx,password=xxx 0       0
//192.168.0.2/dir3       /home/xx/Desktop/Shared/dir3      smbfs   username=xx,password=xxx 0       0
```
iwconfig gives:
```
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Let me know if i should show more logs to find the problem please.
Thanks in advance

---

### Post by darkrad on 2007-04-30
any clue?

---

### Post by darkrad on 2007-04-30
give me a random reply at least, there must be something i should try before give up..

---

### Post by darkrad on 2007-05-01
last up, then i give up.

---

