---
title: "[Ubuntu 23 | Bluetooth] luetooth Audio Getting Discunnected Frequently"
date: 2023-09-12
forum: Networking &amp; Wireless
---

### Post by sethu47 on 2023-09-12
In my Ubuntu 23.04, the bluetooth audio keeps getting crashed. Please suggest me some fix.

Distributor ID: Ubuntu
Description:    Ubuntu 23.04
Release:        23.04
Codename:       lunar

Motherboard: ROG STRIX B550-F GAMING WIFI II
Bluetooth: MEDIATEK Corp. MT7921K (RZ608) Wi-Fi 6E 80MHz


Detailed HW Info: [https://linux-hardware.org/?probe=ecc13f9294](https://linux-hardware.org/?probe=ecc13f9294)


[COLOR=#CCCCCC][FONT=&amp]
[COLOR=#569cd6]2023-09-12T17:42:45.929909+05:30 Ubuntu-23-04 wireplumber[7454][/COLOR]: [COLOR=#b5cea8]0x56315ef87708[/COLOR]: [COLOR=#ce9178]error 24[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:45.959441+05:30 Ubuntu-23-04 acpid[/COLOR]: [COLOR=#ce9178]input device has been disconnected, fd 25[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:46.011727+05:30 Ubuntu-23-04 wireplumber[7454][/COLOR]: [COLOR=#ce9178](bluez_output.28_FA_19_EA_16_D0.1-19) running -> error (Received error event)[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:46.055418+05:30 Ubuntu-23-04 pipewire[7449][/COLOR]: [COLOR=#569cd6]pw.node[/COLOR]: [COLOR=#ce9178](bluez_output.28_FA_19_EA_16_D0.1-68) running -> error (Received error event)[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:46.055605+05:30 Ubuntu-23-04 gsd-media-keys[7992][/COLOR]: [COLOR=#ce9178]Unable to get default sink[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:46.055999+05:30 Ubuntu-23-04 gsd-media-keys[7992][/COLOR]: [COLOR=#569cd6]gvc_mixer_card_get_index[/COLOR]: [COLOR=#ce9178]assertion 'GVC_IS_MIXER_CARD (card)' failed[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:46.056098+05:30 Ubuntu-23-04 gnome-shell[7741][/COLOR]: [COLOR=#569cd6]gvc_mixer_card_get_index[/COLOR]: [COLOR=#ce9178]assertion 'GVC_IS_MIXER_CARD (card)' failed[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:46.056191+05:30 Ubuntu-23-04 systemd[1][/COLOR]: [COLOR=#ce9178]Starting systemd-rfkill.service - Load/Save RF Kill Switch Status...[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:46.057790+05:30 Ubuntu-23-04 systemd[1][/COLOR]: [COLOR=#ce9178]Started systemd-rfkill.service - Load/Save RF Kill Switch Status.[/COLOR]
[COLOR=#569cd6]2023-09-12T17:42:51.063947+05:30 Ubuntu-23-04 systemd[1][/COLOR]: [COLOR=#569cd6]systemd-rfkill.service[/COLOR]: [COLOR=#ce9178]Deactivated successfully.[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:10.059497+05:30 Ubuntu-23-04 systemd[1][/COLOR]: [COLOR=#ce9178]Starting systemd-rfkill.service - Load/Save RF Kill Switch Status...[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:10.061935+05:30 Ubuntu-23-04 systemd[1][/COLOR]: [COLOR=#ce9178]Started systemd-rfkill.service - Load/Save RF Kill Switch Status.[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:10.323091+05:30 Ubuntu-23-04 kernel[/COLOR]: [ [COLOR=#b5cea8]9674.585915[/COLOR]] [COLOR=#569cd6]Bluetooth[/COLOR]: [COLOR=#569cd6]hci0[/COLOR]: [COLOR=#ce9178]Device setup in 155269 usecs[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:10.323110+05:30 Ubuntu-23-04 kernel[/COLOR]: [ [COLOR=#b5cea8]9674.585921[/COLOR]] [COLOR=#569cd6]Bluetooth[/COLOR]: [COLOR=#569cd6]hci0[/COLOR]: [COLOR=#ce9178]HCI Enhanced Setup Synchronous Connection command is advertised, but not supported.[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:10.595087+05:30 Ubuntu-23-04 kernel[/COLOR]: [ [COLOR=#b5cea8]9674.859293[/COLOR]] [COLOR=#569cd6]Bluetooth[/COLOR]: [COLOR=#569cd6]hci0[/COLOR]: [COLOR=#ce9178]AOSP extensions version v1.00[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:10.595101+05:30 Ubuntu-23-04 kernel[/COLOR]: [ [COLOR=#b5cea8]9674.859299[/COLOR]] [COLOR=#569cd6]Bluetooth[/COLOR]: [COLOR=#569cd6]hci0[/COLOR]: [COLOR=#ce9178]AOSP quality report is supported[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:15.064055+05:30 Ubuntu-23-04 systemd[1][/COLOR]: [COLOR=#569cd6]systemd-rfkill.service[/COLOR]: [COLOR=#ce9178]Deactivated successfully.[/COLOR]
[COLOR=#569cd6]2023-09-12T17:43:17.055144+05:30 Ubuntu-23-04 bluetoothd[4325][/COLOR]: [COLOR=#569cd6]profiles/audio/avctp.c:avctp_connect_cb() connect to 28:FA:xx:xx:xx:xx[/COLOR]: [COLOR=#ce9178]Software caused connection abort (103)[/COLOR]
[/FONT][/COLOR]

---

