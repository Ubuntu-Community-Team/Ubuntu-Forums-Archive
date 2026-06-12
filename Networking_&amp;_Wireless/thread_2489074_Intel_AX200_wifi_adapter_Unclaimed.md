---
title: "Intel AX200 wifi adapter Unclaimed ?"
date: 2023-07-17
forum: Networking &amp; Wireless
---

### Post by jaw3000 on 2023-07-17
I recently had to re-install Ubuntu, and am having trouble getting it to use the internal Intel Intel AX200 wifi adapter on my motherboard. On my old Ubuntu installation, it had no trouble detecting or using the Intel adapter, along with a Broadcom adapter I have connected, and I could configure it and switch between wifi adapters via the Settings app GUI. After the re-installation, only the Broadcom wifi adapter shows up in wifi settings. The Broadcom adapter works fine. Running ```
sudo lshw -C network
``` shows the Intel adapter is 'UNCLAMED," yet ```
[FONT=Liberation Serif][SIZE=3][COLOR=#000000]lspci -nnk | grep -iA2 net[/COLOR][/SIZE][/FONT]
```[FONT=Liberation Serif][SIZE=3][COLOR=#000000] correctly shows the adapter as using "kernel modules: iwlwifi." The Broadcom adapter says "kernel driver in use" though. Any idea how to get this working? I have already reinstalled linux-modules-extra to no avail. I'm running [/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=&amp]ubuntu 5.19.0-46-generic (22.04.02 LTS).[/FONT][/COLOR][FONT=Liberation Serif][SIZE=3][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[COLOR=#000000][FONT=&amp]  *-network UNCLAIMED       [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       description: Network controller[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       product: Wi-Fi 6 AX200[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       bus info: pci@0000:06:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       version: 1a[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       capabilities: pm msi pciexpress msix cap_list[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       configuration: latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       resources: memory:fc600000-fc603fff

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  *-network[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       product: BCM43602 802.11ac Wireless LAN SoC[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       vendor: Broadcom Inc. and subsidiaries[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       bus info: pci@0000:09:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       logical name: wlp9s0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       version: 01[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       serial: xxx[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/COLOR]

---

### Post by chili555 on 2023-07-18
What does this tell us?

```
sudo modprobe iwlwifi
sudo dmesg | grep iwl
```Are you missing firmware?

---

### Post by jaw3000 on 2023-07-19
[COLOR=#000000][FONT=UICTFontTextStyleBody]Firmware is installed. It seems Windows (dual-boot) was putting a hold of some sort on the Intel wifi adapter on shutdown, and it was not being loaded by Ubuntu. I disconnected power to force a full shutdown on all components, and the Intel adapter loaded fine after in Ubuntu. However, after the Intel adapter recognized itself, it dropped the Broadcom wifi adapter, which was working fine before the full shutdown, and now is listed as UNCLAIMED and not loading. I did not install or uninstall anything, or edit any config files. The Broadcom driver and firmware are obviously installed because it was working fine before the shutdown. [/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][/FONT]
[/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]Does anyone know how to &#8220;claim&#8221; both of these adapters and have both available for selection in Ubuntu? [/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][/FONT]
[/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]```
~$ sudo dmesg | grep iwlwifi[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.252882] iwlwifi_compat: loading out-of-tree module taints kernel.[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.254704] Loading modules backported from iwlwifi[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.254707] iwlwifi-stack-public:master:9904:0e80336f[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.362650] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.381824] iwlwifi 0000:06:00.0: api flags index 2 larger than supported by driver[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.381836] iwlwifi 0000:06:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.382615] iwlwifi 0000:06:00.0: loaded firmware version 73.35c0a2c6.0 cc-a0-73.ucode op_mode [/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]iwlmvm[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.471508] iwlwifi 0000:06:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.604657] iwlwifi 0000:06:00.0: Detected RF HR B3, rfid=0x10a100[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.670009] iwlwifi 0000:06:00.0: base HW address: xxx[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 4.686539] iwlwifi 0000:06:00.0 wlp6s0: renamed from wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 11.807213] iwlwifi 0000:06:00.0: Not associated and the session protection is over already...[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 14.506678] iwlwifi 0000:06:00.0: Not associated and the session protection is over already...[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 16.777851] iwlwifi 0000:06:00.0: Not associated and the session protection is over already...[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][ 30.328228] iwlwifi 0000:06:00.0: Got NSS = 4 - trimming to 2 [/FONT][FONT=UICTFontTextStyleBody]
```[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody][/FONT]
[/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]```
sudo lshw -C network[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] *-network [/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] description: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] product: Wi-Fi 6 AX200[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]bus info: pci@0000:06:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] logical name: wlp6s0[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] version: 1a[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] serial: xxx[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] configuration: broadcast=yes driver=iwlwifi driverversion=5.19.0-46-generic [/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]firmware=73.35c0a2c6.0 cc-a0-73.ucode ip=xxx latency=0 link=yes multicast=yes[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] resources: irq:24 memory:fc500000-fc503fff[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] *-network UNCLAIMED[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] description: Network controller[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] product: BCM43602 802.11ac Wireless LAN SoC[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] vendor: Broadcom Inc. and subsidiaries[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] bus info: pci@0000:0a:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] version: 01[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] capabilities: pm msi pciexpress cap_list[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] configuration: latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody] resources: memory:fc000000-fc007fff memory:fbc00000-fbffffff[/FONT][FONT=UICTFontTextStyleBody]
```[/FONT][/COLOR]

---

### Post by chili555 on 2023-07-19
Please try this: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

---

