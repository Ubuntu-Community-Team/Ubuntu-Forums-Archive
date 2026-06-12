---
title: "bluetooth device not reachable"
date: 2021-01-16
forum: Networking &amp; Wireless
---

### Post by abelito8 on 2021-01-16
I've tried several of the solutions proposed in the forum (all that I could find at least) but none of them work for me, I am on an asus with kubuntu 20.04, I installed and uninstalled bluez, blueman but nothing is happening....my earplugs are simply not connecting (NB I was able to connected to another device that has ubuntu 20.04 on it)

---

### Post by jeremy31 on 2021-01-17
Post results from terminal for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by abelito8 on 2021-01-17
thank you, here we go (I uninstalled all bluetooth software because there was a chance they were conflicting with something)

[FONT=monospace][COLOR=#000000]$ lsusb; dmesg | egrep -i 'blue|firm'[/COLOR]
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 011: ID 8087:0a2a Intel Corp.  
Bus 001 Device 006: ID 145f:01c8 Trust Trust Wireless Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.000000] [[COLOR=#FF5454]**Firm**[/COLOR][COLOR=#000000]ware Bug]: TPM Final Events table missing or invalid[/COLOR]
[    0.169538] Spectre V2 : Enabling Restricted Speculation for [COLOR=#FF5454]**firm**[/COLOR][COLOR=#000000]ware calls[/COLOR]
[    0.333423] ACPI: [[COLOR=#FF5454]**Firm**[/COLOR][COLOR=#000000]ware Bug]: BIOS _OSI(Linux) query ignored[/COLOR]
[    1.088711] tpm_crb MSFT0101:00: [[COLOR=#FF5454]**Firm**[/COLOR][COLOR=#000000]ware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80[/COLOR]
[    1.088732] tpm_crb MSFT0101:00: [[COLOR=#FF5454]**Firm**[/COLOR][COLOR=#000000]ware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80[/COLOR]
[    1.588537] [drm] Finished loading DMC [COLOR=#FF5454]**firm**[/COLOR][COLOR=#000000]ware i915/skl_dmc_ver1_27.bin (v1.27)[/COLOR]
[   15.306307] elan_i2c i2c-ELAN1000:00: Elan Touchpad: Module ID: 0x0005, [COLOR=#FF5454]**Firm**[/COLOR][COLOR=#000000]ware: 0x0004, Sample: 0x000d, IAP: 0x000e[/COLOR]
[   15.323592] iwlwifi 0000:01:00.0: loaded [COLOR=#FF5454]**firm**[/COLOR][COLOR=#000000]ware version 29.1654887522.0 op_mode iwlmvm[/COLOR]
[   15.395752] iwlwifi 0000:01:00.0: Allocated 0x00400000 bytes for [COLOR=#FF5454]**firm**[/COLOR][COLOR=#000000]ware monitor.[/COLOR]
[  711.898695] audit: type=1107 audit(1610884275.455:51): pid=800 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name=
"org.[COLOR=#FF5454]**blue**[/COLOR][COLOR=#000000]z" pid=22997 label="snap.chromium.chromium"[/COLOR]

[/FONT]

---

### Post by jeremy31 on 2021-01-18
The 8087:0a2a device is Intel Bluetooth but there is no sign of the bluetooth firmware loading

---

### Post by abelito8 on 2021-01-20
so you're saying my laptop has no bluetooth capacity? or that I should install some to gain the capacity to use bluetooth?

---

### Post by abelito8 on 2021-01-20
I followed this thread
[https://itectec.com/ubuntu/ubuntu-ubuntu-20-04-bluetooth-not-working/](https://itectec.com/ubuntu/ubuntu-ubuntu-20-04-bluetooth-not-working/)

and I can connect, I can even listen to some sound...but it's completely scattered and keeps on getting disconnected....

---

