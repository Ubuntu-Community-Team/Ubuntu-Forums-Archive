---
title: "Unable to get realtek 8211 wifi USB dongle to work on Ununtu, works in Raspbian"
date: 2023-05-04
forum: Networking &amp; Wireless
---

### Post by juha_teuvonnen on 2023-05-04
The hardware in question works when plugged into Raspberry pi using Raspbian OS. Which makes me think it's not defective.

I am plugging it into my Dell laptop running Ubuntu 22.04.2 LTS and it does not seem to work.

OS verison I am running:
```
user@user-Latitude-7290:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy

```

The device show us in "lsusb" output:
```
user@user-Latitude-7290:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:568c Realtek Semiconductor Corp. Integrated Webcam HD
**Bus 001 Device 002: ID 0bda:0811 Realtek Semiconductor Corp. Realtek 8812AU/8821AU 802.11ac WLAN Adapter [USB Wireless Dual-Band Adapter 2.4/5Ghz]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The driver is installed using dkms:
```
user@user-Latitude-7290:~$ dkms status
rtl8812au/4.3.8.12175.20140902+dfsg, 5.19.0-41-generic, x86_64: installed

```
I rebooted the machine multiple times after the driver was installed.

When I am running "iwconfig" and "ifconfig" I am not seeing "wlan0" interface, only "wlp2s0" which is built-in Intel wifi chip and enp0s31f6 which is built in wired ethernet.
```
user@user-Latitude-7290:~$ iwconfig 
lo        no wireless extensions.

enp0s31f6  no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"6B17H1-5G"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: 80:CC:9C:3E:B2:84   
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:44   Missed beacon:0

```

```
user@user-Latitude-7290:~$ ifconfig -a
enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether e4:b9:7a:2f:3c:1f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xef200000-ef220000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 468  bytes 47945 (47.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 468  bytes 47945 (47.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.2  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4486:38d0:f794:349f  prefixlen 64  scopeid 0x20<link>
        ether 00:bb:60:0b:8b:00  txqueuelen 1000  (Ethernet)
        RX packets 11675  bytes 11310236 (11.3 MB)
        RX errors 0  dropped 7  overruns 0  frame 0
        TX packets 4962  bytes 1310559 (1.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

This is what I see in "dmesg" output that seems relevant:
```
[    2.986534] 8812au: loading out-of-tree module taints kernel.
[    3.021959] RTL871X: module init start
[    3.021963] RTL871X: rtl8812au v4.3.8_12175.20140902
[    3.021965] RTL871X: build time: May  4 2023 02:49:05
[    3.022042] ------------[ cut here ]------------
[    3.022043] WARNING: CPU: 3 PID: 331 at net/wireless/core.c:901 wiphy_register+0x676/0x8f0 [cfg80211]
[    3.022111] Modules linked in: fjes(+) 8812au(O+) cfg80211 msr parport_pc ppdev lp ramoops pstore_blk drm parport reed_solomon pstore_zone efi_pstore ip_tables x_tables autofs4 hid_generic rtsx_pci_sdmmc i2c_hid_acpi intel_lpss_pci intel_lpss_acpi i2c_i801 ahci xhci_pci i2c_hid intel_lpss crc32_pclmul e1000e i2c_smbus rtsx_pci libahci xhci_pci_renesas wmi hid video idma64
[    3.022145] CPU: 3 PID: 331 Comm: systemd-modules Tainted: G           O      5.19.0-41-generic #42~22.04.1-Ubuntu
[    3.022148] Hardware name: Dell Inc. Latitude 7290/09386V, BIOS 1.7.1 10/15/2018
[    3.022149] RIP: 0010:wiphy_register+0x676/0x8f0 [cfg80211]
[    3.022177] Code: fc 0b 00 41 80 ff 01 0f 86 89 fd ff ff e9 78 f1 07 00 0f 0b b8 ea ff ff ff e9 3e fc ff ff 0f 0b b8 ea ff ff ff e9 32 fc ff ff <0f> 0b b8 ea ff ff ff e9 26 fc ff ff 0f 0b b8 ea ff ff ff e9 1a fc
[    3.022179] RSP: 0018:ffffb69cc0fbb950 EFLAGS: 00010246
[    3.022182] RAX: ffffffffc06b5190 RBX: 0000000000000000 RCX: ffffffffc06b5180
[    3.022184] RDX: ffffffffc06b5220 RSI: 0000000000000005 RDI: 0000000000000008
[    3.022185] RBP: ffffb69cc0fbb9e8 R08: 0000000000000000 R09: 0000000000000000
[    3.022187] R10: 0000000000000000 R11: 0000000000000000 R12: ffff928a8335b3a0
[    3.022188] R13: 0000000000000006 R14: 0000000000000005 R15: 0000000000000001
[    3.022190] FS:  00007fcbeb236900(0000) GS:ffff928d9e4c0000(0000) knlGS:0000000000000000
[    3.022192] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[    3.022194] CR2: 00007f61ab83f000 CR3: 0000000118034003 CR4: 00000000003706e0
[    3.022196] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[    3.022197] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[    3.022199] Call Trace:
[    3.022201]  <TASK>
[    3.022203]  ? _rtw_malloc+0x2d/0x37 [8812au]
[    3.022269]  ? _rtw_memcpy+0x10/0x1e [8812au]
[    3.022300]  ? rtw_5g_rates_init+0x1a/0x26 [8812au]
[    3.022337]  rtw_wdev_alloc+0xfc/0x2ac [8812au]
[    3.022391]  rtw_usb_if1_init+0x10b/0x233 [8812au]
[    3.022428]  rtw_drv_init+0x36f/0x427 [8812au]
[    3.022471]  usb_probe_interface+0xeb/0x2c0
[    3.022479]  really_probe+0x1e1/0x3c0
[    3.022483]  __driver_probe_device+0x12a/0x1b0
[    3.022486]  driver_probe_device+0x23/0xd0
[    3.022488]  __driver_attach+0xc3/0x260
[    3.022491]  ? __device_attach_driver+0x160/0x160
[    3.022493]  bus_for_each_dev+0x80/0xe0
[    3.022498]  driver_attach+0x1e/0x30
[    3.022500]  bus_add_driver+0x187/0x230
[    3.022502]  driver_register+0x95/0x110
[    3.022504]  usb_register_driver+0x8d/0x140
[    3.022507]  ? 0xffffffffc0773000
[    3.022510]  rtw_drv_entry+0x65/0x1000 [8812au]
[    3.022550]  do_one_initcall+0x46/0x220
[    3.022555]  ? kmem_cache_alloc_trace+0x1a6/0x330
[    3.022560]  do_init_module+0x52/0x220
[    3.022565]  load_module+0xb56/0xd40
[    3.022568]  ? security_kernel_post_read_file+0x5c/0x80
[    3.022574]  ? kernel_read_file+0x245/0x2a0
[    3.022579]  __do_sys_finit_module+0xcc/0x150
[    3.022581]  ? __do_sys_finit_module+0xcc/0x150
[    3.022586]  __x64_sys_finit_module+0x18/0x30
[    3.022589]  do_syscall_64+0x59/0x90
[    3.022594]  ? do_syscall_64+0x69/0x90
[    3.022595]  ? do_syscall_64+0x69/0x90
[    3.022597]  ? do_syscall_64+0x69/0x90
[    3.022599]  entry_SYSCALL_64_after_hwframe+0x63/0xcd
[    3.022602] RIP: 0033:0x7fcbeb11ea3d
[    3.022605] Code: 5b 41 5c c3 66 0f 1f 84 00 00 00 00 00 f3 0f 1e fa 48 89 f8 48 89 f7 48 89 d6 48 89 ca 4d 89 c2 4d 89 c8 4c 8b 4c 24 08 0f 05 <48> 3d 01 f0 ff ff 73 01 c3 48 8b 0d c3 a3 0f 00 f7 d8 64 89 01 48
[    3.022606] RSP: 002b:00007ffc0afc7728 EFLAGS: 00000246 ORIG_RAX: 0000000000000139
[    3.022609] RAX: ffffffffffffffda RBX: 0000562a25476da0 RCX: 00007fcbeb11ea3d
[    3.022611] RDX: 0000000000000000 RSI: 00007fcbeb716441 RDI: 0000000000000006
[    3.022612] RBP: 0000000000020000 R08: 0000000000000000 R09: 0000000000000002
[    3.022613] R10: 0000000000000006 R11: 0000000000000246 R12: 00007fcbeb716441
[    3.022614] R13: 0000562a25477490 R14: 00007fcbeb6226b9 R15: 0000562a25481d90
[    3.022618]  </TASK>
[    3.022620] ---[ end trace 0000000000000000 ]---


```

---

### Post by chili555 on 2023-05-04
The driver you installed is a bit old and, I'm confident, only builds with many warnings which, taken altogether, are fatal. I suggest that you remove it and try this instead: [https://github.com/morrownr/8821au-20210708](https://github.com/morrownr/8821au-20210708)

If you need step-by-step guidance, please post back.

---

### Post by juha_teuvonnen on 2023-05-04
> **chili555 said:**
> The driver you installed is a bit old and, I'm confident, only builds with many warnings which, taken altogether, are fatal. I suggest that you remove it and try this instead: [https://github.com/morrownr/8821au-20210708](https://github.com/morrownr/8821au-20210708)

If you need step-by-step guidance, please post back.

I followed the installation instructions from the above github  link and it worked out perfectly. Thanks!

---

### Post by chili555 on 2023-05-04
Awesome! Glad it's working! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

