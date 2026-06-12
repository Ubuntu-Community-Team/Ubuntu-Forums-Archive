---
title: "Dynex Wireless Enhanced G DX-EBUSB dongle"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by thunderdan on 2008-09-09
I am trying to get this wireless dongle to work on my friend's laptop. It's the Dynex Wireless Enhanced G DX-EBUSB dongle. I know I need to get a driver set up for it, but I'm having trouble doing that. I'm not quite sure how to use ndiswrapper. I've tried following some howtos, but everything I have found doesn't seem to fit my situation.

Here is the output of lsusb -v:

```
Bus 005 Device 004: ID 4317:0721  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x4317 
  idProduct          0x0721 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
zardoz@zardoz-laptop:~$ 
```

We have the windows drivers on a CD that came with the dongle. If I could get a little guidance as to what I'm supposed to do next, I'd really appreciate it.

Thanks,
Thunder Dan

---

### Post by thunderdan on 2008-09-10
I'm still trying to get this to work. One thing I've noticed is that when I have the dongle plugged in on startup, the Ubuntu splash screen shows up, then it goes to a screen with lots of text on it, most of which says "* Starting such-and-such [ OK ]"

So it does several of those, then it gets to "* Starting bluetooth" and then it does nothing. I guess maybe it thinks the dongle is a bluetooth device? The computer starts up normally when the dongle is not plugged in.

Thank you for taking time to read this. Any ideas would be greatly appreciated.

Thanks,
Thunder Dan

---

### Post by thunderdan on 2008-09-10
I think maybe I'm supposed to "blacklist" something? I guess I need to figure out what that means before I continue.

Any ideas, or an explanation of what it means/how to blacklist something would be greatly appreciated.

Thanks,
Thunder Dan

Also, here is the output from dmesg that I think is related to the dongle:

```
[   72.059260] usb 5-3: new high speed USB device using ehci_hcd and address 2
[   72.098007] usb 5-3: configuration #1 chosen from 1 choice
[   72.180105] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   72.197993] usb 5-3: reset high speed USB device using ehci_hcd and address 2
[   72.244314] ndiswrapper: driver ndiswdm (Dynex,08/27/2007,4.118.3.0) loaded
[   72.528468] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000010
[   72.528477] printing eip: e05e9e2c *pde = 00000000 
[   72.528482] Oops: 0000 [#1] SMP 
[   72.528486] Modules linked in: ndiswrapper ipv6 i915 drm rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_conservative cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table container dock sbs sbshc iptable_filter ip_tables x_tables parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep video output snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event serio_raw snd_seq button battery snd_timer snd_seq_device ac snd soundcore intel_agp dcdbas shpchp pci_hotplug agpgart iTCO_wdt iTCO_vendor_support evdev psmouse pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi ata_piix b44 ata_generic ssb mii libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   72.528544] 
[   72.528547] Pid: 6067, comm: modprobe Tainted: P        (2.6.24-19-generic #1)
[   72.528551] EIP: 0060:[<e05e9e2c>] EFLAGS: 00010286 CPU: 0
[   72.528579] EIP is at NdisMQueryAdapterResources+0x2c/0xd0 [ndiswrapper]
[   72.528582] EAX: ca663180 EBX: c6b1ba50 ECX: c6b1ba58 EDX: ca734800
[   72.528585] ESI: 00000000 EDI: 000000b8 EBP: c6b1ba54 ESP: c6b1ba28
[   72.528588]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   72.528592] Process modprobe (pid: 6067, ti=c6b1a000 task=ca518b80 task.ti=c6b1a000)
[   72.528594] Stack: ca669000 ca734800 ca669000 c6b1bb14 e06a086d c6b1ba54 ca669000 c6b1ba58 
[   72.528602]        c6b1ba50 00000000 000000b8 00000000 c6b1ba9c ca669000 c6b1ba9c ca54e480 
[   72.528608]        e05ed026 e05ed057 dd4f5aa8 00000000 e05e63bb dd4f5aa8 c6b1baa4 e05e9dd9 
[   72.528615] Call Trace:
[   72.528645]  [<e05ed026>] ExFreePoolWithTag+0x36/0x50 [ndiswrapper]
[   72.528668]  [<e05ed057>] ExFreePool+0x17/0x20 [ndiswrapper]
[   72.528700]  [<e05e63bb>] RtlFreeAnsiString+0x1b/0x40 [ndiswrapper]
[   72.528730]  [<e05e9dd9>] NdisReadNetworkAddress+0x189/0x1b0 [ndiswrapper]
[   72.528770]  [<e05e9889>] NdisReadConfiguration+0x79/0xf0 [ndiswrapper]
[   72.528806]  [<e05e9810>] NdisReadConfiguration+0x0/0xf0 [ndiswrapper]
[   72.528862]  [<e05f6fe4>] mp_init+0xa4/0x1f0 [ndiswrapper]
[   72.528902]  [<e05f7209>] NdisDispatchPnp+0xd9/0xfc0 [ndiswrapper]
[   72.528938]  [<c0121f8f>] update_curr+0x9f/0x150
[   72.528964]  [<c018d89d>] __slab_alloc+0x2ed/0x4a0
[   72.528981]  [<e05f050b>] IoAllocateIrp+0x4b/0x80 [ndiswrapper]
[   72.529018]  [<e05f0521>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
[   72.529054]  [<c031c4b8>] _spin_lock_bh+0x8/0x20
[   72.529061]  [<e05ec604>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
[   72.529097]  [<e05f0815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[   72.529135]  [<e05f585b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[   72.529179]  [<e05f5bb0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
[   72.529225]  [<e05f5e4f>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
[   72.529270]  [<e05f6126>] wrap_pnp_start_usb_device+0xa6/0xd0 [ndiswrapper]
[   72.529291]  [<c01a5251>] find_inode+0x31/0x60
[   72.529296]  [<c01d70e0>] sysfs_ilookup_test+0x0/0x10
[   72.529322]  [<c01d779b>] sysfs_addrm_finish+0x4b/0x1c0
[   72.529329]  [<c01d7484>] sysfs_add_one+0x44/0xe0
[   72.529337]  [<c01d758d>] sysfs_addrm_start+0x6d/0xb0
[   72.529343]  [<c031b438>] mutex_lock+0x8/0x20
[   72.529350]  [<e00a882b>] usb_autopm_do_device+0x7b/0x100 [usbcore]
[   72.529383]  [<e00a8397>] usb_match_one_id+0x27/0xb0 [usbcore]
[   72.529415]  [<e00a95d9>] usb_probe_interface+0xb9/0x140 [usbcore]
[   72.529448]  [<c02828a8>] driver_probe_device+0x88/0x190
[   72.529455]  [<c0215f30>] kobject_uevent_env+0xf0/0x3d0
[   72.529470]  [<c0282b1e>] __driver_attach+0x9e/0xa0
[   72.529478]  [<c0281cdb>] bus_for_each_dev+0x3b/0x60
[   72.529491]  [<c0282726>] driver_attach+0x16/0x20
[   72.529495]  [<c0282a80>] __driver_attach+0x0/0xa0
[   72.529500]  [<c028205a>] bus_add_driver+0x8a/0x1e0
[   72.529514]  [<e00a911e>] usb_register_driver+0x8e/0x110 [usbcore]
[   72.529547]  [<e05e540c>] loader_init+0x9c/0x140 [ndiswrapper]
[   72.529574]  [<e05f223f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[   72.529595]  [<e05f62f5>] wrapndis_init+0x45/0x50 [ndiswrapper]
[   72.529626]  [<e03570b7>] wrapper_init+0xb7/0xc2 [ndiswrapper]
[   72.529653]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   72.529705]  [<c0168c90>] disable_irq+0x0/0x30
[   72.529726]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   72.529749]  =======================
[   72.529751] Code: ec 10 8b 44 24 18 89 1c 24 8b 5c 24 20 89 6c 24 0c 8b 6c 24 14 89 74 24 04 89 7c 24 08 8b 80 9c 01 00 00 8b 3b 8b 40 04 8b 70 68 <8b> 4e 10 89 c8 c1 e0 04 83 c0 08 83 ff 17 77 24 89 03 c7 45 00 
[   72.529782] EIP: [<e05e9e2c>] NdisMQueryAdapterResources+0x2c/0xd0 [ndiswrapper] SS:ESP 0068:c6b1ba28
[   72.529815] ---[ end trace f4ec929eda8a85dc ]---
[   92.914338] b44: eth0: Link is up at 100 Mbps, full duplex.
[   92.914345] b44: eth0: Flow control is off for TX and off for RX.
[   92.914655] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   93.115155] NET: Registered protocol family 17
[   94.024675] eth0: no IPv6 routers present
[  186.278955] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  186.278971] ata1.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 8 in
[  186.278973]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
[  186.278975]          res 50/00:01:00:08:00/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
[  186.278979] ata1.01: status: { DRDY }
[  186.279096] ata1: soft resetting link
[  186.468849] ata1.00: configured for UDMA/100
[  186.623738] ata1.01: configured for UDMA/33
[  186.623764] ata1: EH complete
[  186.629523] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[  186.666699] sd 0:0:0:0: [sda] Write Protect is off
[  186.666709] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  186.666836] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  186.666867] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[  186.666880] sd 0:0:0:0: [sda] Write Protect is off
[  186.666883] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  186.666902] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
zardoz@zardoz-laptop:~$ 
```

---

### Post by thunderdan on 2008-09-10
OK, I found this thread:

[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

So I think what I need to do is find out what driver is assigned to the wireless dongle, then make a blacklist file and add that driver to it. Then I can use ndiswrapper to put a driver in its place, thereby allowing this laptop to have a wireless connection.

Am I on the right track?

---

### Post by thunderdan on 2008-09-15
Well I'm giving up on this issue. I've tried to figure it out, but to no avail. I'll just advise my friend to buy a wireless device with Linux support.

Thanks to everyone who responded.

---

