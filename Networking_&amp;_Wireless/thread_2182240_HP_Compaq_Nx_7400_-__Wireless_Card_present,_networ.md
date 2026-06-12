---
title: "HP Compaq Nx 7400 -  Wireless Card present, networks present, not connecting"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Tymoteusz on 2013-10-20
Hi there - I'm another Linux newbie having wireless problems. I've looked around, and tried some troubleshooting, but I'm still having no luck. 
From what I've read in this forum, there is some specific information you need, regarding my computer, so I have tried to include as much info as possible below.
Any help would be much appreciated.


```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ uname -a[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Linux tymoteusz-desktop 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 17:49:16 UTC 2013 i686 i686 i386 GNU/Linux[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ lsb_release -a[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]No LSB modules are available.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Distributor ID:   Ubuntu[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Description:   Ubuntu 12.04.3 LTS[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Release:   12.04[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Codename:   precise[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ lspci[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 01)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]ymoteusz@tymoteusz-desktop:~$ lspci | egrep -i 'Network | Wireless'[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ lspci -vvnn | grep 14e4[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ sudo iwconfig[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][sudo] password for tymoteusz: [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]wlan0     IEEE 802.11abg  ESSID:off/any  [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          Encryption key:off[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          Power Management:on[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]lo        no wireless extensions.[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]eth0      no wireless extensions.[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ sudo lsmod[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Module                  Size  Used by[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]bnep                   17852  2 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]rfcomm                 38400  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]bluetooth             211552  10 bnep,rfcomm[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]vesafb                 13540  1 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]parport_pc             27612  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ppdev                  12849  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]b44                    31223  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ssb                    51554  1 b44[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]wl                   2902285  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_hda_codec_si3054    12864  1 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_hda_codec_analog    75716  1 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]lib80211               14040  1 wl[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_hda_intel          38819  2 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]arc4                   12509  2 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_hda_codec         118650  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]coretemp               13324  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]iwl3945                64560  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_hwdep              13276  1 snd_hda_codec[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]iwlegacy               88125  1 iwl3945[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_pcm                85934  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_seq_midi           13132  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]pcmcia                 39854  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_rawmidi            25157  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]gpio_ich               13278  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]mac80211              541819  2 iwl3945,iwlegacy[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_seq_midi_event     14475  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]yenta_socket           27427  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]joydev                 17329  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_timer              28931  2 snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]pcmcia_rsrc            18367  1 yenta_socket[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]mac_hid                13077  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]psmouse                82769  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]cfg80211              453919  4 wl,iwl3945,iwlegacy,mac80211[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd                    57014  14 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]microcode              18433  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]soundcore              12600  1 snd[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]serio_raw              13031  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]snd_page_alloc         18398  2 snd_hda_intel,snd_pcm[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]lpc_ich                17048  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]lp                     17455  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]parport                40930  3 parport_pc,ppdev,lp[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]hid_generic            12484  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]usbhid                 46125  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]hid                    83037  2 hid_generic,usbhid[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]firewire_ohci          35914  0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ahci                   25631  2 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]libahci                26336  1 ahci[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]firewire_core          62086  1 firewire_ohci[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]crc_itu_t              12627  1 firewire_core[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ rfkill list all[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]0: phy0: Wireless LAN[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Soft blocked: no[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Hard blocked: no[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ lspci -k | egrep -iA2 'net|wire|eth'[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Subsystem: Hewlett-Packard Company Device 30a2[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Kernel driver in use: firewire_ohci[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Kernel modules: firewire-ohci[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Subsystem: Hewlett-Packard Company NX7300 laptop[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Kernel driver in use: b44[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]--[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Subsystem: Hewlett-Packard Company PRO/Wireless 3945ABG [Golan] Network Connection[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Kernel driver in use: iwl3945[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Kernel modules: wl, iwl3945[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ [/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ lshw -C network[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]WARNING: you should run this program as super-user.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  *-network DISABLED      [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       product: PRO/Wireless 3945ABG [Golan] Network Connection[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       physical id: 0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       bus info: pci@0000:10:00.0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       logical name: wlan0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       version: 02[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       serial: 00:19:d2:12:91:e1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       width: 32 bits[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       capabilities: bus_master cap_list ethernet physical wireless[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       configuration: broadcast=yes driver=iwl3945 driverversion=3.8.0-31-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       resources: irq:11 memory:f4000000-f4000fff[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  *-network[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       product: BCM4401-B0 100Base-TX[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       vendor: Broadcom Corporation[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       physical id: e[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       bus info: pci@0000:02:0e.0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       logical name: eth0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       version: 02[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       serial: 00:1a:4b:57:27:16[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       size: 100Mbit/s[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       capacity: 100Mbit/s[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       width: 32 bits[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.8 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]       resources: irq:10 memory:f4108000-f4109fff[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]WARNING: output may be incomplete or inaccurate, you should run this program as super-user.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ [/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ ifconfig[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]eth0      Link encap:Ethernet  HWaddr 00:1a:4b:57:27:16  [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          inet6 addr: fe80::21a:4bff:fe57:2716/64 Scope:Link[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          RX packets:23246 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          TX packets:15343 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          collisions:0 txqueuelen:1000 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          RX bytes:17307583 (17.3 MB)  TX bytes:3508259 (3.5 MB)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          Interrupt:10 [/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]lo        Link encap:Local Loopback  [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          RX packets:782 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          TX packets:782 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          collisions:0 txqueuelen:0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]          RX bytes:62178 (62.1 KB)  TX bytes:62178 (62.1 KB)[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ iwlist scan[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]wlan0     Failed to read scan data : Network is down[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]lo        Interface doesn't support scanning.[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]eth0      Interface doesn't support scanning.[/FONT][/COLOR]
```

```
[COLOR=#2E8B57][FONT=Monaco]tymoteusz@tymoteusz-desktop:~$ nm-tool[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]NetworkManager Tool[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]State: connected (global)[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Type:              Wired[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Driver:            b44[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  State:             connected[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Default:           yes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  HW Address:        00:1A:4B:57:27:16[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]  Capabilities:[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Carrier Detect:  yes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Speed:           100 Mb/s[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]  Wired Properties[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Carrier:         on[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]  IPv4 Settings:[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Address:         192.168.1.8[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Prefix:          24 (255.255.255.0)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Gateway:         192.168.1.1[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]    DNS:             192.168.1.1[/FONT][/COLOR]


[COLOR=#2E8B57][FONT=Monaco]- Device: wlan0 ----------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Type:              802.11 WiFi[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Driver:            iwl3945[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  State:             unavailable[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Default:           no[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  HW Address:        00:19:D2:12:91:E1[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]  Capabilities:[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]  Wireless Properties[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    WEP Encryption:  yes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    WPA Encryption:  yes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    WPA2 Encryption: yes[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]  Wireless Access Points [/FONT][/COLOR]


```

---

### Post by wildmanne39 on 2013-10-20
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source
```
reboot does it connect if not then do:

```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by Tymoteusz on 2013-10-20
Thanks for that, although I'm no sure if I'm getting it correctly, After 
```
gksudo gedit /etc/pm/power.d/wireless
```
[COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]it creates empty text file. What should I enter there? Is it supposed to look like that?
[COLOR=#000000][FONT=Ubuntu Mono]```
[/FONT][/COLOR]#!/bin/sh/sbin/iwconfig wlan0 power off[COLOR=#000000][FONT=Ubuntu Mono]
```
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2013-10-20
It should look like this:
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```

---

### Post by Tymoteusz on 2013-10-20
OK, so I did it and unfortunately it didn't solve the problem :( [COLOR=#2E8B57][FONT=Monaco]lshw -C network [/FONT][/COLOR]still shows network as disabled.[COLOR=#2E8B57][FONT=Monaco][/FONT][/COLOR]

---

### Post by wildmanne39 on 2013-10-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Tymoteusz on 2013-10-20
OK. The file is attached as requested.[ATTACH]247101[/ATTACH]

---

### Post by wildmanne39 on 2013-10-20
There is an error in your dns server so please set your wireless settings to match the screenshots.
You have two errors in the information you posted one says hardware error detected please make sure your card is setted good after you do the above repost a new wireless file and lets see if the error messages are still there.

Also power management is still on did you save the file and reboot after you edited it?
Thanks

---

