---
title: "Installing TP Link TL-WN723N wireless usb adapter"
date: 2016-08-20
forum: Networking &amp; Wireless
---

### Post by Kim Foltz on 2016-08-20
I am trying to install a TP Link TL-WN723N wireless usb adapter in Kubuntu 16.04. The wired connection works without a problem.

lsusb shows:
```
Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
```

lshw -C network shows:
```
*-network               
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: enp4s2
       version: 10
       serial: 00:e0:4c:aa:1b:d4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.111 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:dc00(size=256) memory:df8fff00-df8fffff memory:df900000-df91ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlxc46e1f16f59a
       serial: c4:6e:1f:16:f5:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu multicast=yes wireless=unassociated
```

I have installed the latest driver 8188eu driver from Github and blacklisted the original r8188eu driver.

lsmod shows:

```
Module                  Size  Used by
cfg80211              565248  0
dcdbas                 16384  0
serio_raw              16384  0
snd_hda_codec_analog    16384  1
snd_hda_codec_generic    77824  1 snd_hda_codec_analog
input_leds             16384  0
snd_hda_intel          36864  3
snd_hda_codec         135168  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_analog
snd_hda_core           73728  4 snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_hda_codec_analog
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
lpc_ich                24576  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  16 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
8250_fintek            16384  0
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
8188eu                716800  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
psmouse               126976  0
8139too                36864  0
8139cp                 28672  0
mii                    16384  2 8139cp,8139too
pata_acpi              16384  0
floppy                 73728  0
i915                 1208320  8
fjes                   28672  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  10 i915,drm_kms_helper
```

So even though the new 8188eu driver appears available it isn't being used by the TP Link usb adapter.

Can anyone help me solve this problem?

---

### Post by jeremy31 on 2016-08-20
Your results show the wireless is disabled, please post results for ```
rfkill list all
```

Please use code tags for terminal output, see link in my signature as it preserves formatting and prevents smilies

---

### Post by Kim Foltz on 2016-08-21
The command returns nothing.

Syslog shows the following when the device is inserted into the usb port.

```

kernel: [93399.648029] usb 1-3: new high-speed USB device number 3 using ehci-pci
Aug 21 17:52:20 kip-OptiPlex-745 kernel: [93399.780835] usb 1-3: New USB device found, idVendor=0bda, idProduct=8179
Aug 21 17:52:20 kip-OptiPlex-745 kernel: [93399.780843] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 21 17:52:20 kip-OptiPlex-745 kernel: [93399.780848] usb 1-3: Product: 802.11n NIC
Aug 21 17:52:20 kip-OptiPlex-745 kernel: [93399.780852] usb 1-3: Manufacturer: Realtek
Aug 21 17:52:20 kip-OptiPlex-745 kernel: [93399.780856] usb 1-3: SerialNumber: 00E04C0001
Aug 21 17:52:20 kip-OptiPlex-745 kernel: [93399.781582] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
Aug 21 17:52:20 kip-OptiPlex-745 kernel: [93399.816832] EEPROM ID = 0x8129
Aug 21 17:52:20 kip-OptiPlex-745 NetworkManager[2063]: <info>  [1471819940.5567] (wlan0): driver supports SSID scans (scan_capa 0x3F).
Aug 21 17:52:20 kip-OptiPlex-745 NetworkManager[2063]: <info>  [1471819940.5568] (wlan0): using WEXT for WiFi device control
Aug 21 17:52:20 kip-OptiPlex-745 NetworkManager[2063]: <info>  [1471819940.5601] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/3)
Aug 21 17:52:20 kip-OptiPlex-745 mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3"
Aug 21 17:52:20 kip-OptiPlex-745 mtp-probe: bus: 1, device: 3 was not an MTP device
Aug 21 17:52:21 kip-OptiPlex-745 kernel: [93400.844970] r8188eu 1-3:1.0 wlxc46e1f16f59a: renamed from wlan0
Aug 21 17:52:21 kip-OptiPlex-745 NetworkManager[2063]: <info>  [1471819941.5992] device (wlan0): interface index 4 renamed iface from 'wlan0' to 'wlxc46e1f16f59a'
Aug 21 17:52:21 kip-OptiPlex-745 NetworkManager[2063]: <info>  [1471819941.6139] devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/net/wlxc46e1f16f59a, iface: wlxc46e1f16f59a)
Aug 21 17:52:21 kip-OptiPlex-745 NetworkManager[2063]: <info>  [1471819941.6140] device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/net/wlxc46e1f16f59a, iface: wlxc46e1f16f59a): no ifupdown configuration found.
Aug 21 17:52:21 kip-OptiPlex-745 NetworkManager[2063]: <info>  [1471819941.6141] device (wlxc46e1f16f59a): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 21 17:52:21 kip-OptiPlex-745 kernel: [93400.876158] IPv6: ADDRCONF(NETDEV_UP): wlxc46e1f16f59a: link is not ready
Aug 21 17:52:23 kip-OptiPlex-745 ModemManager[1999]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3': not supported by any plugin

```

How is the system assigning the r8188eu driver when it is blacklisted and lsmod doesn't show the driver as available?

---

### Post by Kim Foltz on 2016-08-22
Anyone?

---

### Post by chili555 on 2016-08-22
> How is the system assigning the r8188eu driver when it is blacklisted and lsmod doesn't show the driver as available? The command *lsmod* shows that 8188eu is loaded but that no other modules are also loaded that depend on it. I believe 8188eu is a unified driver in that all its dependencies, issue and off-spring are all built in. If there is an interface, wlxc46e1f16f59a in this case, there is a driver.

With the device inserted, does this still come back blank?```
rfkill list all
```> *-network [COLOR="#FF0000"]DISABLED[/COLOR]
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlxc46e1f16f59a
       serial: c4:6e:1f:16:f5:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu multicast=yes wireless=unassociatedDisabled usually means that the hardware switch or key combination is set to disable the wireless. Installing different drivers, blacklisting, etc. is unlikely to move the switch.

What make and model computer is it?

---

### Post by jeremy31 on 2016-08-22
This might be another victim of systemd's renaming of devices.  I compiled Larry Finger's version of 8188eu, did a manual modprobe and then checked parameters with ```
grep [[:alnum:]] /sys/module/8188eu/parameters/*
```
And these two parameters are suspicious
```
/sys/module/8188eu/parameters/if2name:wlan%d
/sys/module/8188eu/parameters/ifname:wlan%d
```

I would recommend editing /etc/default/grub using ```
sudo -H gedit /etc/default/grub
```
Then scroll to the line that starts with ```
GRUB_CMDLINE_LINUX_DEFAULT
```

Mine happens to be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash'
```
And add ```
net.ifnames=0
``` inside of the quotes so that the line becomes
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ifnames=0"
```

Save, exit gedit, then
```
sudo update-grub
```
reboot and see if the driver works with wifi

---

### Post by Kim Foltz on 2016-08-22
However unusual this seems, sudo rfkill list all only produces a line feed with the adapter plugged in. My interpretation is a driver problem is preventing the interface from ever being established so it can't be blocked.

The changes to the Grub command line didn't change the outcome. The connect option in the Connection Manager is greyed out. Filling in a password for the router and attempting a connection produces the message Failed to get Secrets from router.

r8188eu is the original system driver and it is blacklisted. I double checked /etc/modprobe.d/blacklist.conf and it is listed on the last line. 8188eu is the most recent driver from Github and lsmod shows it as available. Beats me but the exact same model of adapter worked out of the box without problems in 14.04.

---

### Post by jeremy31 on 2016-08-23
Post new results for ```
lshw -c net
```

---

### Post by Kim Foltz on 2016-08-23
lshw -c net shows:

```

 *-network               
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:aa:1b:d4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.111 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:dc00(size=256) memory:df8fff00-df8fffff memory:df900000-df91ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlxc46e1f16f59a
       serial: c4:6e:1f:16:f5:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu multicast=yes wireless=unassociated

```

ifconfig - a shows

```

eth0      Link encap:Ethernet  HWaddr 00:e0:4c:aa:1b:d4  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2600:8803:8400:312:2e0:4cff:feaa:1bd4/64 Scope:Global
          inet6 addr: fe80::2e0:4cff:feaa:1bd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6854342 (6.8 MB)  TX bytes:510672 (510.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:12138 (12.1 KB)  TX bytes:12138 (12.1 KB)

wlxc46e1f16f59a Link encap:Ethernet  HWaddr c4:6e:1f:16:f5:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

In trying to track this problem down I discovered the Ubuntu family now uses Predictable Network Interface Names so I shouldn't expect to see a wlan0 interface any longer. If that is true, what is the correct default entry in the /etc/network/interfaces file?

---

### Post by jeremy31 on 2016-08-23
Systemd must be ignoring the ifname for USB.  Just to check if your driver is the same, post ```
grep [[:alnum:]] /sys/module/8188eu/parameters/*
```

---

### Post by Kim Foltz on 2016-08-23
I am running a Dell and I think the correct grub parameters are net.ifnames=0 biosdevname=0. Changed the parameters and updated grub but I still am stuck with the Predictable Network Interface Names  Didn't change any other results.

grep [[:alnum:]] /sys/module/8188eu/parameters/* shows:

```

/sys/module/8188eu/parameters/debug:1
/sys/module/8188eu/parameters/if2name:wlan%d
/sys/module/8188eu/parameters/ifname:wlan%d
/sys/module/8188eu/parameters/rtw_80211d:0
/sys/module/8188eu/parameters/rtw_ampdu_amsdu:0
/sys/module/8188eu/parameters/rtw_ampdu_enable:1
/sys/module/8188eu/parameters/rtw_antdiv_cfg:2
/sys/module/8188eu/parameters/rtw_antdiv_type:0
/sys/module/8188eu/parameters/rtw_busy_thresh:40
/sys/module/8188eu/parameters/rtw_cbw40_enable:3
/sys/module/8188eu/parameters/rtw_channel:1
/sys/module/8188eu/parameters/rtw_channel_plan:66
/sys/module/8188eu/parameters/rtw_chip_version:0
/sys/module/8188eu/parameters/rtw_enusbss:0
/sys/module/8188eu/parameters/rtw_fw_iol:1
/sys/module/8188eu/parameters/rtw_ht_enable:1
/sys/module/8188eu/parameters/rtw_hwpdn_mode:2
/sys/module/8188eu/parameters/rtw_hwpwrp_detect:0
/sys/module/8188eu/parameters/rtw_hw_wps_pbc:1
/sys/module/8188eu/parameters/rtw_initmac:(null)
/sys/module/8188eu/parameters/rtw_ips_mode:1
/sys/module/8188eu/parameters/rtw_lbkmode:0
/sys/module/8188eu/parameters/rtw_low_power:0
/sys/module/8188eu/parameters/rtw_lowrate_two_xmit:1
/sys/module/8188eu/parameters/rtw_max_roaming_times:2
/sys/module/8188eu/parameters/rtw_mc2u_disable:0
/sys/module/8188eu/parameters/rtw_mp_mode:0
/sys/module/8188eu/parameters/rtw_network_mode:0
/sys/module/8188eu/parameters/rtw_notch_filter:0
/sys/module/8188eu/parameters/rtw_power_mgnt:1
/sys/module/8188eu/parameters/rtw_rf_config:5
/sys/module/8188eu/parameters/rtw_rfintfs:2
/sys/module/8188eu/parameters/rtw_rx_stbc:1
/sys/module/8188eu/parameters/rtw_smart_ps:2
/sys/module/8188eu/parameters/rtw_vcs_type:1
/sys/module/8188eu/parameters/rtw_vrtl_carrier_sense:2
/sys/module/8188eu/parameters/rtw_wifi_spec:0
/sys/module/8188eu/parameters/rtw_wmm_enable:1

```

---

### Post by jeremy31 on 2016-08-24
I wonder what this file contains ```
cat /lib/udev/rules.d/73-special-net-names.rules
```

---

### Post by Kim Foltz on 2016-08-24
Thank you to all those who tried to help with this question but I decided to buy different hardware. This computer belongs to a relative who needs a clean solution that isn't likely to break with the next kernel update. Disappointed  to find Kubuntu released an LTS version without more stable network tools.

This question should be considered closed.

---

### Post by jeremy31 on 2016-08-24
You may want to get a TP Link WN722N 150 Mbps USB wireless adapter as some of us here have been using them without issue

I actually found something that eliminates the renaming ```
sudo ln -s /dev/null /etc/udev/rules.d/80-net-setup-link.rules
```
It should allow the wifi to work

---

