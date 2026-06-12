---
title: "Ubuntu 22.04 Wifi not working sometimes - Dual Boot - Network Unclaimed"
date: 2023-05-27
forum: Networking &amp; Wireless
---

### Post by luxolu on 2023-05-27
Hi guys,

First, I'm sorry i feel i needed to post this because i have tried many things to solve this but i couldn't yet.

To add some context, I'm using a laptop XPG Xenia 15. It has Dual Boot configured (at first it came with Windows 10 (never upgraded to 11) and i added a new partition for Ubuntu 20.04)

After some months, Ubuntu 22.04 got released so i upgraded it.

This is kind of weird because i usually use this laptop for work (ubuntu 22.04) and just sometimes i use Windows 10 in order to play some game with friends. Sometimes after I use windows, Ubuntu 22.04 starts having issues with the wifi (ethernet and usb tethering using my cellphone works well).

Many things i have fixed it by trying the following:


[LIST]
[*]Reinstalling driver for my network device (wifi)
[*]Reinstalling network-manager and restarting the service
[*]Restarting the laptop many times
[/LIST]

Just to let you know, using Windows 10, the wifi is always working well.

A bit of additional information is that i'm using Ubuntu 22.04 and the kernel is 5.19.0-42-generic and when i run this command:

```
lshw -C network
```

A fragment of the result is :

*-network UNCLAIMED
       description: Network controller
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3e:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:ae600000-ae603fff




Please, help me.

Luis

---

### Post by chili555 on 2023-05-27
Is Fast Boot an issue? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

Are there any clues in the message log? ```
sudo modprobe iwlwifi && sudo dmesg | grep iwl
```

---

### Post by luxolu on 2023-05-27
Hi!

I tried disabling fast boot and it worked automatically!

Anyways i run the command you asked for:

[    5.225183] iwlwifi 0000:3e:00.0: enabling device (0000 -> 0002)
[    5.257353] iwlwifi 0000:3e:00.0: api flags index 2 larger than supported by driver
[    5.257373] iwlwifi 0000:3e:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37
[    5.257894] iwlwifi 0000:3e:00.0: loaded firmware version 72.daa05125.0 cc-a0-72.ucode op_mode iwlmvm
[    5.838596] iwlwifi 0000:3e:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    5.961482] iwlwifi 0000:3e:00.0: Detected RF HR B3, rfid=0x10a100
[    6.031247] iwlwifi 0000:3e:00.0: base HW address: 5c:80:b6:12:2c:e9
[    6.048082] iwlwifi 0000:3e:00.0 wlp62s0: renamed from wlan0


Not sure if that is relevant now that this is working correctly.

Thank you very much @chily555!

---

### Post by chili555 on 2023-05-27
> I tried disabling fast boot and it worked automatically!Awesome! Glad it's working!

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

