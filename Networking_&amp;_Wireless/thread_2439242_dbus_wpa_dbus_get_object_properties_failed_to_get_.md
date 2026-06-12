---
title: "dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none"
date: 2020-03-24
forum: Networking &amp; Wireless
---

### Post by alephfool on 2020-03-24
Hi guys,

I recently moved to Ubuntu after having issues on Manjaro where my computer would freeze when waking up, and prompt the Wireless password at the lockscreen before ever even trying to access the desktop.

I started receiving a few errors right off the bat and noticed that it also had something to do with my wpa_supplicant and a few USB ports; however I don't know where to proceed as I'm relatively new to Linux in the first place.

As it stands the only thing affecting me is a mild inconvience, I'll encounter a problem and my touchpad scroll up and down will stop functioning; but my journalctl -p 3 outputs many errors related to wpa_supplicant and -rfkill. 
My Wifi stays active, I don't lose connection, at least yet.

Errors below.

[HTML]-- Reboot --
Mar 23 20:07:53 preston-t480 wpa_supplicant[873]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 23 20:07:53 preston-t480 wpa_supplicant[873]: dbus: Failed to construct signal
Mar 23 20:07:54 preston-t480 spice-vdagent[1259]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Mar 23 20:08:16 preston-t480 pulseaudio[1641]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: The name org.ofono was not provided by any .service files
Mar 23 20:08:17 preston-t480 spice-vdagent[1763]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Mar 23 21:47:08 preston-t480 systemd-rfkill[4170]: Failed to open device rfkill0: No such device
Mar 23 21:47:08 preston-t480 wpa_supplicant[873]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 23 21:47:08 preston-t480 wpa_supplicant[873]: dbus: Failed to construct signal
Mar 23 21:52:41 preston-t480 canonical-livepatch[985]: while starting HTTP server: accept unix /var/snap/canonical-livepatch/95/livepatchd.sock: use of closed network connection
Mar 23 21:52:41 preston-t480 canonical-livepatch[985]: while starting HTTP server: accept unix /var/snap/canonical-livepatch/95/livepatchd-priv.sock: use of closed network connection
Mar 23 21:52:42 preston-t480 gdm3[1011]: GLib: g_hash_table_find: assertion 'version == hash_table->version' failed
-- Reboot --
Mar 23 21:53:03 preston-t480 wpa_supplicant[882]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 23 21:53:03 preston-t480 wpa_supplicant[882]: dbus: Failed to construct signal
Mar 23 21:53:04 preston-t480 spice-vdagent[1270]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Mar 23 21:53:13 preston-t480 pulseaudio[1647]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not: The name org.ofono was not provided by any .service files
Mar 23 21:53:14 preston-t480 spice-vdagent[1768]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Mar 24 01:33:44 preston-t480 kernel: audit: backlog limit exceeded
Mar 24 01:57:03 preston-t480 gnome-session-binary[1096]: Unrecoverable failure in required component org.gnome.Shell.desktop
Mar 24 02:29:29 preston-t480 systemd-rfkill[17022]: Failed to open device rfkill0: No such device
Mar 24 02:29:30 preston-t480 wpa_supplicant[882]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 24 02:29:30 preston-t480 wpa_supplicant[882]: dbus: Failed to construct signal
Mar 24 11:47:38 preston-t480 systemd-rfkill[17399]: Failed to open device rfkill4: No such device
Mar 24 11:47:38 preston-t480 wpa_supplicant[882]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 24 11:47:38 preston-t480 wpa_supplicant[882]: dbus: Failed to construct signal
Mar 24 12:01:44 preston-t480 systemd-rfkill[18010]: Failed to open device rfkill5: No such device
Mar 24 12:01:45 preston-t480 wpa_supplicant[882]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 24 12:01:45 preston-t480 wpa_supplicant[882]: dbus: Failed to construct signal
Mar 24 12:16:57 preston-t480 systemd-rfkill[18721]: Failed to open device rfkill6: No such device
Mar 24 12:16:58 preston-t480 wpa_supplicant[882]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 24 12:16:58 preston-t480 wpa_supplicant[882]: dbus: Failed to construct signal
Mar 24 12:31:23 preston-t480 kernel: usb 1-1: device descriptor read/64, error -71

[/HTML]

Specs
[HTML]System:    Host: preston-t480 Kernel: 5.3.0-42-generic x86_64 bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4) info: gnome-shell dm: gdm3 Distro: Ubuntu 18.04.4 LTS
Machine:   Device: laptop System: LENOVO product: 20L5CTO1WW v: ThinkPad T480 serial: N/A
           Mobo: LENOVO model: 20L5CTO1WW v: SDK0J40697 WIN serial: N/A
           UEFI: LENOVO v: N24ET48W (1.23 ) date: 02/20/2019
           Chassis: type: 10 serial: N/A
Battery    BAT0: charge: 21.2 Wh 100.0% condition: 21.2/24.0 Wh (88%) volts: 12.8/11.5
           model: SMP 01AV421 Li-poly serial: <filter>status: Full cycles: 180
           BAT1: charge: 20.0 Wh 99.8% condition: 20.0/24.1 Wh (83%) volts: 12.8/11.4
           model: Celxpert 01AV424 Li-poly serial: <filter>status: Full cycles: 85
CPU:       Quad core Intel Core i7-8650U (-MT-MCP-) arch: Kaby Lake rev.10 cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 16799
           clock speeds: min/max: 400/4200 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz 4: 800 MHz 5: 800 MHz 6: 800 MHz
           7: 800 MHz 8: 800 MHz
Graphics:  Card: Intel UHD Graphics 620 bus-ID: 00:02.0 chip-ID: 8086:5917
           Display Server: x11 (X.Org 1.20.5 ) driver: i915 Resolution: 1920x1080@60.02hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           version: 4.5 Mesa 19.2.8 (compat-v: 3.0) Direct Render: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel bus-ID: 00:1f.3 chip-ID: 8086:9d71
           Sound: Advanced Linux Sound Architecture v: k5.3.0-42-generic
Network:   Card-1: Intel Ethernet Connection (4) I219-LM
           driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6 chip-ID: 8086:15d7
           IF: enp0s31f6 state: down mac: <filter>
           Card-2: Intel Wireless 8265 / 8275 driver: iwlwifi bus-ID: 03:00.0 chip-ID: 8086:24fd
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 1024.2GB (1.7% used)
           ID-1: /dev/nvme0n1 model: SAMSUNG_MZVLB1T0HALR size: 1024.2GB serial: <filter> firmware: 5L2QEXA7
Partition: ID-1: / size: 938G used: 17G (2%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 43.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 2870
Info:      Processes: 318 Uptime: 8:07 Memory: 3638.7/31991.4MB Init: systemd v: 237 runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.201 running in gnome-terminal-) inxi: 2.3.56 [/HTML]

Wireless card: Intel Dual Band 8265 Wireless AC (2 x 2) & Bluetooth 4.1 with vPro

---

