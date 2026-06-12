---
title: "Huawei E5776 not detected as mobile broadband modem ubuntu 14.04"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by mrphconnor on 2014-08-08
[COLOR=#333333][FONT=UbuntuRegular][FONT=arial black]When connecting the device with a USB cable lsusb command crashes in the terminal. 
dmesg shows more errors, any ideas how to fix this and allow ubuntu to detect the device?[/FONT]

[/FONT][/COLOR]
> [12852.415901] CPU: 2 PID: 783 Comm: ModemManager Tainted: G        W    3.13.0-24-generic #47~precise2-Ubuntu
[12852.415992] Hardware name: eMachines eME732/HM55_CP, BIOS V1.01 08/13/2010
[12852.416058] task: f53ab3c0 ti: ebaa6000 task.ti: ebaa6000
[12852.416112] EIP: 0060:[<f881567e>] EFLAGS: 00010283 CPU: 2
[12852.416168] EIP is at usb_wwan_write+0x10e/0x2c0 [usb_wwan]
[12852.416222] EAX: 00000001 EBX: e3c45240 ECX: 00000001 EDX: f2708000
[12852.416283] ESI: 00000000 EDI: 00000000 EBP: ebaa7e9c ESP: ebaa7e50
[12852.416343]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[12852.416396] CR0: 80050033 CR2: 00000040 CR3: 2ba46000 CR4: 000007f0
[12852.416455] Stack:
[12852.416477]  ebcd1be8 ebaa7ea8 c13e26a0 00000078 ebaa7e64 00000000 00000001 00001c04
[12852.416631]  ebec6db8 e3c45288 ebec6c00 e3c45280 f2708000 f3ad2df0 00000001 00000001
[12852.416780]  f8882000 f1f3c600 00000007 ebaa7ed4 f856b751 00000001 00000296 c13e2bde
[12852.416930] Call Trace:
[12852.416983]  [<c13e26a0>] ? tty_mode_ioctl+0xa0/0x510
[12852.417071]  [<f856b751>] serial_write+0x51/0xd0 [usbserial]
[12852.417159]  [<c13e2bde>] ? n_tty_ioctl_helper+0x2e/0x70
[12852.417245]  [<c13dec13>] n_tty_write+0x143/0x340
[12852.417325]  [<c1087930>] ? try_to_wake_up+0x1a0/0x1a0
[12852.417409]  [<c13dbd11>] tty_write+0x101/0x210
[12852.417480]  [<c13dead0>] ? process_echoes+0x70/0x70
[12852.417558]  [<c13dbc10>] ? tty_write_lock+0x50/0x50
[12852.417639]  [<c1181c9d>] vfs_write+0x9d/0x1e0
[12852.417710]  [<c10b738b>] ? ktime_get_ts+0x4b/0x120
[12852.417787]  [<c1182167>] SyS_write+0x57/0xa0
[12852.417862]  [<c168d3cd>] sysenter_do_call+0x12/0x28
[12852.417936] Code: 02 8b 40 08 e8 94 2e cb c8 85 c0 0f 88 fc 00 00 00 81 7c 24 3c 00 10 00 00 b8 00 10 00 00 0f 4e 44 24 3c 8b 54 24 30 89 44 24 38 <8b> 47 40 8b 4c 24 38 e8 c6 73 af c8 8b 54 24 38 8b 44 24 34 89
[12852.418518] EIP: [<f881567e>] usb_wwan_write+0x10e/0x2c0 [usb_wwan] SS:ESP 0068:ebaa7e50
[12852.418651] CR2: 0000000000000040
[12852.438142] ---[ end trace 930c0f6428b9e4a5 ]---
[12856.711325] ISO 9660 Extensions: Microsoft Joliet Level 1
[12856.712596] ISOFS: changing to secondary root
[12868.212757] systemd-hostnamed[7469]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[14286.575679] option1 ttyUSB0: GSM modem (1-port

---

### Post by mrphconnor on 2014-08-24
Seeing this error too.. not sure if its related

> Error mounting /dev/sr1 at /media/liminal/My Broadband: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500" "/dev/sr1" "/media/liminal/My Broadband"' exited with non-zero exit status 32: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: /dev/sr1 already mounted or /media/liminal/My Broadband busy




---

### Post by gojkok on 2015-02-03
Same problem here. I tried everything on other forums but without results. I hope that this problem will be solved soon.

---

### Post by mrphconnor on 2015-02-03
Sorry, I gave up in the end and bought a usb dongle instead.
Can't provide any further assistance in getting this working.

---

### Post by jeremy31 on 2015-02-03
Can it be unmounted as sr1?  I had an android cell phone that I couldn't access the files on until I unmounted it as sr1, there were some windows programs there

---

