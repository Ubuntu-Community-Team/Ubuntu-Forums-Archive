---
title: "How do I get my Network (and settings) back in 20.04?"
date: 2020-07-23
forum: Networking &amp; Wireless
---

### Post by juglugs2 on 2020-07-23
[COLOR=#242729][FONT=Arial]I have lost my network connections (Ethernet, WiFi and Bluetooth) on Ubuntu 20.04. I don't know what I did to lose them, but after a reboot, they had gone. There is no network icon in the system tray and in settings, there is no setting for WiFi and no connections in the network submenu.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I can boot from a Live USB image and everything works well.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So, from another answer I found, I backed up, then copied the netplanner, and NetworkManager files and directories from the Live USB to my computer. Rebooted into the "normal" Ubuntu environment and still nothing.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I ran sudo```
 lshw -C network
``` and the output is:
[/FONT][/COLOR]
```
*-network UNCLAIMED       
       description: Network controller
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f7100000-f717ffff memory:f7180000-f718ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
```

[COLOR=#242729][FONT=Arial]My NetworkManager.conf file is:
[/FONT][/COLOR]```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
```

[COLOR=#242729][FONT=Arial]and my 01-network-manager-all.yaml file is:
[/FONT][/COLOR]
```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
[COLOR=#242729][FONT=Arial]Using sudo nmcli gives:[/FONT][/COLOR]
lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536

Use "nmcli device show" to get complete information about known devices and
"nmcli connection show" to get an overview on active connection profiles.

Consult nmcli(1) and nmcli-examples(7) manual pages for complete usage details.
```

[COLOR=#242729][FONT=Arial]I don't have ifconfig (net-tools) installed.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Running ```
nm-applet 
``` brings up a greyed out system tray icon, but when I click that, the window that opens (showing the connections) is empty.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any help is greatly appreciated.[/FONT][/COLOR]

---

### Post by praseodym on 2020-07-24
Please show
```

uname -a
dpkg -l linux-* | grep ii
```
Can you boot into an earlier kernel? If yes, does it work there?

---

### Post by juglugs2 on 2020-07-24
uname -a:

```
Linux marks-linux-box 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

dpkg -l linux-* | grep ii:


```
ii  linux-base                                 4.5ubuntu3.1         all          Linux image base package
ii  linux-firmware                             1.187.2              all          Firmware for Linux kernel drivers
ii  linux-headers-5.4.0-40                     5.4.0-40.44          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-40-generic             5.4.0-40.44          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-41                     5.4.0-41.45          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-41-generic             5.4.0-41.45          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-42                     5.4.0-42.46          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic             5.4.0-42.46          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-5.4.0-40-generic               5.4.0-40.44          amd64        Signed kernel image generic
ii  linux-image-5.4.0-41-generic               5.4.0-41.45          amd64        Signed kernel image generic
ii  linux-image-unsigned-5.4.0-42-generic      5.4.0-42.46          amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                       5.4.0-42.46          amd64        Linux Kernel Headers for development
ii  linux-modules-5.4.0-40-generic             5.4.0-40.44          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-41-generic             5.4.0-41.45          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-42-generic             5.4.0-42.46          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-40-generic       5.4.0-40.44          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-41-generic       5.4.0-41.45          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-nvidia-390-5.4.0-40-generic  5.4.0-40.44          amd64        Linux kernel nvidia modules for version 5.4.0-40
ii  linux-modules-nvidia-390-5.4.0-41-generic  5.4.0-41.45          amd64        Linux kernel nvidia modules for version 5.4.0-41
ii  linux-modules-nvidia-390-5.4.0-42-generic  5.4.0-42.46          amd64        Linux kernel nvidia modules for version 5.4.0-42
ii  linux-modules-nvidia-390-generic-hwe-20.04 5.4.0-42.46          amd64        Extra drivers for nvidia-390 for generic-hwe-20.04
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5 all          base package for ALSA and OSS sound systems

```

And yes! I can boot into 5.4.0-41 (and 5.4.0-40) and everything works - I'm replying to you from my Ubuntu machine on 5.4.0-41 now...

So something's borked in 5.4.0-42?

Thanks
Mark

---

### Post by praseodym on 2020-07-24
Yes, you miss this one

```
sudo apt install linux-modules-extra-5.4.0-42-generic
```

---

### Post by juglugs2 on 2020-07-24
Thank you - I actually got it working by:
```
sudo apt remove linux-image-unsigned-5.4.0-42-generic && sudo apt autoremove
```

I then followed that up with:

```
sudo apt install linux-image-5.4.0-42-generic && sudo apt install linux-modules-extra-5.4.0-42-generic
```

And it all works now - Thank you very much for your help!

---

