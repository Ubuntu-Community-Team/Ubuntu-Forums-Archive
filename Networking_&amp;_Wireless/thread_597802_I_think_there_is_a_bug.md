---
title: "I think there is a bug"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by sasanf on 2007-10-30
I think there is a bug with the wireless driver or some other software the driver relies on.  My wireless card works great in Windows XP; in Ubuntu 7.10, my access to the net is slow.  Sometimes, I experience a lot of time outs (even disconnects).  I do not experience any of this on my home connection which is a 8 meg or the ECU connection which is a 10 meg when I am booted into Windows.  My laptop is a Dell Inspiron 6400 with a Dell Wireless 1390 WLAN Mini-Card.  Thanks in advance.

---

### Post by Lambert on 2007-10-31
> **sasanf said:**
> I think there is a bug with the wireless driver or some other software the driver relies on.  My wireless card works great in Windows XP; in Ubuntu 7.10, my access to the net is slow.  Sometimes, I experience a lot of time outs (even disconnects).  I do not experience any of this on my home connection which is a 8 meg or the ECU connection which is a 10 meg when I am booted into Windows.  My laptop is a Dell Inspiron 6400 with a Dell Wireless 1390 WLAN Mini-Card.  Thanks in advance.

I wouldn't necesarily call it a bug. Most manufactures don't provide driver support in linux but they do on windows. So there is better support on the windows side which is why it functions better there.

The community can try to help you trouble shoot and stabelize your connection in linux. Sometimes that takes some time and a few posts to find the problem.

If you want you can open a terminal and run these commands and post the output.

```

sudo lshw -C network

sudo iwconfig

```

Also you can open up syslog from the administrators menu and look through there for errors or anything relating to your wireless device.

I did just read a report where there is a general bug that was confirmed on the networking stack in ubuntu to cause slow networking but I haven't seen the actual bug report yet. Your problem could be there.

---

### Post by sasanf on 2007-10-31
Okay,  I'll put in the commands and I will check out the logs.  I will post results.  Thanks.

---

### Post by sasanf on 2007-10-31
lshw comman output:

 *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:ce:37:03:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=150.216.224.179 latency=0 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:d4:0e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s

---

### Post by sasanf on 2007-10-31
iwconfig output:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"taho"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:17:0F:8C:A1:70   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=83/100  Signal level=-50 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sasanf on 2007-10-31
How to do I turn off Smiles?  I can't post the logs until I do that.

---

### Post by Lambert on 2007-10-31
When you're posting page down to the Additional options section. You'll see a section where it says disable smilies.

---

### Post by sasanf on 2007-10-31
Log Output:

Oct 26 00:01:54 superman-laptop init: tty5 main process (4446) killed by TERM signal
Oct 26 00:01:54 superman-laptop init: tty2 main process (4448) killed by TERM signal
Oct 26 00:01:54 superman-laptop init: tty3 main process (4450) killed by TERM signal
Oct 26 00:01:54 superman-laptop init: tty1 main process (4452) killed by TERM signal
Oct 26 00:01:54 superman-laptop init: tty6 main process (4453) killed by TERM signal
Oct 26 00:01:54 superman-laptop init: tty4 main process (4445) killed by TERM signal
Oct 26 00:01:54 superman-laptop avahi-daemon[5391]: Got SIGTERM, quitting.
Oct 26 00:01:54 superman-laptop avahi-daemon[5391]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Oct 26 00:01:56 superman-laptop rpc.statd[4318]: Caught signal 15, un-registering and exiting.
Oct 26 00:01:58 superman-laptop mountd[5203]: Caught signal 15, un-registering and exiting.
Oct 26 08:27:52 superman-laptop NetworkManager: <info>  starting... 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.293733] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.581572] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.582047] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.582422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.583140] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.644018] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.644571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.644935] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.645308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.645804] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.646479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.647278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.648279] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.648743] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.649226] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.650175] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.650623] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.651088] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.652010] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.652451] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.652911] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.694831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.695214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.695563] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.695908] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.696250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.696590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.696938] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.698010] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.698529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.698980] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.699506] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.699970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.702078] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.702524] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.702962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.703433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.704007] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.704463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.704919] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.705370] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.705795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.706218] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.706639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.707060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.707496] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.707917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.708338] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.708759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.709203] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.709623] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.710043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.710463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.710882] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.711301] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.711720] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.712138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.712555] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.712973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.713398] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.713828] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.714245] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.714663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.715091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 26 08:27:52 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 26 08:27:52 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 08:27:52 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 08:27:52 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 26 08:27:52 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 26 08:27:52 superman-laptop NetworkManager: <debug> [1193401672.783176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 26 08:27:53 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 08:27:53 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 08:27:53 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 26 08:27:53 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.283755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.284946] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.285791] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.286500] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.287206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.287948] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.288653] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.297428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.298265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.298971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.299679] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.300430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.301178] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.301912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.302669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.303392] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.304186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.304906] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.305642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.306355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.307065] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.307775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.308492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.309264] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.310068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.310771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.311496] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.312195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.312891] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.321832] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 26 08:27:53 superman-laptop NetworkManager: <debug> [1193401673.322568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: Successfully dropped root privileges.
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: avahi-daemon 0.6.20 starting up.
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: Successfully called chroot().
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: Successfully dropped remaining capabilities.
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: No service file found in /etc/avahi/services.
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: Network interface enumeration completed.
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 26 08:27:54 superman-laptop avahi-daemon[5357]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 2944219812.
Oct 26 08:27:54 superman-laptop hcid[5392]: Bluetooth HCI daemon
Oct 26 08:27:54 superman-laptop hcid[5392]: Starting SDP server
Oct 26 08:27:54 superman-laptop hcid[5392]: Created local server at unix:abstract=/var/run/dbus-k3i3ugEb0W,guid=29558d02676c1930ae72b6004721dd4a
Oct 26 08:27:54 superman-laptop audio[5404]: Bluetooth Audio daemon
Oct 26 08:27:54 superman-laptop audio[5404]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 26 08:27:54 superman-laptop audio[5404]: Unix socket created: 5
Oct 26 08:27:54 superman-laptop input[5405]: Bluetooth Input daemon
Oct 26 08:27:54 superman-laptop input[5405]: Registered input manager path:/org/bluez/input
Oct 26 08:27:54 superman-laptop audio[5404]: add_service_record: got record id 0x10000
Oct 26 08:27:54 superman-laptop audio[5404]: add_service_record: got record id 0x10001
Oct 26 08:27:54 superman-laptop audio[5404]: Registered manager path:/org/bluez/audio
Oct 26 08:27:55 superman-laptop NetworkManager: <debug> [1193401675.240281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 26 08:27:57 superman-laptop ntpd[5475]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 26 08:27:57 superman-laptop ntpd[5476]: precision = 1.000 usec
Oct 26 08:27:57 superman-laptop ntpd[5476]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 26 08:27:57 superman-laptop ntpd[5476]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 26 08:27:57 superman-laptop ntpd[5476]: Listening on interface #2 lo, ::1#123 Enabled
Oct 26 08:27:57 superman-laptop ntpd[5476]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 26 08:27:57 superman-laptop ntpd[5476]: kernel time sync status 0040
Oct 26 08:27:57 superman-laptop ntpd[5476]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: host name not found: ntp.ubuntu.com
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: host name not found: clock.tricity.wsu.edu
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: host name not found: wuarchive.wustl.edu
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: host name not found: gilbreth.ecn.purdue.edu
Oct 26 08:27:59 superman-laptop ntpd_initres[5531]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 26 08:28:17 superman-laptop hcid[5392]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 26 08:28:17 superman-laptop hcid[5392]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 26 08:28:28 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 08:28:29 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 26 08:28:29 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 26 08:28:29 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 26 08:28:30 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 26 08:28:31 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 26 08:28:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 26 08:28:31 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 26 08:28:32 superman-laptop NetworkManager: <debug> [1193401712.189344] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 26 08:28:32 superman-laptop avahi-daemon[5357]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 08:28:32 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 26 08:28:33 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 26 08:28:33 superman-laptop dhclient: DHCPNAK from 1.1.1.1
Oct 26 08:28:33 superman-laptop avahi-autoipd(eth1)[5942]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 26 08:28:33 superman-laptop avahi-autoipd(eth1)[5942]: Successfully called chroot().
Oct 26 08:28:33 superman-laptop avahi-autoipd(eth1)[5942]: Successfully dropped root privileges.
Oct 26 08:28:33 superman-laptop avahi-autoipd(eth1)[5942]: Starting with address 169.254.3.94
Oct 26 08:28:33 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 08:28:34 superman-laptop NetworkManager: <debug> [1193401714.189249] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 26 08:28:38 superman-laptop avahi-autoipd(eth1)[5942]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 26 08:28:38 superman-laptop avahi-daemon[5357]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 26 08:28:38 superman-laptop avahi-daemon[5357]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 08:28:38 superman-laptop avahi-daemon[5357]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 26 08:28:42 superman-laptop avahi-autoipd(eth1)[5942]: Successfully claimed IP address 169.254.3.94
Oct 26 08:28:42 superman-laptop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth1 
Oct 26 08:28:42 superman-laptop avahi-autoipd(eth1)[5942]: Got SIGTERM, quitting.
Oct 26 08:28:42 superman-laptop avahi-autoipd(eth1)[5942]: Callout STOP, address 169.254.3.94 on interface eth1
Oct 26 08:28:42 superman-laptop avahi-daemon[5357]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 26 08:28:42 superman-laptop avahi-daemon[5357]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 26 08:28:42 superman-laptop avahi-daemon[5357]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 08:28:42 superman-laptop avahi-autoipd(eth1)[5943]: client: RTNETLINK answers: No such process
Oct 26 08:28:43 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 26 08:28:43 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct 26 08:28:43 superman-laptop dhclient: DHCPOFFER from 1.1.1.1
Oct 26 08:28:43 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 26 08:28:43 superman-laptop dhclient: DHCPACK from 1.1.1.1
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: Withdrawing address record for 150.216.224.29 on eth1.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 08:28:43 superman-laptop avahi-daemon[5357]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 08:28:44 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 26 08:28:44 superman-laptop dhclient: bound to 150.216.224.29 -- renewal in 1549 seconds.
Oct 26 08:28:44 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>    address 150.216.224.29 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>    broadcast 150.216.224.255 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>    gateway 150.216.224.254 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 26 08:28:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 26 08:28:44 superman-laptop avahi-daemon[5357]: Withdrawing address record for 150.216.224.29 on eth1.
Oct 26 08:28:44 superman-laptop avahi-daemon[5357]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:28:44 superman-laptop avahi-daemon[5357]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 08:28:44 superman-laptop avahi-daemon[5357]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 26 08:28:44 superman-laptop avahi-daemon[5357]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:28:44 superman-laptop avahi-daemon[5357]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 08:28:44 superman-laptop avahi-daemon[5357]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 08:28:45 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 26 08:28:45 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 26 08:28:45 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 26 08:28:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 26 08:28:45 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 26 08:28:45 superman-laptop ntpdate[6083]: can't find host clock.tricity.wsu.edu 
Oct 26 08:28:45 superman-laptop ntpdate[6083]: the NTP socket is in use, exiting
Oct 26 08:28:46 superman-laptop avahi-daemon[5357]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 08:28:55 superman-laptop NetworkManager: <debug> [1193401735.185244] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 26 08:29:05 superman-laptop NetworkManager: <debug> [1193401745.185258] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 26 08:29:25 superman-laptop NetworkManager: <debug> [1193401765.189343] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 26 08:32:05 superman-laptop NetworkManager: <debug> [1193401925.225221] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 26 08:32:58 superman-laptop ntpd[5476]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 26 08:32:58 superman-laptop ntpd[5476]: Listening on interface #5 eth1, 150.216.224.29#123 Enabled
Oct 26 08:34:15 superman-laptop NetworkManager: <debug> [1193402055.257242] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 26 08:36:35 superman-laptop NetworkManager: <debug> [1193402195.269390] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 26 08:38:35 superman-laptop NetworkManager: <debug> [1193402315.285219] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 26 08:44:48 superman-laptop init: tty4 main process (4450) killed by TERM signal
Oct 26 08:44:48 superman-laptop init: tty5 main process (4451) killed by TERM signal
Oct 26 08:44:48 superman-laptop init: tty2 main process (4453) killed by TERM signal
Oct 26 08:44:48 superman-laptop init: tty3 main process (4455) killed by TERM signal
Oct 26 08:44:48 superman-laptop init: tty1 main process (4457) killed by TERM signal
Oct 26 08:44:48 superman-laptop init: tty6 main process (4458) killed by TERM signal
Oct 26 08:44:48 superman-laptop avahi-daemon[5357]: Got SIGTERM, quitting.
Oct 26 08:44:48 superman-laptop avahi-daemon[5357]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:44:51 superman-laptop rpc.statd[4323]: Caught signal 15, un-registering and exiting.
Oct 26 08:44:53 superman-laptop mountd[5169]: Caught signal 15, un-registering and exiting.
Oct 26 08:58:32 superman-laptop NetworkManager: <info>  starting... 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.363011] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.656888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.657698] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.658345] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.658897] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.659582] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.721211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.723035] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.724370] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.725005] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.725564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.726861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.727323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.727765] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.728220] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.729143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.729587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.730045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.772675] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.773187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.773636] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.774164] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.774751] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.775241] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.775739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.776167] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.776595] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.777020] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.777445] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.777921] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.778402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.780576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.781024] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.781461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.781931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.782483] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.782959] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.783418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.783842] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.784263] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.784684] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.785104] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.785526] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.785962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.786396] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.786836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.787255] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.787672] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.788090] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.788507] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.788923] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.789340] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.789800] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.790235] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.790694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.791127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.791561] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.791991] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.792423] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.792855] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.793286] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.793717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.794147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.794581] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.795025] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 26 08:58:32 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 26 08:58:32 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 08:58:32 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 08:58:32 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 26 08:58:32 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 26 08:58:32 superman-laptop NetworkManager: <debug> [1193403512.863002] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 26 08:58:33 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 08:58:33 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 08:58:33 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 26 08:58:33 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.418107] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.418942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.419627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.420297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.420963] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.421627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.422288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.423036] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.423710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.424375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.425041] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.425705] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.426379] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.435250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.436014] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.436701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.437405] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.438078] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.438757] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.439462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.440170] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.440873] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.441575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.442276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.442992] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.443719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.444417] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.445114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.445810] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 26 08:58:33 superman-laptop NetworkManager: <debug> [1193403513.446545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: Successfully dropped root privileges.
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: avahi-daemon 0.6.20 starting up.
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: Successfully called chroot().
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: Successfully dropped remaining capabilities.
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: No service file found in /etc/avahi/services.
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: Network interface enumeration completed.
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 26 08:58:34 superman-laptop avahi-daemon[5321]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 3056180160.
Oct 26 08:58:34 superman-laptop hcid[5357]: Bluetooth HCI daemon
Oct 26 08:58:34 superman-laptop hcid[5357]: Starting SDP server
Oct 26 08:58:34 superman-laptop hcid[5357]: Created local server at unix:abstract=/var/run/dbus-it0Ra6iClj,guid=0415e878ed1ee90c3e13e3004721e47a
Oct 26 08:58:34 superman-laptop audio[5369]: Bluetooth Audio daemon
Oct 26 08:58:34 superman-laptop audio[5369]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 26 08:58:34 superman-laptop audio[5369]: Unix socket created: 5
Oct 26 08:58:34 superman-laptop input[5370]: Bluetooth Input daemon
Oct 26 08:58:34 superman-laptop input[5370]: Registered input manager path:/org/bluez/input
Oct 26 08:58:34 superman-laptop audio[5369]: add_service_record: got record id 0x10000
Oct 26 08:58:34 superman-laptop audio[5369]: add_service_record: got record id 0x10001
Oct 26 08:58:34 superman-laptop audio[5369]: Registered manager path:/org/bluez/audio
Oct 26 08:58:35 superman-laptop NetworkManager: <debug> [1193403515.423086] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 26 08:58:37 superman-laptop ntpd[5440]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 26 08:58:37 superman-laptop ntpd[5441]: precision = 1.000 usec
Oct 26 08:58:37 superman-laptop ntpd[5441]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 26 08:58:37 superman-laptop ntpd[5441]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 26 08:58:37 superman-laptop ntpd[5441]: Listening on interface #2 lo, ::1#123 Enabled
Oct 26 08:58:37 superman-laptop ntpd[5441]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 26 08:58:37 superman-laptop ntpd[5441]: kernel time sync status 0040
Oct 26 08:58:37 superman-laptop ntpd[5441]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: host name not found: ntp.ubuntu.com
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: host name not found: clock.tricity.wsu.edu
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: host name not found: wuarchive.wustl.edu
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: host name not found: gilbreth.ecn.purdue.edu
Oct 26 08:58:39 superman-laptop ntpd_initres[5481]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 26 08:58:55 superman-laptop hcid[5357]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 26 08:58:55 superman-laptop hcid[5357]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 26 08:59:03 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (6/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (7/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (8/10). 
Oct 26 08:59:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (9/10). 
Oct 26 08:59:06 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (10/10). 
Oct 26 08:59:06 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (11/10). 
Oct 26 08:59:06 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (12/10). 
Oct 26 08:59:07 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (13/10). 
Oct 26 08:59:07 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (14/10). 
Oct 26 08:59:07 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 26 08:59:08 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 26 08:59:09 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 26 08:59:09 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 26 08:59:09 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 26 08:59:10 superman-laptop avahi-daemon[5321]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 08:59:11 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 26 08:59:13 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 08:59:15 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 26 08:59:15 superman-laptop dhclient: DHCPACK from 1.1.1.1
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Withdrawing address record for 150.216.224.29 on eth1.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 08:59:15 superman-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 26 08:59:15 superman-laptop dhclient: bound to 150.216.224.29 -- renewal in 1396 seconds.
Oct 26 08:59:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>    address 150.216.224.29 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>    broadcast 150.216.224.255 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>    gateway 150.216.224.254 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 26 08:59:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Withdrawing address record for 150.216.224.29 on eth1.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 08:59:15 superman-laptop avahi-daemon[5321]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 08:59:16 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 26 08:59:16 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 26 08:59:16 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 26 08:59:16 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 26 08:59:16 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 26 08:59:16 superman-laptop ntpdate[5955]: can't find host clock.tricity.wsu.edu 
Oct 26 08:59:16 superman-laptop ntpdate[5955]: the NTP socket is in use, exiting
Oct 26 08:59:17 superman-laptop avahi-daemon[5321]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 08:59:34 superman-laptop NetworkManager: <debug> [1193403574.210785] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 26 09:00:29 superman-laptop NetworkManager: <debug> [1193403629.527847] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'taho' 
Oct 26 09:00:29 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / taho 
Oct 26 09:00:29 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 09:00:29 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5849
Oct 26 09:00:29 superman-laptop dhclient: killed old client process, removed PID file
Oct 26 09:00:29 superman-laptop dhclient: DHCPRELEASE on eth1 to 1.1.1.1 port 67
Oct 26 09:00:29 superman-laptop avahi-daemon[5321]: Withdrawing address record for 150.216.224.29 on eth1.
Oct 26 09:00:29 superman-laptop avahi-daemon[5321]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 09:00:29 superman-laptop avahi-daemon[5321]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 09:00:30 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 26 09:00:30 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 09:00:30 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 26 09:00:40 superman-laptop init: tty4 main process (4414) killed by TERM signal
Oct 26 09:00:41 superman-laptop init: tty5 main process (4415) killed by TERM signal
Oct 26 09:00:41 superman-laptop init: tty2 main process (4417) killed by TERM signal
Oct 26 09:00:41 superman-laptop init: tty3 main process (4419) killed by TERM signal
Oct 26 09:00:41 superman-laptop init: tty1 main process (4421) killed by TERM signal
Oct 26 09:00:41 superman-laptop init: tty6 main process (4422) killed by TERM signal
Oct 26 09:00:41 superman-laptop avahi-daemon[5321]: Got SIGTERM, quitting.
Oct 26 09:00:43 superman-laptop rpc.statd[4287]: Caught signal 15, un-registering and exiting.
Oct 26 09:00:45 superman-laptop mountd[5133]: Caught signal 15, un-registering and exiting.
Oct 26 10:57:08 superman-laptop NetworkManager: <info>  starting... 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.348297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.612228] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.612743] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.613163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.613998] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.673489] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.674060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.674485] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.675436] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.676531] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.676912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.677550] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.678007] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.678449] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.678886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.679916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.680355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.680802] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.681241] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.681686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.682124] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.682564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.683005] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.683438] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.683863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.684301] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.684764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.685203] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.685641] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.686107] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.686568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.687009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.687463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.687902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.688337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.688786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.689211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.689632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.690061] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.690495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.690924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.691356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.691792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.692228] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.692682] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.693114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.693540] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.694166] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.694598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.695017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.695433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.695868] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.696284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.696736] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.697187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.697627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.698594] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.699027] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.699470] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.700377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.700825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.701272] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.743468] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.743961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.744392] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 26 10:57:08 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 26 10:57:08 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 10:57:08 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 10:57:08 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 26 10:57:08 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 26 10:57:08 superman-laptop NetworkManager: <debug> [1193410628.814694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 26 10:57:09 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 10:57:09 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 10:57:09 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 26 10:57:09 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.461944] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.462587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.463029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.463460] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.463910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.464340] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.464896] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.465575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.466274] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.466950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.467624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.468335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.478026] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.478764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.479515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.480185] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.480893] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.481554] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.482215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.482874] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.483530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.484212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.484880] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.485677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.486339] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.487052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.487710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.488377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.489085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 26 10:57:09 superman-laptop NetworkManager: <debug> [1193410629.489690] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: Successfully dropped root privileges.
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: avahi-daemon 0.6.20 starting up.
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: Successfully called chroot().
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: Successfully dropped remaining capabilities.
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: No service file found in /etc/avahi/services.
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: Network interface enumeration completed.
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 26 10:57:10 superman-laptop avahi-daemon[5353]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 830690252.
Oct 26 10:57:10 superman-laptop hcid[5389]: Bluetooth HCI daemon
Oct 26 10:57:10 superman-laptop hcid[5389]: Starting SDP server
Oct 26 10:57:10 superman-laptop hcid[5389]: Created local server at unix:abstract=/var/run/dbus-GfUGTalx8p,guid=3b06ac55435419bdd2be360047220046
Oct 26 10:57:10 superman-laptop audio[5401]: Bluetooth Audio daemon
Oct 26 10:57:10 superman-laptop audio[5401]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 26 10:57:10 superman-laptop audio[5401]: Unix socket created: 5
Oct 26 10:57:10 superman-laptop input[5402]: Bluetooth Input daemon
Oct 26 10:57:10 superman-laptop input[5402]: Registered input manager path:/org/bluez/input
Oct 26 10:57:10 superman-laptop audio[5401]: add_service_record: got record id 0x10000
Oct 26 10:57:10 superman-laptop audio[5401]: add_service_record: got record id 0x10001
Oct 26 10:57:10 superman-laptop audio[5401]: Registered manager path:/org/bluez/audio
Oct 26 10:57:11 superman-laptop NetworkManager: <debug> [1193410631.313099] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 26 10:57:13 superman-laptop ntpd[5472]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 26 10:57:13 superman-laptop ntpd[5473]: precision = 1.000 usec
Oct 26 10:57:13 superman-laptop ntpd[5473]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 26 10:57:13 superman-laptop ntpd[5473]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 26 10:57:13 superman-laptop ntpd[5473]: Listening on interface #2 lo, ::1#123 Enabled
Oct 26 10:57:13 superman-laptop ntpd[5473]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 26 10:57:13 superman-laptop ntpd[5473]: kernel time sync status 0040
Oct 26 10:57:13 superman-laptop ntpd[5473]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: host name not found: ntp.ubuntu.com
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: host name not found: clock.tricity.wsu.edu
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: host name not found: wuarchive.wustl.edu
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: host name not found: gilbreth.ecn.purdue.edu
Oct 26 10:57:15 superman-laptop ntpd_initres[5528]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 26 10:57:34 superman-laptop hcid[5389]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Oct 26 10:57:34 superman-laptop hcid[5389]: Default authorization agent (:1.17, /org/bluez/auth) registered
Oct 26 10:57:42 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 26 10:57:42 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 26 10:57:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (6/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (7/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (8/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (9/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (10/10). 
Oct 26 10:57:44 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 26 10:57:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 26 10:57:46 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 26 10:57:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 26 10:57:46 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 26 10:57:47 superman-laptop NetworkManager: <debug> [1193410667.288857] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:D5:10 on wireless network 'taho' 
Oct 26 10:57:47 superman-laptop avahi-daemon[5353]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 10:57:48 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 26 10:57:50 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 10:57:51 superman-laptop NetworkManager: <debug> [1193410671.288933] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:D5:10 on wireless network 'taho' 
Oct 26 10:57:52 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Oct 26 10:57:52 superman-laptop dhclient: DHCPOFFER from 1.1.1.1
Oct 26 10:57:52 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 26 10:57:52 superman-laptop dhclient: DHCPACK from 1.1.1.1
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Withdrawing address record for 150.216.224.29 on eth1.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 10:57:52 superman-laptop dhclient: bound to 150.216.224.29 -- renewal in 1590 seconds.
Oct 26 10:57:52 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>    address 150.216.224.29 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>    broadcast 150.216.224.255 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>    gateway 150.216.224.254 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 26 10:57:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Withdrawing address record for 150.216.224.29 on eth1.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 10:57:52 superman-laptop avahi-daemon[5353]: Registering new address record for 150.216.224.29 on eth1.IPv4.
Oct 26 10:57:53 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 26 10:57:53 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 26 10:57:53 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 26 10:57:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 26 10:57:53 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 26 10:57:54 superman-laptop ntpdate[5966]: can't find host clock.tricity.wsu.edu 
Oct 26 10:57:54 superman-laptop ntpdate[5966]: the NTP socket is in use, exiting
Oct 26 10:57:54 superman-laptop avahi-daemon[5353]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 10:58:21 superman-laptop NetworkManager: <debug> [1193410701.900833] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:D5:10 on wireless network 'taho' 
Oct 26 10:58:51 superman-laptop NetworkManager: <debug> [1193410731.904939] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:D5:10 on wireless network 'taho' 
Oct 26 10:59:11 superman-laptop NetworkManager: <debug> [1193410751.908830] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:D5:10 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 26 11:01:01 superman-laptop init: tty2 main process (4450) killed by TERM signal
Oct 26 11:01:01 superman-laptop init: tty3 main process (4452) killed by TERM signal
Oct 26 11:01:01 superman-laptop init: tty1 main process (4454) killed by TERM signal
Oct 26 11:01:01 superman-laptop init: tty6 main process (4455) killed by TERM signal
Oct 26 11:01:01 superman-laptop init: tty4 main process (4447) killed by TERM signal
Oct 26 11:01:01 superman-laptop init: tty5 main process (4448) killed by TERM signal
Oct 26 11:01:02 superman-laptop avahi-daemon[5353]: Got SIGTERM, quitting.
Oct 26 11:01:02 superman-laptop avahi-daemon[5353]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.29.
Oct 26 11:01:04 superman-laptop rpc.statd[4320]: Caught signal 15, un-registering and exiting.
Oct 26 11:01:06 superman-laptop mountd[5165]: Caught signal 15, un-registering and exiting.
Oct 26 13:02:30 superman-laptop NetworkManager: <info>  starting... 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.400851] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.577778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.578555] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.579080] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.579596] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.580340] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.639125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.639881] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.640975] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.641525] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.642489] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.643027] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.643638] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.644303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.644745] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.645188] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.646062] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.646496] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.646929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.647847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.648906] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.690933] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.691411] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.691851] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.692299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.692716] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.693128] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.694165] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.694635] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.695054] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.696963] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.697406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.697779] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.698149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.698556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.699042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.699436] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.699832] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.700194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.700556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.700917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.701312] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.701664] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.702022] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.702380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.702738] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.703096] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.703487] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.703845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.704202] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.704559] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.704915] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.705355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.705717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.706076] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.706434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.706793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.707149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.707504] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.707860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.708215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.708571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.708926] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.709296] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.709652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 26 13:02:30 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 26 13:02:30 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 13:02:30 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 13:02:30 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 26 13:02:30 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 26 13:02:30 superman-laptop NetworkManager: <debug> [1193418150.777362] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 26 13:02:31 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 13:02:31 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 13:02:31 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 26 13:02:31 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.379663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.380332] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.380774] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.381199] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.381690] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.382127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.382485] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.382835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.383186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.383534] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.383883] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.384237] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.384581] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.384932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.385305] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.393633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.394130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.394560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.395005] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.395433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.395861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.396288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.396716] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.397141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.397579] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.398027] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.398455] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.398914] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.399353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 26 13:02:31 superman-laptop NetworkManager: <debug> [1193418151.399785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: Successfully dropped root privileges.
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: avahi-daemon 0.6.20 starting up.
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: Successfully called chroot().
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: Successfully dropped remaining capabilities.
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: No service file found in /etc/avahi/services.
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: Network interface enumeration completed.
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 26 13:02:32 superman-laptop avahi-daemon[5362]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 1597243280.
Oct 26 13:02:32 superman-laptop hcid[5398]: Bluetooth HCI daemon
Oct 26 13:02:32 superman-laptop hcid[5398]: Starting SDP server
Oct 26 13:02:32 superman-laptop hcid[5398]: Created local server at unix:abstract=/var/run/dbus-l3FUjTgbSg,guid=4623ed1bafcd751c5c42c40047221da8
Oct 26 13:02:32 superman-laptop audio[5410]: Bluetooth Audio daemon
Oct 26 13:02:32 superman-laptop audio[5410]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 26 13:02:32 superman-laptop audio[5410]: Unix socket created: 5
Oct 26 13:02:32 superman-laptop input[5411]: Bluetooth Input daemon
Oct 26 13:02:32 superman-laptop input[5411]: Registered input manager path:/org/bluez/input
Oct 26 13:02:32 superman-laptop audio[5410]: add_service_record: got record id 0x10000
Oct 26 13:02:32 superman-laptop audio[5410]: add_service_record: got record id 0x10001
Oct 26 13:02:32 superman-laptop audio[5410]: Registered manager path:/org/bluez/audio
Oct 26 13:02:33 superman-laptop NetworkManager: <debug> [1193418153.377375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 26 13:02:35 superman-laptop ntpd[5481]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 26 13:02:35 superman-laptop ntpd[5482]: precision = 1.000 usec
Oct 26 13:02:35 superman-laptop ntpd[5482]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 26 13:02:35 superman-laptop ntpd[5482]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 26 13:02:35 superman-laptop ntpd[5482]: Listening on interface #2 lo, ::1#123 Enabled
Oct 26 13:02:35 superman-laptop ntpd[5482]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 26 13:02:35 superman-laptop ntpd[5482]: kernel time sync status 0040
Oct 26 13:02:35 superman-laptop ntpd[5482]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: host name not found: ntp.ubuntu.com
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: host name not found: clock.tricity.wsu.edu
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: host name not found: wuarchive.wustl.edu
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: host name not found: gilbreth.ecn.purdue.edu
Oct 26 13:02:37 superman-laptop ntpd_initres[5531]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 26 13:03:00 superman-laptop hcid[5398]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Oct 26 13:03:00 superman-laptop hcid[5398]: Default authorization agent (:1.17, /org/bluez/auth) registered
Oct 26 13:03:05 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 26 13:03:06 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 26 13:03:09 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 13:03:10 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 26 13:03:11 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 26 13:03:11 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 26 13:03:11 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 26 13:03:12 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 26 13:03:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 26 13:03:12 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 26 13:03:12 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 26 13:03:12 superman-laptop avahi-daemon[5362]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 13:03:13 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 26 13:03:13 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 26 13:03:18 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Oct 26 13:03:30 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Oct 26 13:03:44 superman-laptop dhclient: No DHCPOFFERS received.
Oct 26 13:03:44 superman-laptop dhclient: Trying recorded lease 192.168.0.87
Oct 26 13:03:44 superman-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 26 13:03:44 superman-laptop avahi-daemon[5362]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 13:03:44 superman-laptop avahi-daemon[5362]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 26 13:03:47 superman-laptop avahi-daemon[5362]: Withdrawing address record for 192.168.0.87 on eth1.
Oct 26 13:03:47 superman-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 26 13:03:47 superman-laptop avahi-daemon[5362]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 13:03:47 superman-laptop avahi-autoipd(eth1)[5963]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 26 13:03:47 superman-laptop avahi-autoipd(eth1)[5963]: Successfully called chroot().
Oct 26 13:03:47 superman-laptop avahi-autoipd(eth1)[5963]: Successfully dropped root privileges.
Oct 26 13:03:47 superman-laptop avahi-autoipd(eth1)[5963]: Starting with address 169.254.3.94
Oct 26 13:03:52 superman-laptop avahi-autoipd(eth1)[5963]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 26 13:03:52 superman-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 26 13:03:52 superman-laptop avahi-daemon[5362]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 13:03:52 superman-laptop avahi-daemon[5362]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 26 13:03:56 superman-laptop avahi-autoipd(eth1)[5963]: Successfully claimed IP address 169.254.3.94
Oct 26 13:03:56 superman-laptop dhclient: Trying recorded lease 192.168.2.3
Oct 26 13:03:56 superman-laptop avahi-autoipd(eth1)[5963]: A routable address has been configured.
Oct 26 13:03:56 superman-laptop avahi-autoipd(eth1)[5963]: Callout UNBIND, address 169.254.3.94 on interface eth1
Oct 26 13:03:56 superman-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 26 13:03:56 superman-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 26 13:03:56 superman-laptop avahi-daemon[5362]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 26 13:03:56 superman-laptop avahi-daemon[5362]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 26 13:03:59 superman-laptop avahi-autoipd(eth1)[5963]: No longer a routable address configured, restarting probe process.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Withdrawing address record for 192.168.2.3 on eth1.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Oct 26 13:03:59 superman-laptop dhclient: Trying recorded lease 192.168.2.4
Oct 26 13:03:59 superman-laptop avahi-autoipd(eth1)[5963]: A routable address has been configured.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Registering new address record for 192.168.2.4 on eth1.IPv4.
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  Activation (eth1) failed for access point (taho) 
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  Activation (eth1) failed. 
Oct 26 13:03:59 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 13:03:59 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5866
Oct 26 13:03:59 superman-laptop dhclient: killed old client process, removed PID file
Oct 26 13:03:59 superman-laptop dhclient: DHCPRELEASE on eth1 to 1.1.1.1 port 67
Oct 26 13:03:59 superman-laptop dhclient: send_packet: Network is unreachable
Oct 26 13:03:59 superman-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Oct 26 13:03:59 superman-laptop avahi-autoipd(eth1)[5963]: Got SIGTERM, quitting.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Withdrawing address record for 192.168.2.4 on eth1.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Oct 26 13:03:59 superman-laptop avahi-daemon[5362]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 13:04:00 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 26 13:04:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 13:04:00 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 26 13:04:02 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 26 13:04:02 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 26 13:04:03 superman-laptop avahi-daemon[5362]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 26 13:04:09 superman-laptop avahi-autoipd(eth1)[6019]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 26 13:04:09 superman-laptop avahi-autoipd(eth1)[6019]: Successfully called chroot().
Oct 26 13:04:09 superman-laptop avahi-autoipd(eth1)[6019]: Successfully dropped root privileges.
Oct 26 13:04:09 superman-laptop avahi-autoipd(eth1)[6019]: Starting with address 169.254.3.94
Oct 26 13:04:11 superman-laptop avahi-daemon[5362]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 26 13:04:14 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Oct 26 13:04:14 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'TERMINATE'.  Response: 'TIMEOUT[CLI]' 
Oct 26 13:04:14 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't terminate wpasupplicant cleanly. 
Oct 26 13:04:14 superman-laptop avahi-daemon[5362]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 26 13:04:14 superman-laptop avahi-autoipd(eth1)[6019]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 26 13:04:14 superman-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 26 13:04:14 superman-laptop avahi-daemon[5362]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 13:04:14 superman-laptop avahi-daemon[5362]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 26 13:04:18 superman-laptop avahi-autoipd(eth1)[6019]: Successfully claimed IP address 169.254.3.94
Oct 26 13:07:36 superman-laptop ntpd[5482]: Listening on interface #4 eth1:avahi, 169.254.3.94#123 Enabled
Oct 26 13:20:19 superman-laptop init: tty4 main process (4456) killed by TERM signal
Oct 26 13:20:19 superman-laptop init: tty5 main process (4457) killed by TERM signal
Oct 26 13:20:19 superman-laptop init: tty2 main process (4461) killed by TERM signal
Oct 26 13:20:19 superman-laptop init: tty3 main process (4462) killed by TERM signal
Oct 26 13:20:19 superman-laptop init: tty1 main process (4463) killed by TERM signal
Oct 26 13:20:19 superman-laptop init: tty6 main process (4464) killed by TERM signal
Oct 26 13:20:19 superman-laptop avahi-daemon[5362]: Got SIGTERM, quitting.
Oct 26 13:20:19 superman-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 26 13:20:21 superman-laptop rpc.statd[4329]: Caught signal 15, un-registering and exiting.
Oct 26 13:20:23 superman-laptop mountd[5184]: Caught signal 15, un-registering and exiting.
Oct 26 16:56:26 superman-laptop NetworkManager: <info>  starting... 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.143389] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.318488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.318994] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.319463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.320594] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.321023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.321530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.322051] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.322632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.323006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.323377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.323771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.389751] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.390493] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.392459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.393652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.395070] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.395525] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.395951] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.396371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.396790] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.397232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.397689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.398138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.398583] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.399034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.399481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.399933] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.400374] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.400841] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.401316] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.401961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.402406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.402841] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.403274] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.403705] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.404151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.404584] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.405015] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.405469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.405931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.406916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.407362] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.407819] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.408734] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.409189] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.409642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.454644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.455161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.455604] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.456043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.456507] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.456964] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.457416] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.457855] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.458291] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.458729] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.459163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.459616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.460051] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.460486] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.460920] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.461375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.461813] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.462246] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0_logicaldev_input'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.462694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.463127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.463557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 26 16:56:27 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 26 16:56:27 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 16:56:27 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 16:56:27 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 26 16:56:27 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 26 16:56:27 superman-laptop NetworkManager: <debug> [1193432187.532007] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 26 16:56:28 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 16:56:28 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 16:56:28 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 26 16:56:28 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.081226] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.081965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.082569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.083205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.083811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.084426] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.085058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.093895] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.094616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.095334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.096048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.096762] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.097495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.098223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.098943] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.099664] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.100383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.101131] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_usbraw'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.101850] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.102565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.103309] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.104025] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.104755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.105487] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.106199] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.106934] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.107694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.108406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.109125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.109835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 26 16:56:28 superman-laptop NetworkManager: <debug> [1193432188.110542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: Successfully dropped root privileges.
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: avahi-daemon 0.6.20 starting up.
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: Successfully called chroot().
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: Successfully dropped remaining capabilities.
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: No service file found in /etc/avahi/services.
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: Network interface enumeration completed.
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 26 16:56:29 superman-laptop avahi-daemon[5434]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 200236090.
Oct 26 16:56:29 superman-laptop hcid[5469]: Bluetooth HCI daemon
Oct 26 16:56:29 superman-laptop hcid[5469]: Starting SDP server
Oct 26 16:56:29 superman-laptop hcid[5469]: Created local server at unix:abstract=/var/run/dbus-th55F4YvB4,guid=9698ad0e6c232bc02e64f4004722547d
Oct 26 16:56:29 superman-laptop audio[5481]: Bluetooth Audio daemon
Oct 26 16:56:29 superman-laptop audio[5481]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 26 16:56:29 superman-laptop input[5482]: Bluetooth Input daemon
Oct 26 16:56:29 superman-laptop audio[5481]: Unix socket created: 5
Oct 26 16:56:29 superman-laptop input[5482]: Registered input manager path:/org/bluez/input
Oct 26 16:56:29 superman-laptop audio[5481]: add_service_record: got record id 0x10000
Oct 26 16:56:29 superman-laptop audio[5481]: add_service_record: got record id 0x10001
Oct 26 16:56:29 superman-laptop audio[5481]: Registered manager path:/org/bluez/audio
Oct 26 16:56:29 superman-laptop ntpd[5535]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 26 16:56:29 superman-laptop ntpd[5541]: precision = 1.000 usec
Oct 26 16:56:29 superman-laptop ntpd[5541]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 26 16:56:29 superman-laptop ntpd[5541]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 26 16:56:29 superman-laptop ntpd[5541]: Listening on interface #2 lo, ::1#123 Enabled
Oct 26 16:56:29 superman-laptop ntpd[5541]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 26 16:56:29 superman-laptop ntpd[5541]: kernel time sync status 0040
Oct 26 16:56:29 superman-laptop ntpd[5541]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 26 16:56:30 superman-laptop NetworkManager: <debug> [1193432190.013190] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: host name not found: ntp.ubuntu.com
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: host name not found: clock.tricity.wsu.edu
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: host name not found: wuarchive.wustl.edu
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: host name not found: gilbreth.ecn.purdue.edu
Oct 26 16:56:31 superman-laptop ntpd_initres[5610]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 26 16:56:48 superman-laptop hcid[5469]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 26 16:56:48 superman-laptop hcid[5469]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 26 16:56:52 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 26 16:57:08 superman-laptop NetworkManager: <debug> [1193432228.921238] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5150_SNDK1405050D2AA08006'). 
Oct 26 16:57:08 superman-laptop NetworkManager: <debug> [1193432228.989600] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5150_SNDK1405050D2AA08006_if0'). 
Oct 26 16:57:09 superman-laptop NetworkManager: <debug> [1193432229.005336] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5150_SNDK1405050D2AA08006_usbraw'). 
Oct 26 16:57:14 superman-laptop NetworkManager: <debug> [1193432234.153611] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5150_SNDK1405050D2AA08006_if0_scsi_host'). 
Oct 26 16:57:14 superman-laptop NetworkManager: <debug> [1193432234.157247] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5150_SNDK1405050D2AA08006_if0_scsi_host_scsi_device_lun0'). 
Oct 26 16:57:14 superman-laptop NetworkManager: <debug> [1193432234.167943] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5150_SNDK1405050D2AA08006_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 26 16:57:14 superman-laptop NetworkManager: <debug> [1193432234.221298] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SanDisk_Corporation_Geek_Squad_SNDK1405050D2AA08006_0_0'). 
Oct 26 16:57:14 superman-laptop NetworkManager: <debug> [1193432234.256289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B07A_91FB'). 
Oct 26 16:57:14 superman-laptop hald: mounted /dev/sdb1 on behalf of uid 1000
Oct 26 16:57:27 superman-laptop NetworkManager: <debug> [1193432247.594048] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_usbraw'). 
Oct 26 16:57:27 superman-laptop NetworkManager: <debug> [1193432247.596305] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0'). 
Oct 26 16:57:27 superman-laptop NetworkManager: <debug> [1193432247.598735] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0_logicaldev_input'). 
Oct 26 16:57:27 superman-laptop NetworkManager: <debug> [1193432247.602273] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial'). 
Oct 26 17:04:48 superman-laptop init: tty4 main process (4486) killed by TERM signal
Oct 26 17:04:48 superman-laptop init: tty5 main process (4487) killed by TERM signal
Oct 26 17:04:48 superman-laptop init: tty2 main process (4489) killed by TERM signal
Oct 26 17:04:48 superman-laptop init: tty3 main process (4491) killed by TERM signal
Oct 26 17:04:48 superman-laptop init: tty6 main process (4494) killed by TERM signal
Oct 26 17:04:48 superman-laptop init: tty1 main process (4493) killed by TERM signal
Oct 26 17:04:49 superman-laptop hald: unmounted /dev/sdb1 from '/media/NEW VOLUME' on behalf of uid 1000
Oct 26 17:04:49 superman-laptop avahi-daemon[5434]: Got SIGTERM, quitting.
Oct 26 17:04:51 superman-laptop rpc.statd[4359]: Caught signal 15, un-registering and exiting.
Oct 26 17:04:53 superman-laptop mountd[5245]: Caught signal 15, un-registering and exiting.
Oct 26 17:19:07 superman-laptop NetworkManager: <info>  starting... 
Oct 26 17:19:07 superman-laptop NetworkManager: <debug> [1193433547.933334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.194656] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.195289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.195737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.196829] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.197266] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.197688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.198205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.198648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.264143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.264676] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.265539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.266015] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.266674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.268015] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.269014] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.269782] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.271407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.272115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.272839] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.273303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.273719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.315115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.315648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.316096] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.316532] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.317025] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.317587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.318052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.318601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.319059] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.319528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.319957] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.320380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.320850] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.321310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.321747] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.322232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.322708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.325102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.325621] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.326084] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.326521] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.326945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.327365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.327786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.328206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.328626] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.329045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.329464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.329883] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.330359] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.330786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.331214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.331712] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.332270] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.332725] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.333210] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.333632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.334069] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.334503] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.334914] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.335321] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.335743] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.336149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.406290] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 26 17:19:08 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.865718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.866192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.866561] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.866922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.867281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.867665] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.868024] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.868383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.868739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.869096] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.869468] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.869825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.870191] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.870567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.870925] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.871282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.871639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.871994] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.872349] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.872704] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.873059] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.873415] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.873776] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.874179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.874542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.874927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.875307] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.875659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.876017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 26 17:19:08 superman-laptop NetworkManager: <debug> [1193433548.876363] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: Successfully dropped root privileges.
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: avahi-daemon 0.6.20 starting up.
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: Successfully called chroot().
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: Successfully dropped remaining capabilities.
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: No service file found in /etc/avahi/services.
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: Network interface enumeration completed.
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 26 17:19:09 superman-laptop avahi-daemon[5353]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 1368541973.
Oct 26 17:19:09 superman-laptop hcid[5388]: Bluetooth HCI daemon
Oct 26 17:19:10 superman-laptop hcid[5388]: Starting SDP server
Oct 26 17:19:10 superman-laptop hcid[5388]: Created local server at unix:abstract=/var/run/dbus-eZinR8xMWX,guid=f23e3a68081f5a69dfd97500472259ce
Oct 26 17:19:10 superman-laptop audio[5400]: Bluetooth Audio daemon
Oct 26 17:19:10 superman-laptop audio[5400]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 26 17:19:10 superman-laptop audio[5400]: Unix socket created: 5
Oct 26 17:19:10 superman-laptop input[5401]: Bluetooth Input daemon
Oct 26 17:19:10 superman-laptop input[5401]: Registered input manager path:/org/bluez/input
Oct 26 17:19:10 superman-laptop audio[5400]: add_service_record: got record id 0x10000
Oct 26 17:19:10 superman-laptop audio[5400]: add_service_record: got record id 0x10001
Oct 26 17:19:10 superman-laptop audio[5400]: Registered manager path:/org/bluez/audio
Oct 26 17:19:12 superman-laptop ntpd[5471]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 26 17:19:12 superman-laptop ntpd[5472]: precision = 1.000 usec
Oct 26 17:19:12 superman-laptop ntpd[5472]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 26 17:19:12 superman-laptop ntpd[5472]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 26 17:19:12 superman-laptop ntpd[5472]: Listening on interface #2 lo, ::1#123 Enabled
Oct 26 17:19:12 superman-laptop ntpd[5472]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 26 17:19:12 superman-laptop ntpd[5472]: kernel time sync status 0040
Oct 26 17:19:12 superman-laptop ntpd[5472]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: host name not found: ntp.ubuntu.com
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: host name not found: clock.tricity.wsu.edu
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: host name not found: wuarchive.wustl.edu
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: host name not found: gilbreth.ecn.purdue.edu
Oct 26 17:19:14 superman-laptop ntpd_initres[5500]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 26 17:19:27 superman-laptop init: tty4 main process (4441) killed by TERM signal
Oct 26 17:19:27 superman-laptop init: tty5 main process (4442) killed by TERM signal
Oct 26 17:19:27 superman-laptop init: tty2 main process (4444) killed by TERM signal
Oct 26 17:19:27 superman-laptop init: tty3 main process (4446) killed by TERM signal
Oct 26 17:19:27 superman-laptop init: tty1 main process (4448) killed by TERM signal
Oct 26 17:19:27 superman-laptop init: tty6 main process (4449) killed by TERM signal
Oct 26 17:19:27 superman-laptop avahi-daemon[5353]: Got SIGTERM, quitting.
Oct 26 17:19:28 superman-laptop gdm[5789]: CRITICAL: gdm_connection_close: assertion `conn != NULL' failed 
Oct 26 17:19:28 superman-laptop last message repeated 2 times
Oct 26 17:19:29 superman-laptop gdm[5789]: WARNING: gdm_slave_send: Can't open fifo! 
Oct 26 17:19:29 superman-laptop last message repeated 4 times
Oct 26 17:19:30 superman-laptop rpc.statd[4314]: Caught signal 15, un-registering and exiting.
Oct 26 17:19:32 superman-laptop mountd[5181]: Caught signal 15, un-registering and exiting.
Oct 27 09:44:42 superman-laptop NetworkManager: <info>  starting... 
Oct 27 09:44:42 superman-laptop NetworkManager: <debug> [1193492682.702479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.015320] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.016125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.016696] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.017324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.018223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.018696] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.019209] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.078234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.079310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.080826] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.081735] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.083042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.083509] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.084497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.084967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.085400] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.085854] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.086284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.086713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.087170] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.087638] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.088121] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.130919] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.131435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.131882] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.132323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.132772] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.133213] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.133656] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.134092] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.135184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.135804] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.136325] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.136880] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.137323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.137749] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.138203] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.138671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.140811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.141278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.141717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.142195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.142752] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.143239] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.143703] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.144133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.144560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.145015] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.145453] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.145896] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.146329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.146761] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.147199] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.147630] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.148057] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.148483] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.148926] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.149368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.149810] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.150252] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.150694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.151162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.151605] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.152044] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.152486] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.221371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 27 09:44:43 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.751240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.751771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.752194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.752607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.753035] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.753405] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.753770] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.754135] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.754500] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.754864] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.755229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.755595] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.756003] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.756373] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.756752] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.757134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.757496] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.757859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.758221] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.758583] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.758945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.759308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.759669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.760031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.760409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.760778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.765713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.766162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 27 09:44:43 superman-laptop NetworkManager: <debug> [1193492683.766602] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: Successfully dropped root privileges.
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: avahi-daemon 0.6.20 starting up.
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: Successfully called chroot().
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: Successfully dropped remaining capabilities.
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: No service file found in /etc/avahi/services.
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: Network interface enumeration completed.
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 27 09:44:44 superman-laptop avahi-daemon[5342]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 412257463.
Oct 27 09:44:44 superman-laptop hcid[5378]: Bluetooth HCI daemon
Oct 27 09:44:44 superman-laptop hcid[5378]: Starting SDP server
Oct 27 09:44:44 superman-laptop hcid[5378]: Created local server at unix:abstract=/var/run/dbus-VnhF1OkfJJ,guid=ec7c058527f83279afcdbf00472340cc
Oct 27 09:44:44 superman-laptop input[5391]: Bluetooth Input daemon
Oct 27 09:44:44 superman-laptop input[5391]: Registered input manager path:/org/bluez/input
Oct 27 09:44:44 superman-laptop audio[5390]: Bluetooth Audio daemon
Oct 27 09:44:44 superman-laptop audio[5390]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 27 09:44:44 superman-laptop audio[5390]: Unix socket created: 5
Oct 27 09:44:44 superman-laptop audio[5390]: add_service_record: got record id 0x10000
Oct 27 09:44:44 superman-laptop audio[5390]: add_service_record: got record id 0x10001
Oct 27 09:44:44 superman-laptop audio[5390]: Registered manager path:/org/bluez/audio
Oct 27 09:44:45 superman-laptop NetworkManager: <debug> [1193492685.709046] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 27 09:44:47 superman-laptop ntpd[5461]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 27 09:44:47 superman-laptop ntpd[5462]: precision = 1.000 usec
Oct 27 09:44:47 superman-laptop ntpd[5462]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 27 09:44:47 superman-laptop ntpd[5462]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 27 09:44:47 superman-laptop ntpd[5462]: Listening on interface #2 lo, ::1#123 Enabled
Oct 27 09:44:47 superman-laptop ntpd[5462]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 27 09:44:47 superman-laptop ntpd[5462]: kernel time sync status 0040
Oct 27 09:44:47 superman-laptop ntpd[5462]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: host name not found: ntp.ubuntu.com
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: host name not found: clock.tricity.wsu.edu
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: host name not found: wuarchive.wustl.edu
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: host name not found: gilbreth.ecn.purdue.edu
Oct 27 09:44:49 superman-laptop ntpd_initres[5504]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 27 09:45:09 superman-laptop hcid[5378]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 27 09:45:09 superman-laptop hcid[5378]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 27 09:45:22 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Bowman'. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, but NO valid key exists.  New key needed. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Bowman'. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Bowman' received. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 27 09:45:53 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, and a key exists.  No new key needed. 
Oct 27 09:45:54 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 27 09:45:54 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 27 09:45:54 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426f776d616e' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Bowman'. 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 27 09:45:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 27 09:45:56 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 27 09:45:56 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 27 09:45:56 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 27 09:45:57 superman-laptop avahi-daemon[5342]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 27 09:45:57 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 27 09:45:58 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 27 09:45:58 superman-laptop dhclient: DHCPOFFER from 192.168.0.7
Oct 27 09:45:58 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 27 09:45:58 superman-laptop dhclient: DHCPACK from 192.168.0.7
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: New relevant interface eth1.IPv4 for mDNS.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 27 09:45:58 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 27 09:45:58 superman-laptop dhclient: bound to 192.168.0.87 -- renewal in 280793 seconds.
Oct 27 09:45:58 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>    address 192.168.0.87 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>    broadcast 192.168.0.255 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>    gateway 192.168.0.1 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>    nameserver 192.168.0.7 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>    domain name 'bei.image' 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 27 09:45:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Withdrawing address record for 192.168.0.87 on eth1.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: New relevant interface eth1.IPv4 for mDNS.
Oct 27 09:45:58 superman-laptop avahi-daemon[5342]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 27 09:45:59 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 27 09:45:59 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 27 09:45:59 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 27 09:45:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 27 09:45:59 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 27 09:45:59 superman-laptop ntpdate[6007]: can't find host clock.tricity.wsu.edu 
Oct 27 09:45:59 superman-laptop ntpdate[6007]: the NTP socket is in use, exiting
Oct 27 09:46:00 superman-laptop avahi-daemon[5342]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 27 09:49:48 superman-laptop ntpd[5462]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 27 09:49:48 superman-laptop ntpd[5462]: Listening on interface #5 eth1, 192.168.0.87#123 Enabled
Oct 27 09:51:28 superman-laptop init: tty4 main process (4430) killed by TERM signal
Oct 27 09:51:28 superman-laptop init: tty5 main process (4431) killed by TERM signal
Oct 27 09:51:28 superman-laptop init: tty2 main process (4433) killed by TERM signal
Oct 27 09:51:28 superman-laptop init: tty3 main process (4435) killed by TERM signal
Oct 27 09:51:28 superman-laptop init: tty1 main process (4437) killed by TERM signal
Oct 27 09:51:28 superman-laptop init: tty6 main process (4438) killed by TERM signal
Oct 27 09:51:28 superman-laptop avahi-daemon[5342]: Got SIGTERM, quitting.
Oct 27 09:51:28 superman-laptop avahi-daemon[5342]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 27 09:51:30 superman-laptop rpc.statd[4303]: Caught signal 15, un-registering and exiting.
Oct 27 09:51:32 superman-laptop mountd[5155]: Caught signal 15, un-registering and exiting.
Oct 27 18:06:43 superman-laptop NetworkManager: <info>  starting... 
Oct 27 18:06:43 superman-laptop NetworkManager: <debug> [1193522803.730908] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.010952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.011621] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.012037] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.012483] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.081953] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.083012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.084234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.086116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.087474] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.088126] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.089100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.089559] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.090005] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.090440] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.090873] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.091304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.091737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.092168] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.093035] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.093510] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.139810] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.140316] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.140775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.141258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.141820] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.142288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.142811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.143308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.145460] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.145902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.146339] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.146809] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.147364] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.147822] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.148279] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.148717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.149142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.149565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.149988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.150410] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.150833] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.151271] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.151707] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.152130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.152558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.152979] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.153399] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.153819] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.154240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.154659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.155091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.155512] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.155932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.156350] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.156793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.157212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.157632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.158050] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.158468] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.158885] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.159302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.159718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0_logicaldev_input'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.160136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.160573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.161005] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.161421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.229250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 27 18:06:44 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.724342] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.725073] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.725465] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.725845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.726217] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.726588] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.726962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.727334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.727711] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.728086] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.728460] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.736961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.737453] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.737850] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.738223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.738596] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.738966] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.739335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.739704] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_usbraw'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.740071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.740442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.740825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.741268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.741705] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.742147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.742592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.743021] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.743469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.743902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.744327] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.744764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 27 18:06:44 superman-laptop NetworkManager: <debug> [1193522804.745194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: Successfully dropped root privileges.
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: avahi-daemon 0.6.20 starting up.
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: Successfully called chroot().
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: Successfully dropped remaining capabilities.
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: No service file found in /etc/avahi/services.
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: Network interface enumeration completed.
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 27 18:06:45 superman-laptop avahi-daemon[5416]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 943458308.
Oct 27 18:06:45 superman-laptop hcid[5451]: Bluetooth HCI daemon
Oct 27 18:06:45 superman-laptop hcid[5451]: Starting SDP server
Oct 27 18:06:45 superman-laptop hcid[5451]: Created local server at unix:abstract=/var/run/dbus-CBcwWK56IW,guid=32286e8c0c95b25dced11d004723b675
Oct 27 18:06:45 superman-laptop audio[5463]: Bluetooth Audio daemon
Oct 27 18:06:45 superman-laptop audio[5463]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 27 18:06:45 superman-laptop audio[5463]: Unix socket created: 5
Oct 27 18:06:45 superman-laptop input[5464]: Bluetooth Input daemon
Oct 27 18:06:45 superman-laptop input[5464]: Registered input manager path:/org/bluez/input
Oct 27 18:06:45 superman-laptop audio[5463]: add_service_record: got record id 0x10000
Oct 27 18:06:45 superman-laptop audio[5463]: add_service_record: got record id 0x10001
Oct 27 18:06:45 superman-laptop audio[5463]: Registered manager path:/org/bluez/audio
Oct 27 18:06:46 superman-laptop NetworkManager: <debug> [1193522806.716998] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 27 18:06:48 superman-laptop ntpd[5534]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 27 18:06:48 superman-laptop ntpd[5535]: precision = 1.000 usec
Oct 27 18:06:48 superman-laptop ntpd[5535]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 27 18:06:48 superman-laptop ntpd[5535]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 27 18:06:48 superman-laptop ntpd[5535]: Listening on interface #2 lo, ::1#123 Enabled
Oct 27 18:06:48 superman-laptop ntpd[5535]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 27 18:06:48 superman-laptop ntpd[5535]: kernel time sync status 0040
Oct 27 18:06:48 superman-laptop ntpd[5535]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: host name not found: ntp.ubuntu.com
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: host name not found: clock.tricity.wsu.edu
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: host name not found: wuarchive.wustl.edu
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: host name not found: gilbreth.ecn.purdue.edu
Oct 27 18:06:50 superman-laptop ntpd_initres[5591]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 27 18:07:28 superman-laptop hcid[5451]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 27 18:07:28 superman-laptop hcid[5451]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 27 18:07:35 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 27 18:52:10 superman-laptop init: tty4 main process (4503) killed by TERM signal
Oct 27 18:52:10 superman-laptop init: tty5 main process (4504) killed by TERM signal
Oct 27 18:52:10 superman-laptop init: tty2 main process (4508) killed by TERM signal
Oct 27 18:52:10 superman-laptop init: tty3 main process (4509) killed by TERM signal
Oct 27 18:52:10 superman-laptop init: tty1 main process (4510) killed by TERM signal
Oct 27 18:52:10 superman-laptop init: tty6 main process (4511) killed by TERM signal
Oct 27 18:52:10 superman-laptop avahi-daemon[5416]: Got SIGTERM, quitting.
Oct 27 18:52:12 superman-laptop rpc.statd[4376]: Caught signal 15, un-registering and exiting.
Oct 27 18:52:14 superman-laptop mountd[5230]: Caught signal 15, un-registering and exiting.
Oct 28 10:18:13 superman-laptop NetworkManager: <info>  starting... 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.713078] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.969458] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.970177] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.970775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.971377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.971747] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.972127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 28 10:18:13 superman-laptop NetworkManager: <debug> [1193581093.972546] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.033726] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.034596] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.035756] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.036537] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.036958] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.038006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.038385] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.038760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.039147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.040028] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.040403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.040771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.041155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.083992] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.084764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.086689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.087185] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.087586] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.088031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.088428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.090459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.090834] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.091203] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.091571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.091989] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.092464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.092842] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.093261] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.093624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.093986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.094347] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.094706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.095064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.095422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.095782] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.096159] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.096518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.096879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.097244] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.097608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.097974] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.098337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.098699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.099064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.099430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.099787] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.100159] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.100520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.100885] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.101251] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.101615] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.101981] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.102344] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.102708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.103069] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.103432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.103792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.174275] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 28 10:18:14 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.760262] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.760987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.761576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.762147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.762714] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.763290] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.763888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.772242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.772916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.773578] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.774240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.774899] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.775585] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.776268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.776927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.777645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.778405] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.779131] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.779847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.780616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.781334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.782146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.782868] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.783607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.784346] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.785093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.785848] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.786556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.787253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 28 10:18:14 superman-laptop NetworkManager: <debug> [1193581094.787972] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: Successfully dropped root privileges.
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: avahi-daemon 0.6.20 starting up.
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: Successfully called chroot().
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: Successfully dropped remaining capabilities.
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: No service file found in /etc/avahi/services.
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: Network interface enumeration completed.
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 28 10:18:15 superman-laptop avahi-daemon[5358]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 313062112.
Oct 28 10:18:15 superman-laptop hcid[5394]: Bluetooth HCI daemon
Oct 28 10:18:15 superman-laptop hcid[5394]: Starting SDP server
Oct 28 10:18:15 superman-laptop hcid[5394]: Created local server at unix:abstract=/var/run/dbus-TaiJ6GrqYD,guid=b3284e7b48047c319c1bf20047249a27
Oct 28 10:18:16 superman-laptop audio[5406]: Bluetooth Audio daemon
Oct 28 10:18:16 superman-laptop audio[5406]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 28 10:18:16 superman-laptop audio[5406]: Unix socket created: 5
Oct 28 10:18:16 superman-laptop input[5407]: Bluetooth Input daemon
Oct 28 10:18:16 superman-laptop input[5407]: Registered input manager path:/org/bluez/input
Oct 28 10:18:16 superman-laptop audio[5406]: add_service_record: got record id 0x10000
Oct 28 10:18:16 superman-laptop audio[5406]: add_service_record: got record id 0x10001
Oct 28 10:18:16 superman-laptop audio[5406]: Registered manager path:/org/bluez/audio
Oct 28 10:18:16 superman-laptop NetworkManager: <debug> [1193581096.715505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 28 10:18:18 superman-laptop ntpd[5477]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 28 10:18:18 superman-laptop ntpd[5478]: precision = 1.000 usec
Oct 28 10:18:18 superman-laptop ntpd[5478]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 28 10:18:18 superman-laptop ntpd[5478]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 28 10:18:18 superman-laptop ntpd[5478]: Listening on interface #2 lo, ::1#123 Enabled
Oct 28 10:18:18 superman-laptop ntpd[5478]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 28 10:18:18 superman-laptop ntpd[5478]: kernel time sync status 0040
Oct 28 10:18:18 superman-laptop ntpd[5478]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: host name not found: ntp.ubuntu.com
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: host name not found: clock.tricity.wsu.edu
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: host name not found: wuarchive.wustl.edu
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: host name not found: gilbreth.ecn.purdue.edu
Oct 28 10:18:20 superman-laptop ntpd_initres[5547]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 28 10:19:11 superman-laptop hcid[5394]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 28 10:19:11 superman-laptop hcid[5394]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Bowman'. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, but NO valid key exists.  New key needed. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Bowman'. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Bowman' received. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 10:19:20 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, and a key exists.  No new key needed. 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426f776d616e' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 10:19:22 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Bowman'. 
Oct 28 10:19:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 28 10:19:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 28 10:19:23 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 28 10:19:23 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 28 10:19:23 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 28 10:19:24 superman-laptop avahi-daemon[5358]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 10:19:24 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 28 10:19:26 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 28 10:19:27 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 28 10:19:31 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 28 10:19:41 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Oct 28 10:19:45 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 28 10:19:50 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Oct 28 10:19:54 superman-laptop NetworkManager: <debug> [1193581194.798388] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Bowman' 
Oct 28 10:19:54 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Bowman 
Oct 28 10:19:54 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 28 10:19:54 superman-laptop NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 28 10:19:54 superman-laptop NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 28 10:19:54 superman-laptop NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 28 10:19:54 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5899
Oct 28 10:19:54 superman-laptop dhclient: killed old client process, removed PID file
Oct 28 10:19:54 superman-laptop dhclient: DHCPRELEASE on eth1 to 192.168.0.7 port 67
Oct 28 10:19:54 superman-laptop dhclient: send_packet: Network is unreachable
Oct 28 10:19:54 superman-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:55 superman-laptop avahi-daemon[5358]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, but NO valid key exists.  New key needed. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Bowman'. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Bowman' received. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 10:19:55 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, and a key exists.  No new key needed. 
Oct 28 10:19:56 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 28 10:19:56 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant6^I' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426f776d616e' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 10:19:57 superman-laptop NetworkManager: <debug> [1193581197.982660] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Bowman' 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Bowman 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 28 10:19:57 superman-laptop NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, but NO valid key exists.  New key needed. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Bowman'. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Bowman' received. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 10:19:58 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, and a key exists.  No new key needed. 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant9^I' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426f776d616e' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:19:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 10:20:00 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Bowman'. 
Oct 28 10:20:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 28 10:20:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 28 10:20:01 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 28 10:20:01 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Oct 28 10:20:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 28 10:20:01 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 28 10:20:01 superman-laptop avahi-daemon[5358]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 10:20:02 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 28 10:20:02 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct 28 10:20:02 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 28 10:20:10 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Oct 28 10:20:19 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Oct 28 10:20:33 superman-laptop dhclient: No DHCPOFFERS received.
Oct 28 10:20:33 superman-laptop dhclient: Trying recorded lease 192.168.2.4
Oct 28 10:20:33 superman-laptop avahi-daemon[5358]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Oct 28 10:20:33 superman-laptop avahi-daemon[5358]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 10:20:33 superman-laptop avahi-daemon[5358]: Registering new address record for 192.168.2.4 on eth1.IPv4.
Oct 28 10:20:36 superman-laptop avahi-daemon[5358]: Withdrawing address record for 192.168.2.4 on eth1.
Oct 28 10:20:36 superman-laptop avahi-daemon[5358]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Oct 28 10:20:36 superman-laptop avahi-daemon[5358]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 10:20:36 superman-laptop avahi-autoipd(eth1)[6077]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 28 10:20:36 superman-laptop avahi-autoipd(eth1)[6077]: Successfully called chroot().
Oct 28 10:20:36 superman-laptop avahi-autoipd(eth1)[6077]: Successfully dropped root privileges.
Oct 28 10:20:36 superman-laptop avahi-autoipd(eth1)[6077]: Starting with address 169.254.3.94
Oct 28 10:20:42 superman-laptop avahi-autoipd(eth1)[6077]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 28 10:20:42 superman-laptop avahi-daemon[5358]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 28 10:20:42 superman-laptop avahi-daemon[5358]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 10:20:42 superman-laptop avahi-daemon[5358]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 28 10:20:46 superman-laptop avahi-autoipd(eth1)[6077]: Successfully claimed IP address 169.254.3.94
Oct 28 10:20:46 superman-laptop dhclient: Trying recorded lease 192.168.2.3
Oct 28 10:20:46 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Oct 28 10:20:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Oct 28 10:20:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Oct 28 10:20:46 superman-laptop NetworkManager: <debug> [1193581246.364728] real_act_stage4_ip_config_timeout(): Activation (eth1/wireless): could not get IP configuration info for 'Bowman', asking for new key. 
Oct 28 10:20:46 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Bowman'. 
Oct 28 10:20:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Oct 28 10:20:46 superman-laptop avahi-autoipd(eth1)[6077]: A routable address has been configured.
Oct 28 10:20:46 superman-laptop avahi-autoipd(eth1)[6077]: Callout UNBIND, address 169.254.3.94 on interface eth1
Oct 28 10:20:46 superman-laptop avahi-daemon[5358]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 28 10:20:46 superman-laptop avahi-daemon[5358]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 28 10:20:46 superman-laptop avahi-daemon[5358]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 28 10:20:46 superman-laptop avahi-daemon[5358]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 28 10:20:49 superman-laptop avahi-autoipd(eth1)[6077]: No longer a routable address configured, restarting probe process.
Oct 28 10:20:49 superman-laptop avahi-daemon[5358]: Withdrawing address record for 192.168.2.3 on eth1.
Oct 28 10:20:49 superman-laptop avahi-daemon[5358]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 28 10:20:49 superman-laptop avahi-daemon[5358]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 10:20:49 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Oct 28 10:20:49 superman-laptop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Oct 28 10:20:49 superman-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Oct 28 10:20:55 superman-laptop avahi-autoipd(eth1)[6077]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 28 10:20:55 superman-laptop avahi-daemon[5358]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 28 10:20:55 superman-laptop avahi-daemon[5358]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 10:20:55 superman-laptop avahi-daemon[5358]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 28 10:20:59 superman-laptop avahi-autoipd(eth1)[6077]: Successfully claimed IP address 169.254.3.94
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Bowman' received. 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:31 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, and a key exists.  No new key needed. 
Oct 28 10:21:32 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 28 10:21:32 superman-laptop avahi-daemon[5358]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 10:21:32 superman-laptop avahi-daemon[5358]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 28 10:21:32 superman-laptop avahi-autoipd(eth1)[6077]: SIOCSIFFLAGS failed: Permission denied
Oct 28 10:21:32 superman-laptop avahi-autoipd(eth1)[6077]: Callout STOP, address 169.254.3.94 on interface eth1
Oct 28 10:21:32 superman-laptop avahi-daemon[5358]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 28 10:21:32 superman-laptop avahi-daemon[5358]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 28 10:21:32 superman-laptop avahi-autoipd(eth1)[6078]: client: RTNETLINK answers: No such process
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426f776d616e' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 10:21:33 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 10:21:34 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Bowman'. 
Oct 28 10:21:34 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 28 10:21:34 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 28 10:21:35 superman-laptop avahi-daemon[5358]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 10:21:35 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 28 10:21:35 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 28 10:21:35 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 28 10:21:36 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 28 10:21:38 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Oct 28 10:21:38 superman-laptop dhclient: DHCPOFFER from 192.168.0.7
Oct 28 10:21:38 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 28 10:21:38 superman-laptop dhclient: DHCPACK from 192.168.0.7
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 28 10:21:38 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 28 10:21:38 superman-laptop dhclient: bound to 192.168.0.87 -- renewal in 324685 seconds.
Oct 28 10:21:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>    address 192.168.0.87 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>    broadcast 192.168.0.255 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>    gateway 192.168.0.1 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>    nameserver 192.168.0.7 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>    domain name 'bei.image' 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 28 10:21:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Withdrawing address record for 192.168.0.87 on eth1.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 10:21:38 superman-laptop avahi-daemon[5358]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 28 10:21:39 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 28 10:21:39 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 28 10:21:39 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 28 10:21:39 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 28 10:21:39 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 28 10:21:39 superman-laptop NetworkManager: <debug> [1193581299.247087] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Bowman' 
Oct 28 10:21:39 superman-laptop ntpdate[6189]: can't find host clock.tricity.wsu.edu 
Oct 28 10:21:39 superman-laptop ntpdate[6189]: the NTP socket is in use, exiting
Oct 28 10:21:40 superman-laptop avahi-daemon[5358]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 10:23:19 superman-laptop ntpd[5478]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 28 10:23:19 superman-laptop ntpd[5478]: Listening on interface #5 eth1, 192.168.0.87#123 Enabled
Oct 28 11:25:26 superman-laptop NetworkManager: <debug> [1193585126.518231] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 28 11:25:50 superman-laptop NetworkManager: <debug> [1193585150.443267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_empty_cd_r'). 
Oct 28 11:31:08 superman-laptop NetworkManager: <debug> [1193585468.122394] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_empty_cd_r'). 
Oct 28 12:08:07 superman-laptop init: tty4 main process (4445) killed by TERM signal
Oct 28 12:08:07 superman-laptop init: tty5 main process (4446) killed by TERM signal
Oct 28 12:08:07 superman-laptop init: tty2 main process (4448) killed by TERM signal
Oct 28 12:08:07 superman-laptop init: tty3 main process (4450) killed by TERM signal
Oct 28 12:08:07 superman-laptop init: tty1 main process (4452) killed by TERM signal
Oct 28 12:08:07 superman-laptop init: tty6 main process (4453) killed by TERM signal
Oct 28 12:08:08 superman-laptop avahi-daemon[5358]: Got SIGTERM, quitting.
Oct 28 12:08:08 superman-laptop avahi-daemon[5358]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 12:08:11 superman-laptop rpc.statd[4318]: Caught signal 15, un-registering and exiting.
Oct 28 12:08:13 superman-laptop mountd[5171]: Caught signal 15, un-registering and exiting.
Oct 28 12:46:16 superman-laptop NetworkManager: <info>  starting... 
Oct 28 12:46:16 superman-laptop NetworkManager: <debug> [1193589976.783134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.059648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.060328] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.060800] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.061229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.122941] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.123529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.124205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.124633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.125047] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.125482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.126045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.127553] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.128071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.129377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.129835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.130278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.130718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.131152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.132300] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.134184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.134665] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.135106] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.135567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.135996] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.136428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.136871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.137300] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.137772] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.180099] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.180589] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.181016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.181463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.181903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.182334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.182776] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.183198] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.183619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.184039] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.184460] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.184880] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.185301] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.185730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.186148] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.186566] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.186983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.187413] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.187830] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.188246] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.188662] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.189077] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.189521] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.189952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.190428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.190971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.191406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.191930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.192387] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.194574] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.195041] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.195477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.195908] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.196339] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.196768] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.197196] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.265174] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 28 12:46:17 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.874481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.875426] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.876119] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.876783] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.877463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.878123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.878785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.879448] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.880110] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.880770] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.889502] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.890247] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.890831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.891422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.892035] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.892677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.893354] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.893967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.894562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.895153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.895746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.896337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.896930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.897515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.898109] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.898697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.899334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.899900] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.900466] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 28 12:46:17 superman-laptop NetworkManager: <debug> [1193589977.901029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: Successfully dropped root privileges.
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: avahi-daemon 0.6.20 starting up.
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: Successfully called chroot().
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: Successfully dropped remaining capabilities.
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: No service file found in /etc/avahi/services.
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: Network interface enumeration completed.
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 28 12:46:18 superman-laptop avahi-daemon[5302]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 675047296.
Oct 28 12:46:18 superman-laptop hcid[5337]: Bluetooth HCI daemon
Oct 28 12:46:18 superman-laptop hcid[5337]: Starting SDP server
Oct 28 12:46:18 superman-laptop hcid[5337]: Created local server at unix:abstract=/var/run/dbus-qli3r1n5aM,guid=54195f97b6073b2db0b651004724bcda
Oct 28 12:46:19 superman-laptop audio[5349]: Bluetooth Audio daemon
Oct 28 12:46:19 superman-laptop audio[5349]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 28 12:46:19 superman-laptop audio[5349]: Unix socket created: 5
Oct 28 12:46:19 superman-laptop input[5350]: Bluetooth Input daemon
Oct 28 12:46:19 superman-laptop input[5350]: Registered input manager path:/org/bluez/input
Oct 28 12:46:19 superman-laptop audio[5349]: add_service_record: got record id 0x10000
Oct 28 12:46:19 superman-laptop audio[5349]: add_service_record: got record id 0x10001
Oct 28 12:46:19 superman-laptop audio[5349]: Registered manager path:/org/bluez/audio
Oct 28 12:46:21 superman-laptop ntpd[5420]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 28 12:46:21 superman-laptop ntpd[5421]: precision = 1.000 usec
Oct 28 12:46:21 superman-laptop ntpd[5421]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 28 12:46:21 superman-laptop ntpd[5421]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 28 12:46:21 superman-laptop ntpd[5421]: Listening on interface #2 lo, ::1#123 Enabled
Oct 28 12:46:21 superman-laptop ntpd[5421]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 28 12:46:21 superman-laptop ntpd[5421]: kernel time sync status 0040
Oct 28 12:46:21 superman-laptop ntpd[5421]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: host name not found: ntp.ubuntu.com
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: host name not found: clock.tricity.wsu.edu
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: host name not found: wuarchive.wustl.edu
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: host name not found: gilbreth.ecn.purdue.edu
Oct 28 12:46:23 superman-laptop ntpd_initres[5463]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 28 12:46:38 superman-laptop hcid[5337]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Oct 28 12:46:38 superman-laptop hcid[5337]: Default authorization agent (:1.17, /org/bluez/auth) registered
Oct 28 12:46:43 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Bowman'. 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, but NO valid key exists.  New key needed. 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Bowman'. 
Oct 28 12:46:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 12:46:46 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Bowman' received. 
Oct 28 12:46:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 12:46:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 12:46:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 12:46:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 12:46:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 12:46:46 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, and a key exists.  No new key needed. 
Oct 28 12:46:47 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 28 12:46:47 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 28 12:46:47 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426f776d616e' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 12:46:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 12:46:49 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Bowman'. 
Oct 28 12:46:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 28 12:46:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 28 12:46:50 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 28 12:46:50 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 28 12:46:50 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 28 12:46:51 superman-laptop avahi-daemon[5302]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 12:46:53 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 28 12:46:54 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 28 12:46:57 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 28 12:46:57 superman-laptop dhclient: DHCPACK from 192.168.0.7
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 28 12:46:57 superman-laptop dhclient: bound to 192.168.0.87 -- renewal in 342292 seconds.
Oct 28 12:46:57 superman-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>    address 192.168.0.87 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>    broadcast 192.168.0.255 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>    gateway 192.168.0.1 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>    nameserver 192.168.0.7 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>    domain name 'bei.image' 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 28 12:46:57 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Withdrawing address record for 192.168.0.87 on eth1.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 12:46:57 superman-laptop avahi-daemon[5302]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 28 12:46:58 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 28 12:46:58 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 28 12:46:58 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 28 12:46:58 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 28 12:46:58 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 28 12:46:58 superman-laptop ntpdate[5933]: can't find host clock.tricity.wsu.edu 
Oct 28 12:46:58 superman-laptop ntpdate[5933]: the NTP socket is in use, exiting
Oct 28 12:47:00 superman-laptop avahi-daemon[5302]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 12:51:22 superman-laptop ntpd[5421]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 28 12:51:22 superman-laptop ntpd[5421]: Listening on interface #5 eth1, 192.168.0.87#123 Enabled
Oct 28 14:29:52 superman-laptop init: tty4 main process (4388) killed by TERM signal
Oct 28 14:29:52 superman-laptop init: tty5 main process (4389) killed by TERM signal
Oct 28 14:29:52 superman-laptop init: tty2 main process (4393) killed by TERM signal
Oct 28 14:29:52 superman-laptop init: tty3 main process (4394) killed by TERM signal
Oct 28 14:29:52 superman-laptop init: tty1 main process (4395) killed by TERM signal
Oct 28 14:29:52 superman-laptop init: tty6 main process (4396) killed by TERM signal
Oct 28 14:29:53 superman-laptop avahi-daemon[5302]: Got SIGTERM, quitting.
Oct 28 14:29:53 superman-laptop avahi-daemon[5302]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 14:29:55 superman-laptop rpc.statd[4261]: Caught signal 15, un-registering and exiting.
Oct 28 14:29:57 superman-laptop mountd[5113]: Caught signal 15, un-registering and exiting.
Oct 28 16:01:06 superman-laptop NetworkManager: <info>  starting... 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.346120] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.592842] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.593442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.594192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.594719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.595142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.595560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.595981] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.596399] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.596814] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.597227] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.597643] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.598225] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.598642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.663581] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.665043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.666081] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.666464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.666842] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.667280] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.668468] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.668847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.669238] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.670126] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.670506] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.670878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.671251] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.714136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.714751] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.715123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.715495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.715864] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.716278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.716761] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.717142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.717602] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.718010] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.720048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.720419] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.720781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.721142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.721502] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.721894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.722246] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.722610] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.722975] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.723340] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.723706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.724112] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.724614] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.725008] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.725402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.725761] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.726136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.726492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.726847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.727203] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.727558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.727913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.728268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.728623] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.728978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.729333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.729688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.730083] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.730437] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 28 16:01:06 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 28 16:01:06 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 16:01:06 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 16:01:06 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 28 16:01:06 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 28 16:01:06 superman-laptop NetworkManager: <debug> [1193601666.798158] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 28 16:01:07 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 16:01:07 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 16:01:07 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 28 16:01:07 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.310649] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.311187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.311554] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.311911] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.312270] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.312623] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.312982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.313335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.313691] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.314060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.314421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.314778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.315178] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.315548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.315901] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.316258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.316609] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.316966] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.317316] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.317669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.326098] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.326566] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.326932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.327295] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.327673] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.328036] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.328397] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.328758] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 28 16:01:07 superman-laptop NetworkManager: <debug> [1193601667.329118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: Successfully dropped root privileges.
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: avahi-daemon 0.6.20 starting up.
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: Successfully called chroot().
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: Successfully dropped remaining capabilities.
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: No service file found in /etc/avahi/services.
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: Network interface enumeration completed.
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 28 16:01:08 superman-laptop avahi-daemon[5378]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 4235260480.
Oct 28 16:01:08 superman-laptop hcid[5413]: Bluetooth HCI daemon
Oct 28 16:01:08 superman-laptop hcid[5413]: Starting SDP server
Oct 28 16:01:08 superman-laptop hcid[5413]: Created local server at unix:abstract=/var/run/dbus-oDXCHJ46uQ,guid=050d62acb85119cf84eba9004724ea84
Oct 28 16:01:08 superman-laptop audio[5425]: Bluetooth Audio daemon
Oct 28 16:01:08 superman-laptop audio[5425]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 28 16:01:08 superman-laptop audio[5425]: Unix socket created: 5
Oct 28 16:01:08 superman-laptop input[5426]: Bluetooth Input daemon
Oct 28 16:01:08 superman-laptop input[5426]: Registered input manager path:/org/bluez/input
Oct 28 16:01:08 superman-laptop audio[5425]: add_service_record: got record id 0x10000
Oct 28 16:01:08 superman-laptop audio[5425]: add_service_record: got record id 0x10001
Oct 28 16:01:08 superman-laptop audio[5425]: Registered manager path:/org/bluez/audio
Oct 28 16:01:11 superman-laptop ntpd[5496]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 28 16:01:11 superman-laptop ntpd[5497]: precision = 1.000 usec
Oct 28 16:01:11 superman-laptop ntpd[5497]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 28 16:01:11 superman-laptop ntpd[5497]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 28 16:01:11 superman-laptop ntpd[5497]: Listening on interface #2 lo, ::1#123 Enabled
Oct 28 16:01:11 superman-laptop ntpd[5497]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 28 16:01:11 superman-laptop ntpd[5497]: kernel time sync status 0040
Oct 28 16:01:11 superman-laptop ntpd[5497]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: host name not found: ntp.ubuntu.com
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: host name not found: clock.tricity.wsu.edu
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: host name not found: wuarchive.wustl.edu
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: host name not found: gilbreth.ecn.purdue.edu
Oct 28 16:01:13 superman-laptop ntpd_initres[5538]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 28 16:10:32 superman-laptop hcid[5413]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Oct 28 16:10:32 superman-laptop hcid[5413]: Default authorization agent (:1.17, /org/bluez/auth) registered
Oct 28 16:10:36 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 28 16:11:45 superman-laptop hcid[5413]: Default passkey agent (:1.28, /org/bluez/passkey) registered
Oct 28 16:11:45 superman-laptop hcid[5413]: Default authorization agent (:1.28, /org/bluez/auth) registered
Oct 28 16:11:46 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Bowman'. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, but NO valid key exists.  New key needed. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Bowman'. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Bowman' received. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 16:11:59 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Bowman' is encrypted, and a key exists.  No new key needed. 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426f776d616e' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 16:12:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 16:12:01 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Bowman'. 
Oct 28 16:12:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 28 16:12:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 28 16:12:02 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 28 16:12:02 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 28 16:12:02 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 28 16:12:02 superman-laptop avahi-daemon[5378]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 16:12:03 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 28 16:12:04 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 28 16:12:04 superman-laptop dhclient: DHCPACK from 192.168.0.7
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 28 16:12:04 superman-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 28 16:12:04 superman-laptop dhclient: bound to 192.168.0.87 -- renewal in 310760 seconds.
Oct 28 16:12:04 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>    address 192.168.0.87 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>    broadcast 192.168.0.255 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>    gateway 192.168.0.1 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>    nameserver 192.168.0.7 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>    domain name 'bei.image' 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 28 16:12:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Withdrawing address record for 192.168.0.87 on eth1.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 16:12:04 superman-laptop avahi-daemon[5378]: Registering new address record for 192.168.0.87 on eth1.IPv4.
Oct 28 16:12:05 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 28 16:12:05 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 28 16:12:05 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 28 16:12:05 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 28 16:12:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 28 16:12:05 superman-laptop ntpdate[6318]: can't find host clock.tricity.wsu.edu 
Oct 28 16:12:05 superman-laptop ntpdate[6318]: the NTP socket is in use, exiting
Oct 28 16:12:06 superman-laptop avahi-daemon[5378]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 16:16:12 superman-laptop ntpd[5497]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 28 16:16:12 superman-laptop ntpd[5497]: Listening on interface #5 eth1, 192.168.0.87#123 Enabled
Oct 28 16:19:10 superman-laptop init: tty4 main process (4472) killed by TERM signal
Oct 28 16:19:10 superman-laptop init: tty5 main process (4473) killed by TERM signal
Oct 28 16:19:10 superman-laptop init: tty2 main process (4475) killed by TERM signal
Oct 28 16:19:10 superman-laptop init: tty3 main process (4477) killed by TERM signal
Oct 28 16:19:10 superman-laptop init: tty1 main process (4479) killed by TERM signal
Oct 28 16:19:10 superman-laptop init: tty6 main process (4480) killed by TERM signal
Oct 28 16:19:10 superman-laptop avahi-daemon[5378]: Got SIGTERM, quitting.
Oct 28 16:19:10 superman-laptop avahi-daemon[5378]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.87.
Oct 28 16:19:13 superman-laptop rpc.statd[4345]: Caught signal 15, un-registering and exiting.
Oct 28 16:19:15 superman-laptop mountd[5190]: Caught signal 15, un-registering and exiting.
Oct 28 20:53:35 superman-laptop NetworkManager: <info>  starting... 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.447057] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.727686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.728355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.728753] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.729252] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.789323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.789929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.790888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.792612] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.796160] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.796569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.796950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.797338] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.798243] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.798619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.799024] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.799411] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.800254] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.800627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.801001] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.801386] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.845381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.845787] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.846161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.846532] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.846971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.847459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.847843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.848304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.848703] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.850720] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.851117] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.851490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.851860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.852268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.852758] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.853153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.853551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.853914] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.854276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.854636] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.855019] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.855380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.855741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.856100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.856459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.856818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.857176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.857535] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.857893] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.858250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.858607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.858983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.859350] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.859713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.860081] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.861179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.861583] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.861949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.862316] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.862710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.863161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.863597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.864028] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 28 20:53:35 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 28 20:53:35 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 20:53:35 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 20:53:35 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 28 20:53:35 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 28 20:53:35 superman-laptop NetworkManager: <debug> [1193619215.932427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 28 20:53:36 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 28 20:53:36 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 28 20:53:36 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 28 20:53:36 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.490950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.492169] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.492886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.493594] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.494300] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.503172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.503929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.504650] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.505371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.506089] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.506808] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.507516] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.508221] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.508937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.509674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.510384] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.511095] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.511781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.512366] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.512970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.513556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.514148] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.514792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.515407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.515986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.516562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.517170] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.517748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.518321] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.518918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 28 20:53:36 superman-laptop NetworkManager: <debug> [1193619216.519509] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: Successfully dropped root privileges.
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: avahi-daemon 0.6.20 starting up.
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: Successfully called chroot().
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: Successfully dropped remaining capabilities.
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: No service file found in /etc/avahi/services.
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: Network interface enumeration completed.
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 28 20:53:37 superman-laptop avahi-daemon[5388]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 1770413012.
Oct 28 20:53:37 superman-laptop hcid[5424]: Bluetooth HCI daemon
Oct 28 20:53:37 superman-laptop hcid[5424]: Starting SDP server
Oct 28 20:53:37 superman-laptop hcid[5424]: Created local server at unix:abstract=/var/run/dbus-RYFBPxG8IH,guid=c403825a1970e8004aeb8c0047252f11
Oct 28 20:53:37 superman-laptop input[5437]: Bluetooth Input daemon
Oct 28 20:53:37 superman-laptop input[5437]: Registered input manager path:/org/bluez/input
Oct 28 20:53:37 superman-laptop audio[5436]: Bluetooth Audio daemon
Oct 28 20:53:37 superman-laptop audio[5436]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 28 20:53:37 superman-laptop audio[5436]: Unix socket created: 5
Oct 28 20:53:37 superman-laptop audio[5436]: add_service_record: got record id 0x10000
Oct 28 20:53:37 superman-laptop audio[5436]: add_service_record: got record id 0x10001
Oct 28 20:53:37 superman-laptop audio[5436]: Registered manager path:/org/bluez/audio
Oct 28 20:53:40 superman-laptop ntpd[5507]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 28 20:53:40 superman-laptop ntpd[5508]: precision = 1.000 usec
Oct 28 20:53:40 superman-laptop ntpd[5508]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 28 20:53:40 superman-laptop ntpd[5508]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 28 20:53:40 superman-laptop ntpd[5508]: Listening on interface #2 lo, ::1#123 Enabled
Oct 28 20:53:40 superman-laptop ntpd[5508]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 28 20:53:40 superman-laptop ntpd[5508]: kernel time sync status 0040
Oct 28 20:53:40 superman-laptop ntpd[5508]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: host name not found: ntp.ubuntu.com
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: host name not found: clock.tricity.wsu.edu
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: host name not found: wuarchive.wustl.edu
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: host name not found: gilbreth.ecn.purdue.edu
Oct 28 20:53:42 superman-laptop ntpd_initres[5536]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 28 20:54:18 superman-laptop hcid[5424]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Oct 28 20:54:18 superman-laptop hcid[5424]: Default authorization agent (:1.17, /org/bluez/auth) registered
Oct 28 20:54:22 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 28 20:55:01 superman-laptop NetworkManager: <debug> [1193619301.658435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial'). 
Oct 28 20:55:01 superman-laptop NetworkManager: <debug> [1193619301.766293] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0'). 
Oct 28 20:55:01 superman-laptop NetworkManager: <debug> [1193619301.798031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_usbraw'). 
Oct 28 20:55:01 superman-laptop NetworkManager: <debug> [1193619301.818869] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c03d_noserial_if0_logicaldev_input'). 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Forghani'. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, but NO valid key exists.  New key needed. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Forghani'. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Forghani' received. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 28 20:55:46 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, and a key exists.  No new key needed. 
Oct 28 20:55:47 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 28 20:55:47 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 28 20:55:47 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 28 20:55:47 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 20:55:47 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 466f726768616e69' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Forghani'. 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 28 20:55:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 28 20:55:49 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 28 20:55:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 28 20:55:49 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 28 20:55:50 superman-laptop avahi-daemon[5388]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 20:55:50 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 28 20:55:53 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 28 20:55:53 superman-laptop dhclient: DHCPNAK from 192.168.2.1
Oct 28 20:55:53 superman-laptop avahi-autoipd(eth1)[6015]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 28 20:55:53 superman-laptop avahi-autoipd(eth1)[6015]: Successfully called chroot().
Oct 28 20:55:53 superman-laptop avahi-autoipd(eth1)[6015]: Successfully dropped root privileges.
Oct 28 20:55:53 superman-laptop avahi-autoipd(eth1)[6015]: Starting with address 169.254.3.94
Oct 28 20:55:53 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 28 20:55:59 superman-laptop avahi-autoipd(eth1)[6015]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 28 20:55:59 superman-laptop avahi-daemon[5388]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 28 20:55:59 superman-laptop avahi-daemon[5388]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 20:55:59 superman-laptop avahi-daemon[5388]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 28 20:56:03 superman-laptop avahi-autoipd(eth1)[6015]: Successfully claimed IP address 169.254.3.94
Oct 28 20:56:03 superman-laptop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth1 
Oct 28 20:56:03 superman-laptop avahi-autoipd(eth1)[6015]: Got SIGTERM, quitting.
Oct 28 20:56:03 superman-laptop avahi-autoipd(eth1)[6015]: Callout STOP, address 169.254.3.94 on interface eth1
Oct 28 20:56:03 superman-laptop avahi-daemon[5388]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 28 20:56:03 superman-laptop avahi-daemon[5388]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 28 20:56:03 superman-laptop avahi-daemon[5388]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 20:56:03 superman-laptop avahi-autoipd(eth1)[6016]: client: RTNETLINK answers: No such process
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 28 20:56:04 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 28 20:56:04 superman-laptop dhclient: DHCPOFFER from 192.168.2.1
Oct 28 20:56:04 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 28 20:56:04 superman-laptop dhclient: DHCPACK from 192.168.2.1
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Registering new address record for 192.168.2.2 on eth1.IPv4.
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 28 20:56:04 superman-laptop dhclient: bound to 192.168.2.2 -- renewal in 953864283 seconds.
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>    address 192.168.2.2 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>    broadcast 192.168.2.255 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>    gateway 192.168.2.1 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>    nameserver 192.168.2.1 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>    nameserver 192.168.10.1 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>    domain name 'Forghani1' 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 28 20:56:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Withdrawing address record for 192.168.2.2 on eth1.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: New relevant interface eth1.IPv4 for mDNS.
Oct 28 20:56:04 superman-laptop avahi-daemon[5388]: Registering new address record for 192.168.2.2 on eth1.IPv4.
Oct 28 20:56:05 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 28 20:56:05 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 28 20:56:05 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 28 20:56:05 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 28 20:56:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 28 20:56:07 superman-laptop avahi-daemon[5388]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 28 20:56:36 superman-laptop ntpdate[6084]: can't find host clock.tricity.wsu.edu 
Oct 28 20:57:07 superman-laptop ntpdate[6084]: the NTP socket is in use, exiting
Oct 28 20:58:41 superman-laptop ntpd[5508]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 28 20:58:41 superman-laptop ntpd[5508]: Listening on interface #5 eth1, 192.168.2.2#123 Enabled
Oct 28 21:36:46 superman-laptop init: tty4 main process (4477) killed by TERM signal
Oct 28 21:36:46 superman-laptop init: tty5 main process (4478) killed by TERM signal
Oct 28 21:36:46 superman-laptop init: tty2 main process (4480) killed by TERM signal
Oct 28 21:36:46 superman-laptop init: tty3 main process (4482) killed by TERM signal
Oct 28 21:36:46 superman-laptop init: tty1 main process (4484) killed by TERM signal
Oct 28 21:36:46 superman-laptop init: tty6 main process (4485) killed by TERM signal
Oct 28 21:36:46 superman-laptop avahi-daemon[5388]: Got SIGTERM, quitting.
Oct 28 21:36:46 superman-laptop avahi-daemon[5388]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 28 21:36:48 superman-laptop rpc.statd[4350]: Caught signal 15, un-registering and exiting.
Oct 28 21:36:50 superman-laptop mountd[5201]: Caught signal 15, un-registering and exiting.
Oct 29 08:37:29 superman-laptop NetworkManager: <info>  starting... 
Oct 29 08:37:29 superman-laptop NetworkManager: <debug> [1193661449.814488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.075479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.075974] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.076430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.077552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.077985] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.078410] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.079267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.138440] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.139073] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.139800] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.140413] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.140841] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.141293] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.141714] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.142139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.144329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.145590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.146348] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.146959] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.147382] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.147809] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.148215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.148624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.149030] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.149444] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.150127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.150629] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.151040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.151464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.151872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.152278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.152689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.194391] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.195265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.195692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.196100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.196506] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.196912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.197315] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.197738] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.198158] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.198644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.199252] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.199702] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.200139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.200576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.201007] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.201430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.201851] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.202289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.202722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.203175] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.203610] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.204040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.204472] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.204903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.205330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.205755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.206394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.206827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.207249] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.207681] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.208119] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.208537] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.278303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 29 08:37:30 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.821595] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.822380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.822841] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.823276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.823709] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.824139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.824571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.825002] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.825432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.825863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.834368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.834809] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.835333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.835758] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.836173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.836587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.837002] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.837419] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.837828] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.838269] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.838681] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.839101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.839519] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.839936] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.840362] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.840795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.841213] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.841620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.842062] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 29 08:37:30 superman-laptop NetworkManager: <debug> [1193661450.842493] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: Successfully dropped root privileges.
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: avahi-daemon 0.6.20 starting up.
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: Successfully called chroot().
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: Successfully dropped remaining capabilities.
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: No service file found in /etc/avahi/services.
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: Network interface enumeration completed.
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 29 08:37:31 superman-laptop avahi-daemon[5333]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 527447392.
Oct 29 08:37:31 superman-laptop hcid[5368]: Bluetooth HCI daemon
Oct 29 08:37:31 superman-laptop hcid[5368]: Starting SDP server
Oct 29 08:37:31 superman-laptop hcid[5368]: Created local server at unix:abstract=/var/run/dbus-NuTRBDocwJ,guid=c13b05248a8c8e73796be8004725d40b
Oct 29 08:37:31 superman-laptop audio[5380]: Bluetooth Audio daemon
Oct 29 08:37:31 superman-laptop audio[5380]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 29 08:37:31 superman-laptop audio[5380]: Unix socket created: 5
Oct 29 08:37:31 superman-laptop input[5381]: Bluetooth Input daemon
Oct 29 08:37:31 superman-laptop input[5381]: Registered input manager path:/org/bluez/input
Oct 29 08:37:31 superman-laptop audio[5380]: add_service_record: got record id 0x10000
Oct 29 08:37:31 superman-laptop audio[5380]: add_service_record: got record id 0x10001
Oct 29 08:37:31 superman-laptop audio[5380]: Registered manager path:/org/bluez/audio
Oct 29 08:37:34 superman-laptop ntpd[5451]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 29 08:37:34 superman-laptop ntpd[5452]: precision = 1.000 usec
Oct 29 08:37:34 superman-laptop ntpd[5452]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 29 08:37:34 superman-laptop ntpd[5452]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 29 08:37:34 superman-laptop ntpd[5452]: Listening on interface #2 lo, ::1#123 Enabled
Oct 29 08:37:34 superman-laptop ntpd[5452]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 29 08:37:34 superman-laptop ntpd[5452]: kernel time sync status 0040
Oct 29 08:37:34 superman-laptop ntpd[5452]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: host name not found: ntp.ubuntu.com
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: host name not found: clock.tricity.wsu.edu
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: host name not found: wuarchive.wustl.edu
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: host name not found: gilbreth.ecn.purdue.edu
Oct 29 08:37:36 superman-laptop ntpd_initres[5494]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 29 08:37:53 superman-laptop hcid[5368]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Oct 29 08:37:53 superman-laptop hcid[5368]: Default authorization agent (:1.17, /org/bluez/auth) registered
Oct 29 08:37:59 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 08:38:01 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 29 08:38:04 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 29 08:38:04 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 29 08:38:04 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 29 08:38:04 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 29 08:38:04 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 29 08:38:04 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 29 08:38:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (6/10). 
Oct 29 08:38:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (7/10). 
Oct 29 08:38:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (8/10). 
Oct 29 08:38:05 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (9/10). 
Oct 29 08:38:05 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:38:06 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 08:38:07 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 29 08:38:07 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 29 08:38:07 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 29 08:38:08 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 29 08:38:08 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 29 08:38:08 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 29 08:38:09 superman-laptop avahi-daemon[5333]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 08:38:09 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 29 08:38:10 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 29 08:38:10 superman-laptop dhclient: DHCPNAK from 1.1.1.1
Oct 29 08:38:10 superman-laptop avahi-autoipd(eth1)[5950]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 29 08:38:10 superman-laptop avahi-autoipd(eth1)[5950]: Successfully called chroot().
Oct 29 08:38:10 superman-laptop avahi-autoipd(eth1)[5950]: Successfully dropped root privileges.
Oct 29 08:38:10 superman-laptop avahi-autoipd(eth1)[5950]: Starting with address 169.254.3.94
Oct 29 08:38:10 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 08:38:16 superman-laptop avahi-autoipd(eth1)[5950]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 29 08:38:16 superman-laptop avahi-daemon[5333]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 29 08:38:16 superman-laptop avahi-daemon[5333]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 08:38:16 superman-laptop avahi-daemon[5333]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 29 08:38:20 superman-laptop avahi-autoipd(eth1)[5950]: Successfully claimed IP address 169.254.3.94
Oct 29 08:38:20 superman-laptop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth1 
Oct 29 08:38:20 superman-laptop avahi-autoipd(eth1)[5950]: Got SIGTERM, quitting.
Oct 29 08:38:20 superman-laptop avahi-autoipd(eth1)[5950]: Callout STOP, address 169.254.3.94 on interface eth1
Oct 29 08:38:20 superman-laptop avahi-daemon[5333]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 29 08:38:20 superman-laptop avahi-daemon[5333]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 29 08:38:20 superman-laptop avahi-daemon[5333]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 08:38:20 superman-laptop avahi-autoipd(eth1)[5951]: client: RTNETLINK answers: No such process
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 29 08:38:21 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct 29 08:38:21 superman-laptop dhclient: DHCPOFFER from 1.1.1.1
Oct 29 08:38:21 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 29 08:38:21 superman-laptop dhclient: DHCPACK from 1.1.1.1
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Registering new address record for 150.216.229.40 on eth1.IPv4.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Withdrawing address record for 150.216.229.40 on eth1.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Registering new address record for 150.216.229.40 on eth1.IPv4.
Oct 29 08:38:21 superman-laptop dhclient: bound to 150.216.229.40 -- renewal in 1616 seconds.
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>    address 150.216.229.40 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>    broadcast 150.216.229.255 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>    gateway 150.216.229.254 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 29 08:38:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Withdrawing address record for 150.216.229.40 on eth1.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 08:38:21 superman-laptop avahi-daemon[5333]: Registering new address record for 150.216.229.40 on eth1.IPv4.
Oct 29 08:38:22 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 29 08:38:22 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 29 08:38:22 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 29 08:38:22 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 29 08:38:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 29 08:38:22 superman-laptop ntpdate[6063]: can't find host clock.tricity.wsu.edu 
Oct 29 08:38:23 superman-laptop ntpdate[6063]: the NTP socket is in use, exiting
Oct 29 08:38:24 superman-laptop avahi-daemon[5333]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 08:38:42 superman-laptop NetworkManager: <debug> [1193661522.714113] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 29 08:39:42 superman-laptop NetworkManager: <debug> [1193661582.718111] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 29 08:42:35 superman-laptop ntpd[5452]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 29 08:42:35 superman-laptop ntpd[5452]: Listening on interface #5 eth1, 150.216.229.40#123 Enabled
Oct 29 08:43:52 superman-laptop NetworkManager: <debug> [1193661832.726115] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 29 08:48:12 superman-laptop NetworkManager: <debug> [1193662092.734094] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 29 08:52:32 superman-laptop NetworkManager: <debug> [1193662352.734098] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 29 08:56:52 superman-laptop NetworkManager: <debug> [1193662612.738106] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 29 08:58:56 superman-laptop NetworkManager: <debug> [1193662736.738235] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 29 08:59:16 superman-laptop NetworkManager: <info>  eth1: link timed out. 
Oct 29 08:59:16 superman-laptop NetworkManager: <info>  SWITCH: found better connection 'eth1/taho' than current connection 'eth1/taho'.  same_ssid=1, have_link=0 
Oct 29 08:59:16 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 29 08:59:16 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 29 08:59:16 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 29 08:59:16 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5913
Oct 29 08:59:16 superman-laptop dhclient: killed old client process, removed PID file
Oct 29 08:59:16 superman-laptop dhclient: DHCPRELEASE on eth1 to 1.1.1.1 port 67
Oct 29 08:59:16 superman-laptop avahi-daemon[5333]: Withdrawing address record for 150.216.229.40 on eth1.
Oct 29 08:59:16 superman-laptop avahi-daemon[5333]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 08:59:16 superman-laptop avahi-daemon[5333]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 08:59:17 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 29 08:59:29 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Oct 29 08:59:29 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'DISABLE_NETWORK 0'.  Response: 'TIMEOUT[CLI]' 
Oct 29 08:59:29 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't disable network in supplicant_cleanup 
Oct 29 08:59:29 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 29 08:59:41 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Oct 29 08:59:41 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'AP_SCAN 0'.  Response: 'TIMEOUT[CLI]' 
Oct 29 08:59:41 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't set AP_SCAN 0 
Oct 29 08:59:41 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 29 08:59:42 superman-laptop avahi-daemon[5333]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Oct 29 08:59:53 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'TERMINATE'.  Response: 'TIMEOUT[CLI]' 
Oct 29 08:59:53 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't terminate wpasupplicant cleanly. 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Oct 29 08:59:53 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 08:59:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 08:59:55 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 29 08:59:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 29 08:59:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 29 08:59:56 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 29 08:59:56 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Oct 29 08:59:56 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 29 08:59:56 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 29 08:59:56 superman-laptop avahi-daemon[5333]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 08:59:57 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 29 08:59:58 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 09:00:01 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Oct 29 09:00:01 superman-laptop dhclient: DHCPOFFER from 1.1.1.1
Oct 29 09:00:01 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 29 09:00:01 superman-laptop dhclient: DHCPACK from 1.1.1.1
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Registering new address record for 150.216.229.40 on eth1.IPv4.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Withdrawing address record for 150.216.229.40 on eth1.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Registering new address record for 150.216.229.40 on eth1.IPv4.
Oct 29 09:00:01 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 29 09:00:01 superman-laptop dhclient: bound to 150.216.229.40 -- renewal in 1480 seconds.
Oct 29 09:00:01 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>    address 150.216.229.40 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>    broadcast 150.216.229.255 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>    gateway 150.216.229.254 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 29 09:00:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Withdrawing address record for 150.216.229.40 on eth1.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 09:00:01 superman-laptop avahi-daemon[5333]: Registering new address record for 150.216.229.40 on eth1.IPv4.
Oct 29 09:00:02 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 29 09:00:02 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 29 09:00:02 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 29 09:00:02 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 29 09:00:02 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 29 09:00:03 superman-laptop ntpdate[7567]: can't find host clock.tricity.wsu.edu 
Oct 29 09:00:03 superman-laptop ntpdate[7567]: the NTP socket is in use, exiting
Oct 29 09:00:04 superman-laptop avahi-daemon[5333]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 09:00:48 superman-laptop NetworkManager: <debug> [1193662848.866075] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 29 09:01:18 superman-laptop NetworkManager: <debug> [1193662878.874057] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 29 09:01:48 superman-laptop NetworkManager: <debug> [1193662908.866075] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 29 09:03:58 superman-laptop NetworkManager: <debug> [1193663038.870129] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 29 09:10:28 superman-laptop NetworkManager: <debug> [1193663428.882101] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A8:F0 to 00:17:0F:8C:09:60 on wireless network 'taho' 
Oct 29 09:12:38 superman-laptop NetworkManager: <debug> [1193663558.894059] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:09:60 to 00:17:0F:8C:A8:F0 on wireless network 'taho' 
Oct 29 09:24:41 superman-laptop dhclient: DHCPREQUEST on eth1 to 1.1.1.1 port 67
Oct 29 09:24:41 superman-laptop dhclient: DHCPACK from 1.1.1.1
Oct 29 09:24:41 superman-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Oct 29 09:24:41 superman-laptop dhclient: bound to 150.216.229.40 -- renewal in 1393 seconds.
Oct 29 09:33:18 superman-laptop init: tty4 main process (4421) killed by TERM signal
Oct 29 09:33:18 superman-laptop init: tty5 main process (4422) killed by TERM signal
Oct 29 09:33:18 superman-laptop init: tty2 main process (4424) killed by TERM signal
Oct 29 09:33:18 superman-laptop init: tty3 main process (4426) killed by TERM signal
Oct 29 09:33:18 superman-laptop init: tty1 main process (4427) killed by TERM signal
Oct 29 09:33:18 superman-laptop init: tty6 main process (4428) killed by TERM signal
Oct 29 09:33:18 superman-laptop avahi-daemon[5333]: Got SIGTERM, quitting.
Oct 29 09:33:18 superman-laptop avahi-daemon[5333]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.229.40.
Oct 29 09:33:20 superman-laptop rpc.statd[4294]: Caught signal 15, un-registering and exiting.
Oct 29 09:33:22 superman-laptop mountd[5145]: Caught signal 15, un-registering and exiting.
Oct 29 14:39:52 superman-laptop NetworkManager: <info>  starting... 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.282281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.541403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.542218] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.542909] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.543610] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.544089] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.544621] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.545308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.546112] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.607048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.607879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.608970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.609422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.609869] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.610942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.611934] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.612384] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.612822] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.613281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.613740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.615499] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.615976] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.616417] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.616858] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.617299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.617737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.618175] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.618632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.619091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.619525] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.619957] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.620383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.620810] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.621265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.621700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.622135] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.622587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.623022] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.623456] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.623889] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.624339] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.624968] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.625404] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.625836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.626263] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.626722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.668876] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.669375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.669810] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.670240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.670686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.671162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.671595] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.672023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.672449] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.672893] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.673321] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.673749] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.674176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.674625] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.675051] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.675477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.675903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.676346] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.676811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.677237] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 29 14:39:52 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 29 14:39:52 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 14:39:52 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 14:39:52 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 29 14:39:52 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 29 14:39:52 superman-laptop NetworkManager: <debug> [1193683192.749130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 29 14:39:53 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 14:39:53 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 14:39:53 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 29 14:39:53 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.388089] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.388939] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.389538] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.390201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.390802] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.391409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.392009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.392607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.393205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.393802] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.402467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.403147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.403814] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.404481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.405143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.405805] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.406579] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.407238] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.407898] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.408773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.409433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.410112] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.410791] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.411449] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.412129] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.412782] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.413431] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.414097] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 29 14:39:53 superman-laptop NetworkManager: <debug> [1193683193.414769] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: Successfully dropped root privileges.
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: avahi-daemon 0.6.20 starting up.
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: Successfully called chroot().
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: Successfully dropped remaining capabilities.
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: No service file found in /etc/avahi/services.
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: Network interface enumeration completed.
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 29 14:39:54 superman-laptop avahi-daemon[5354]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 248497705.
Oct 29 14:39:54 superman-laptop hcid[5390]: Bluetooth HCI daemon
Oct 29 14:39:54 superman-laptop hcid[5390]: Starting SDP server
Oct 29 14:39:54 superman-laptop hcid[5390]: Created local server at unix:abstract=/var/run/dbus-gtxgxJYVMA,guid=1cc425c73dafa2334415b900472628fa
Oct 29 14:39:54 superman-laptop audio[5402]: Bluetooth Audio daemon
Oct 29 14:39:54 superman-laptop audio[5402]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 29 14:39:54 superman-laptop audio[5402]: Unix socket created: 5
Oct 29 14:39:54 superman-laptop input[5403]: Bluetooth Input daemon
Oct 29 14:39:54 superman-laptop input[5403]: Registered input manager path:/org/bluez/input
Oct 29 14:39:54 superman-laptop audio[5402]: add_service_record: got record id 0x10000
Oct 29 14:39:54 superman-laptop audio[5402]: add_service_record: got record id 0x10001
Oct 29 14:39:54 superman-laptop audio[5402]: Registered manager path:/org/bluez/audio
Oct 29 14:39:57 superman-laptop ntpd[5473]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 29 14:39:57 superman-laptop ntpd[5474]: precision = 1.000 usec
Oct 29 14:39:57 superman-laptop ntpd[5474]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 29 14:39:57 superman-laptop ntpd[5474]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 29 14:39:57 superman-laptop ntpd[5474]: Listening on interface #2 lo, ::1#123 Enabled
Oct 29 14:39:57 superman-laptop ntpd[5474]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 29 14:39:57 superman-laptop ntpd[5474]: kernel time sync status 0040
Oct 29 14:39:57 superman-laptop ntpd[5474]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: host name not found: ntp.ubuntu.com
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: host name not found: clock.tricity.wsu.edu
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: host name not found: wuarchive.wustl.edu
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: host name not found: gilbreth.ecn.purdue.edu
Oct 29 14:39:59 superman-laptop ntpd_initres[5529]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 29 14:40:13 superman-laptop hcid[5390]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Oct 29 14:40:13 superman-laptop hcid[5390]: Default authorization agent (:1.17, /org/bluez/auth) registered
Oct 29 14:40:18 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 29 14:40:19 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 14:40:20 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 29 14:40:21 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 29 14:40:21 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 29 14:40:21 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 29 14:40:21 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 29 14:40:21 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 29 14:40:21 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 29 14:40:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 29 14:40:23 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 29 14:40:23 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 29 14:40:23 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 29 14:40:24 superman-laptop avahi-daemon[5354]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 14:40:25 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 29 14:40:27 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct 29 14:40:27 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 14:40:27 superman-laptop dhclient: DHCPOFFER from 1.1.1.1
Oct 29 14:40:27 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 29 14:40:27 superman-laptop dhclient: DHCPACK from 1.1.1.1
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.8.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: Registering new address record for 150.216.224.8 on eth1.IPv4.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: Withdrawing address record for 150.216.224.8 on eth1.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.8.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.8.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 14:40:27 superman-laptop avahi-daemon[5354]: Registering new address record for 150.216.224.8 on eth1.IPv4.
Oct 29 14:40:28 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 29 14:40:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 29 14:40:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 29 14:40:28 superman-laptop dhclient: bound to 150.216.224.8 -- renewal in 1492 seconds.
Oct 29 14:40:29 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>    address 150.216.224.8 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>    broadcast 150.216.224.255 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>    gateway 150.216.224.254 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 29 14:40:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 29 14:40:29 superman-laptop avahi-daemon[5354]: Withdrawing address record for 150.216.224.8 on eth1.
Oct 29 14:40:29 superman-laptop avahi-daemon[5354]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.8.
Oct 29 14:40:29 superman-laptop avahi-daemon[5354]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 14:40:29 superman-laptop avahi-daemon[5354]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 29 14:40:29 superman-laptop avahi-daemon[5354]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.224.8.
Oct 29 14:40:29 superman-laptop avahi-daemon[5354]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 14:40:29 superman-laptop avahi-daemon[5354]: Registering new address record for 150.216.224.8 on eth1.IPv4.
Oct 29 14:40:30 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 29 14:40:30 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 29 14:40:30 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 29 14:40:30 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 29 14:40:30 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 29 14:40:30 superman-laptop NetworkManager: <debug> [1193683230.217090] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 29 14:40:30 superman-laptop ntpdate[5956]: can't find host clock.tricity.wsu.edu 
Oct 29 14:40:30 superman-laptop ntpdate[5956]: the NTP socket is in use, exiting
Oct 29 14:40:31 superman-laptop avahi-daemon[5354]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 14:44:58 superman-laptop ntpd[5474]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 29 14:44:58 superman-laptop ntpd[5474]: Listening on interface #5 eth1, 150.216.224.8#123 Enabled
Oct 29 14:49:55 superman-laptop init: tty4 main process (4449) killed by TERM signal
Oct 29 14:49:55 superman-laptop init: tty5 main process (4450) killed by TERM signal
Oct 29 14:49:55 superman-laptop init: tty2 main process (4452) killed by TERM signal
Oct 29 14:49:55 superman-laptop init: tty3 main process (4454) killed by TERM signal
Oct 29 14:49:55 superman-laptop init: tty1 main process (4456) killed by TERM signal
Oct 29 14:49:55 superman-laptop init: tty6 main process (4457) killed by TERM signal
Oct 29 14:49:55 superman-laptop avahi-daemon[5354]: Got SIGTERM, quitting.
Oct 29 14:49:55 superman-laptop avahi-daemon[5354]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.224.8.
Oct 29 14:49:57 superman-laptop rpc.statd[4322]: Caught signal 15, un-registering and exiting.
Oct 29 14:49:59 superman-laptop mountd[5166]: Caught signal 15, un-registering and exiting.
Oct 29 16:52:56 superman-laptop NetworkManager: <info>  starting... 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.633639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.972947] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.973469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.973838] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.974687] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.975074] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.975416] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.975757] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.976100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.976439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.976780] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.977128] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 29 16:52:56 superman-laptop NetworkManager: <debug> [1193691176.977492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.041990] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.042814] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.043412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.043885] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.044331] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.044773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.045212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.045668] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.046106] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.046783] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.047223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.047663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.048107] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.048543] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.049046] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.050521] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.051163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.052098] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.052548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.052978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.053430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.054486] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.054933] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.055381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.098037] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.098586] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.099028] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.099511] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.100079] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.100544] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.101036] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.101513] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.103580] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.104020] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.104450] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.104918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.105483] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.105959] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.106417] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.106843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.107267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.107689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.108111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.108533] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.108954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.109394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.109799] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.110181] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.110792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.111495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.111898] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.112274] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.180103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 29 16:52:57 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.715095] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.715892] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.716333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.716769] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.717204] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.717658] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.718093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.718527] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.718975] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.719406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.719837] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.720267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.720697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.721130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.729625] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.729995] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.730356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.730709] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.731060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.731486] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.731896] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.732303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.732722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.733147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.733767] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.734468] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.735143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.735819] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.736494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.737169] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 29 16:52:57 superman-laptop NetworkManager: <debug> [1193691177.737888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: Successfully dropped root privileges.
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: avahi-daemon 0.6.20 starting up.
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: Successfully called chroot().
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: Successfully dropped remaining capabilities.
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: No service file found in /etc/avahi/services.
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: Network interface enumeration completed.
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 29 16:52:58 superman-laptop avahi-daemon[5385]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 507008285.
Oct 29 16:52:58 superman-laptop hcid[5420]: Bluetooth HCI daemon
Oct 29 16:52:58 superman-laptop hcid[5420]: Starting SDP server
Oct 29 16:52:58 superman-laptop hcid[5420]: Created local server at unix:abstract=/var/run/dbus-IENtys2I3D,guid=17df66f002d26738fc7f30004726482a
Oct 29 16:52:58 superman-laptop audio[5432]: Bluetooth Audio daemon
Oct 29 16:52:58 superman-laptop audio[5432]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 29 16:52:58 superman-laptop audio[5432]: Unix socket created: 5
Oct 29 16:52:58 superman-laptop input[5433]: Bluetooth Input daemon
Oct 29 16:52:58 superman-laptop input[5433]: Registered input manager path:/org/bluez/input
Oct 29 16:52:58 superman-laptop audio[5432]: add_service_record: got record id 0x10000
Oct 29 16:52:58 superman-laptop audio[5432]: add_service_record: got record id 0x10001
Oct 29 16:52:58 superman-laptop audio[5432]: Registered manager path:/org/bluez/audio
Oct 29 16:53:01 superman-laptop ntpd[5503]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 29 16:53:01 superman-laptop ntpd[5504]: precision = 1.000 usec
Oct 29 16:53:01 superman-laptop ntpd[5504]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 29 16:53:01 superman-laptop ntpd[5504]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 29 16:53:01 superman-laptop ntpd[5504]: Listening on interface #2 lo, ::1#123 Enabled
Oct 29 16:53:01 superman-laptop ntpd[5504]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 29 16:53:01 superman-laptop ntpd[5504]: kernel time sync status 0040
Oct 29 16:53:01 superman-laptop ntpd[5504]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: host name not found: ntp.ubuntu.com
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: host name not found: clock.tricity.wsu.edu
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: host name not found: wuarchive.wustl.edu
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: host name not found: gilbreth.ecn.purdue.edu
Oct 29 16:53:03 superman-laptop ntpd_initres[5574]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 29 16:53:40 superman-laptop hcid[5420]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 29 16:53:40 superman-laptop hcid[5420]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 29 16:53:47 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Forghani'. 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, but NO valid key exists.  New key needed. 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Forghani'. 
Oct 29 16:53:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 16:53:49 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Forghani' received. 
Oct 29 16:53:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 16:53:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 16:53:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 16:53:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 16:53:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 16:53:49 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, and a key exists.  No new key needed. 
Oct 29 16:53:50 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 29 16:53:50 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 29 16:53:50 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 29 16:53:50 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 466f726768616e69' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Forghani'. 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 29 16:53:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 29 16:53:52 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 29 16:53:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 29 16:53:52 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 29 16:53:53 superman-laptop avahi-daemon[5385]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 16:53:54 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 29 16:53:55 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 29 16:53:55 superman-laptop dhclient: DHCPOFFER from 192.168.2.1
Oct 29 16:53:55 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 29 16:53:55 superman-laptop dhclient: DHCPACK from 192.168.2.1
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 29 16:53:55 superman-laptop dhclient: bound to 192.168.2.3 -- renewal in 953792412 seconds.
Oct 29 16:53:55 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>    address 192.168.2.3 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>    broadcast 192.168.2.255 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>    gateway 192.168.2.1 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>    nameserver 192.168.2.1 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>    nameserver 192.168.10.1 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>    domain name 'Forghani1' 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 29 16:53:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Withdrawing address record for 192.168.2.3 on eth1.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 16:53:55 superman-laptop avahi-daemon[5385]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 29 16:53:56 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 29 16:53:56 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 29 16:53:56 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 29 16:53:56 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 29 16:53:56 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 29 16:53:57 superman-laptop avahi-daemon[5385]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 16:54:29 superman-laptop ntpdate[6036]: can't find host clock.tricity.wsu.edu 
Oct 29 16:55:00 superman-laptop ntpdate[6036]: the NTP socket is in use, exiting
Oct 29 16:58:02 superman-laptop ntpd[5504]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 29 16:58:02 superman-laptop ntpd[5504]: Listening on interface #5 eth1, 192.168.2.3#123 Enabled
Oct 29 17:38:16 superman-laptop init: tty4 main process (4439) killed by TERM signal
Oct 29 17:38:16 superman-laptop init: tty5 main process (4440) killed by TERM signal
Oct 29 17:38:16 superman-laptop init: tty2 main process (4445) killed by TERM signal
Oct 29 17:38:16 superman-laptop init: tty3 main process (4446) killed by TERM signal
Oct 29 17:38:16 superman-laptop init: tty1 main process (4447) killed by TERM signal
Oct 29 17:38:16 superman-laptop init: tty6 main process (4448) killed by TERM signal
Oct 29 17:38:17 superman-laptop avahi-daemon[5385]: Got SIGTERM, quitting.
Oct 29 17:38:17 superman-laptop avahi-daemon[5385]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 17:38:19 superman-laptop rpc.statd[4312]: Caught signal 15, un-registering and exiting.
Oct 29 17:38:21 superman-laptop mountd[5197]: Caught signal 15, un-registering and exiting.
Oct 29 19:28:04 superman-laptop NetworkManager: <info>  starting... 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.697748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.991693] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.992157] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.992590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.993308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.993734] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.994150] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.994573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.995057] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 29 19:28:04 superman-laptop NetworkManager: <debug> [1193700484.995623] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.057901] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.058720] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.059840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.060658] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.061110] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.061551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.062017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.062454] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.062892] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.064651] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.065161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.065608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.066048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.066489] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.066926] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.067386] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.067824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.068272] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.068708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.069133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.069556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.069995] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.070427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.070856] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.071289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.071718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.072151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.072600] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.073031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.073477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.074105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.074539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.074970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.075403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.075846] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.076918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.077528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.077982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.119849] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.120372] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.120811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.121246] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.121683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.122138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.122624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.123176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.123613] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.124131] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.124600] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.126744] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.127202] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.127639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.128096] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.128544] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.128988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.129418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.198916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 29 19:28:05 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.805547] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.806292] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.806889] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.807470] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.808056] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.808662] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.809240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.809815] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.810391] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.810971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.811556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.812130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.820785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.821500] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.822208] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.822915] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.823648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.824367] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.825077] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.825808] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.826528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.827250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.827999] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.828754] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.829487] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.830190] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.830893] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.831593] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 29 19:28:05 superman-laptop NetworkManager: <debug> [1193700485.832305] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: Successfully dropped root privileges.
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: avahi-daemon 0.6.20 starting up.
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: Successfully called chroot().
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: Successfully dropped remaining capabilities.
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: No service file found in /etc/avahi/services.
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: Network interface enumeration completed.
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 29 19:28:06 superman-laptop avahi-daemon[5366]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 4153814688.
Oct 29 19:28:06 superman-laptop hcid[5402]: Bluetooth HCI daemon
Oct 29 19:28:06 superman-laptop hcid[5402]: Starting SDP server
Oct 29 19:28:06 superman-laptop hcid[5402]: Created local server at unix:abstract=/var/run/dbus-cwhNvwAEGe,guid=7a9c062c2aa1956f6884470047266c86
Oct 29 19:28:06 superman-laptop audio[5414]: Bluetooth Audio daemon
Oct 29 19:28:06 superman-laptop audio[5414]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 29 19:28:06 superman-laptop audio[5414]: Unix socket created: 5
Oct 29 19:28:06 superman-laptop input[5415]: Bluetooth Input daemon
Oct 29 19:28:06 superman-laptop input[5415]: Registered input manager path:/org/bluez/input
Oct 29 19:28:06 superman-laptop audio[5414]: add_service_record: got record id 0x10000
Oct 29 19:28:06 superman-laptop audio[5414]: add_service_record: got record id 0x10001
Oct 29 19:28:06 superman-laptop audio[5414]: Registered manager path:/org/bluez/audio
Oct 29 19:28:07 superman-laptop NetworkManager: <debug> [1193700487.720011] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 29 19:28:09 superman-laptop ntpd[5485]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 29 19:28:09 superman-laptop ntpd[5486]: precision = 1.000 usec
Oct 29 19:28:09 superman-laptop ntpd[5486]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 29 19:28:09 superman-laptop ntpd[5486]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 29 19:28:09 superman-laptop ntpd[5486]: Listening on interface #2 lo, ::1#123 Enabled
Oct 29 19:28:09 superman-laptop ntpd[5486]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 29 19:28:09 superman-laptop ntpd[5486]: kernel time sync status 0040
Oct 29 19:28:09 superman-laptop ntpd[5486]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: host name not found: ntp.ubuntu.com
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: host name not found: clock.tricity.wsu.edu
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: host name not found: wuarchive.wustl.edu
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: host name not found: gilbreth.ecn.purdue.edu
Oct 29 19:28:11 superman-laptop ntpd_initres[5528]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 29 19:28:33 superman-laptop hcid[5402]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 29 19:28:33 superman-laptop hcid[5402]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Forghani'. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, but NO valid key exists.  New key needed. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Forghani'. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Forghani' received. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, and a key exists.  No new key needed. 
Oct 29 19:28:41 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 19:28:42 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 29 19:28:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 29 19:28:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 29 19:28:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 29 19:28:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 29 19:28:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 29 19:28:43 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (6/10). 
Oct 29 19:28:43 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 466f726768616e69' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 19:28:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 19:28:45 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Forghani'. 
Oct 29 19:28:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 29 19:28:45 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 29 19:28:46 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 29 19:28:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 29 19:28:46 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 29 19:28:46 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 19:28:46 superman-laptop avahi-daemon[5366]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 19:28:48 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 29 19:28:51 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 29 19:28:51 superman-laptop dhclient: DHCPACK from 192.168.2.1
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 29 19:28:51 superman-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 29 19:28:51 superman-laptop dhclient: bound to 192.168.2.3 -- renewal in 953783116 seconds.
Oct 29 19:28:51 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>    address 192.168.2.3 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>    broadcast 192.168.2.255 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>    gateway 192.168.2.1 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>    nameserver 192.168.2.1 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>    nameserver 192.168.10.1 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>    domain name 'Forghani1' 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 29 19:28:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Withdrawing address record for 192.168.2.3 on eth1.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 19:28:51 superman-laptop avahi-daemon[5366]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 29 19:28:52 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 29 19:28:52 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 29 19:28:52 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 29 19:28:52 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 29 19:28:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 29 19:28:53 superman-laptop avahi-daemon[5366]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 19:29:23 superman-laptop ntpdate[6006]: can't find host clock.tricity.wsu.edu 
Oct 29 19:29:53 superman-laptop ntpdate[6006]: the NTP socket is in use, exiting
Oct 29 19:33:10 superman-laptop ntpd[5486]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 29 19:33:10 superman-laptop ntpd[5486]: Listening on interface #5 eth1, 192.168.2.3#123 Enabled
Oct 29 20:09:05 superman-laptop init: tty4 main process (4454) killed by TERM signal
Oct 29 20:09:05 superman-laptop init: tty5 main process (4455) killed by TERM signal
Oct 29 20:09:05 superman-laptop init: tty2 main process (4459) killed by TERM signal
Oct 29 20:09:05 superman-laptop init: tty3 main process (4460) killed by TERM signal
Oct 29 20:09:05 superman-laptop init: tty1 main process (4461) killed by TERM signal
Oct 29 20:09:05 superman-laptop init: tty6 main process (4462) killed by TERM signal
Oct 29 20:09:06 superman-laptop avahi-daemon[5366]: Got SIGTERM, quitting.
Oct 29 20:09:06 superman-laptop avahi-daemon[5366]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 20:09:08 superman-laptop rpc.statd[4327]: Caught signal 15, un-registering and exiting.
Oct 29 20:09:10 superman-laptop mountd[5178]: Caught signal 15, un-registering and exiting.
Oct 29 20:31:11 superman-laptop NetworkManager: <info>  starting... 
Oct 29 20:31:11 superman-laptop NetworkManager: <debug> [1193704271.789428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.082784] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.083415] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.083876] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.084982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.085816] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.086219] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.145589] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.146161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.146536] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.146972] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.147982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.148808] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.149604] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.150569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.151020] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.151455] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.151891] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.152351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.152793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.153254] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.153677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.154100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.154522] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.154943] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.155364] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.155786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.156207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.156628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.157063] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.157498] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.157948] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.158863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.159298] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.159748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.201902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.202409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.202849] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.203334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.203909] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.204353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.204822] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.205281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.205750] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.206245] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.206704] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.208793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.209233] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.209663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.210133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.210680] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.211134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.211588] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.212009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.212427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.212863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.213291] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.213712] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.214129] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.214546] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.214969] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.215400] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.215827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.216295] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.216743] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.284841] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 29 20:31:12 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.883261] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.883974] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.884579] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.893247] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.893836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.894420] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.895103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.895688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.896267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.896849] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.897449] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.898043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.898630] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.899259] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.899870] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.900492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.901091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.901679] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.902267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.902879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.903476] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.904061] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.904647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.905272] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.905869] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.906485] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.907056] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.907631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.908206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 29 20:31:12 superman-laptop NetworkManager: <debug> [1193704272.908821] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: Successfully dropped root privileges.
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: avahi-daemon 0.6.20 starting up.
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: Successfully called chroot().
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: Successfully dropped remaining capabilities.
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: No service file found in /etc/avahi/services.
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: Network interface enumeration completed.
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 29 20:31:13 superman-laptop avahi-daemon[5297]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 487130892.
Oct 29 20:31:13 superman-laptop hcid[5333]: Bluetooth HCI daemon
Oct 29 20:31:13 superman-laptop hcid[5333]: Starting SDP server
Oct 29 20:31:13 superman-laptop hcid[5333]: Created local server at unix:abstract=/var/run/dbus-37uwREG1CV,guid=df2b177c1c0560318ee7b00047267b51
Oct 29 20:31:14 superman-laptop audio[5345]: Bluetooth Audio daemon
Oct 29 20:31:14 superman-laptop audio[5345]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 29 20:31:14 superman-laptop audio[5345]: Unix socket created: 5
Oct 29 20:31:14 superman-laptop input[5346]: Bluetooth Input daemon
Oct 29 20:31:14 superman-laptop input[5346]: Registered input manager path:/org/bluez/input
Oct 29 20:31:14 superman-laptop audio[5345]: add_service_record: got record id 0x10000
Oct 29 20:31:14 superman-laptop audio[5345]: add_service_record: got record id 0x10001
Oct 29 20:31:14 superman-laptop audio[5345]: Registered manager path:/org/bluez/audio
Oct 29 20:31:14 superman-laptop NetworkManager: <debug> [1193704274.769039] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 29 20:31:16 superman-laptop ntpd[5416]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 29 20:31:16 superman-laptop ntpd[5417]: precision = 1.000 usec
Oct 29 20:31:16 superman-laptop ntpd[5417]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 29 20:31:16 superman-laptop ntpd[5417]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 29 20:31:16 superman-laptop ntpd[5417]: Listening on interface #2 lo, ::1#123 Enabled
Oct 29 20:31:16 superman-laptop ntpd[5417]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 29 20:31:16 superman-laptop ntpd[5417]: kernel time sync status 0040
Oct 29 20:31:16 superman-laptop ntpd[5417]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: host name not found: ntp.ubuntu.com
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: host name not found: clock.tricity.wsu.edu
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: host name not found: wuarchive.wustl.edu
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: host name not found: gilbreth.ecn.purdue.edu
Oct 29 20:31:18 superman-laptop ntpd_initres[5475]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 29 20:31:40 superman-laptop hcid[5333]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 29 20:31:40 superman-laptop hcid[5333]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Forghani'. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, but NO valid key exists.  New key needed. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Forghani'. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Forghani' received. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 29 20:31:51 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, and a key exists.  No new key needed. 
Oct 29 20:31:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 29 20:31:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 29 20:31:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 29 20:31:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 29 20:31:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 29 20:31:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 466f726768616e69' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 29 20:31:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 29 20:31:54 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 20:31:54 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Forghani'. 
Oct 29 20:31:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 29 20:31:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 29 20:31:55 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 29 20:31:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 29 20:31:55 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 29 20:31:55 superman-laptop avahi-daemon[5297]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 20:31:56 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 29 20:31:59 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 29 20:31:59 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 29 20:31:59 superman-laptop dhclient: DHCPACK from 192.168.2.1
Oct 29 20:31:59 superman-laptop avahi-daemon[5297]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 20:31:59 superman-laptop avahi-daemon[5297]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 20:31:59 superman-laptop avahi-daemon[5297]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 29 20:31:59 superman-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 29 20:31:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 29 20:31:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 29 20:31:59 superman-laptop dhclient: bound to 192.168.2.3 -- renewal in 953779328 seconds.
Oct 29 20:32:00 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>    address 192.168.2.3 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>    broadcast 192.168.2.255 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>    gateway 192.168.2.1 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>    nameserver 192.168.2.1 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>    nameserver 192.168.10.1 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>    domain name 'Forghani1' 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 29 20:32:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 29 20:32:00 superman-laptop avahi-daemon[5297]: Withdrawing address record for 192.168.2.3 on eth1.
Oct 29 20:32:00 superman-laptop avahi-daemon[5297]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 20:32:00 superman-laptop avahi-daemon[5297]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 29 20:32:00 superman-laptop avahi-daemon[5297]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 29 20:32:00 superman-laptop avahi-daemon[5297]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 20:32:00 superman-laptop avahi-daemon[5297]: New relevant interface eth1.IPv4 for mDNS.
Oct 29 20:32:00 superman-laptop avahi-daemon[5297]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Oct 29 20:32:01 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 29 20:32:01 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 29 20:32:01 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 29 20:32:01 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 29 20:32:01 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 29 20:32:02 superman-laptop avahi-daemon[5297]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 29 20:32:32 superman-laptop ntpdate[5924]: can't find host clock.tricity.wsu.edu 
Oct 29 20:33:02 superman-laptop ntpdate[5924]: the NTP socket is in use, exiting
Oct 29 20:36:17 superman-laptop ntpd[5417]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 29 20:36:17 superman-laptop ntpd[5417]: Listening on interface #5 eth1, 192.168.2.3#123 Enabled
Oct 29 21:23:42 superman-laptop init: tty4 main process (4384) killed by TERM signal
Oct 29 21:23:42 superman-laptop init: tty5 main process (4385) killed by TERM signal
Oct 29 21:23:42 superman-laptop init: tty2 main process (4387) killed by TERM signal
Oct 29 21:23:42 superman-laptop init: tty3 main process (4389) killed by TERM signal
Oct 29 21:23:42 superman-laptop init: tty1 main process (4391) killed by TERM signal
Oct 29 21:23:42 superman-laptop init: tty6 main process (4392) killed by TERM signal
Oct 29 21:23:42 superman-laptop avahi-daemon[5297]: Got SIGTERM, quitting.
Oct 29 21:23:42 superman-laptop avahi-daemon[5297]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Oct 29 21:23:44 superman-laptop rpc.statd[4257]: Caught signal 15, un-registering and exiting.
Oct 29 21:23:46 superman-laptop mountd[5109]: Caught signal 15, un-registering and exiting.
Oct 30 08:52:50 superman-laptop NetworkManager: <info>  starting... 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.345420] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.560034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.560663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.561277] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.562868] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.563639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.623012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.624085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.624536] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.624962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.625529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.626194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.626580] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.626950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.627319] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.627692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.628063] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.628463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.628827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.629189] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.629549] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.629929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.630297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.630660] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.631029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.631409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.632286] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.632655] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.633024] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.633405] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.634252] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.634619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.634988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.635369] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.685288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.685896] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.686265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.686620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.686973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.687323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.687664] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.688006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.688352] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.688695] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.689037] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.689434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.689778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.690139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.690486] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.690864] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.691217] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.693287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.694699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.695322] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.695738] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.696144] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.696548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.696953] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.697355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.697762] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.698210] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.698607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.699001] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.699398] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.699893] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.700301] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 30 08:52:50 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 30 08:52:50 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 08:52:50 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 08:52:50 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 30 08:52:50 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 30 08:52:50 superman-laptop NetworkManager: <debug> [1193748770.768335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 30 08:52:51 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 08:52:51 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 08:52:51 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 30 08:52:51 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.347766] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.348531] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.348971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.349412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.349859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.350323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.350767] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.351200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.351631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.352087] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.352516] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.352952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.353388] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.353845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.363207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.363683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.364128] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.364568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.365006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.365443] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.365918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.366357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.367597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.368804] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.369270] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.369700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.370146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.370572] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 30 08:52:51 superman-laptop NetworkManager: <debug> [1193748771.371022] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: Successfully dropped root privileges.
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: avahi-daemon 0.6.20 starting up.
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: Successfully called chroot().
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: Successfully dropped remaining capabilities.
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: No service file found in /etc/avahi/services.
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: Network interface enumeration completed.
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 30 08:52:52 superman-laptop avahi-daemon[5364]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 4076917942.
Oct 30 08:52:52 superman-laptop hcid[5400]: Bluetooth HCI daemon
Oct 30 08:52:52 superman-laptop hcid[5400]: Starting SDP server
Oct 30 08:52:52 superman-laptop hcid[5400]: Created local server at unix:abstract=/var/run/dbus-q6IdOuhKWU,guid=6fe9a9fa9e431dcb9efbf80047272924
Oct 30 08:52:52 superman-laptop audio[5412]: Bluetooth Audio daemon
Oct 30 08:52:52 superman-laptop audio[5412]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 30 08:52:52 superman-laptop audio[5412]: Unix socket created: 5
Oct 30 08:52:52 superman-laptop input[5413]: Bluetooth Input daemon
Oct 30 08:52:52 superman-laptop input[5413]: Registered input manager path:/org/bluez/input
Oct 30 08:52:52 superman-laptop audio[5412]: add_service_record: got record id 0x10000
Oct 30 08:52:52 superman-laptop audio[5412]: add_service_record: got record id 0x10001
Oct 30 08:52:52 superman-laptop audio[5412]: Registered manager path:/org/bluez/audio
Oct 30 08:52:53 superman-laptop NetworkManager: <debug> [1193748773.334334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 30 08:52:55 superman-laptop ntpd[5483]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 30 08:52:55 superman-laptop ntpd[5484]: precision = 1.000 usec
Oct 30 08:52:55 superman-laptop ntpd[5484]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 30 08:52:55 superman-laptop ntpd[5484]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 30 08:52:55 superman-laptop ntpd[5484]: Listening on interface #2 lo, ::1#123 Enabled
Oct 30 08:52:55 superman-laptop ntpd[5484]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 30 08:52:55 superman-laptop ntpd[5484]: kernel time sync status 0040
Oct 30 08:52:55 superman-laptop ntpd[5484]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: host name not found: ntp.ubuntu.com
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: host name not found: clock.tricity.wsu.edu
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: host name not found: wuarchive.wustl.edu
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: host name not found: gilbreth.ecn.purdue.edu
Oct 30 08:52:57 superman-laptop ntpd_initres[5539]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 30 08:53:12 superman-laptop hcid[5400]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 30 08:53:12 superman-laptop hcid[5400]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 08:53:15 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:53:17 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 08:53:18 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 30 08:53:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 08:53:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 08:53:19 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 08:53:19 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 08:53:19 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 08:53:20 superman-laptop avahi-daemon[5364]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:20 superman-laptop avahi-daemon[5364]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:20 superman-laptop avahi-daemon[5364]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 08:53:20 superman-laptop avahi-daemon[5364]: Registering new address record for 2002:96d8:e0b3:a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:21 superman-laptop avahi-daemon[5364]: Registering new address record for 2002:96d8:e122:a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:21 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 08:53:22 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 08:53:22 superman-laptop dhclient: DHCPNAK from 150.216.226.254
Oct 30 08:53:22 superman-laptop avahi-autoipd(eth1)[5897]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 30 08:53:22 superman-laptop avahi-autoipd(eth1)[5897]: Successfully called chroot().
Oct 30 08:53:22 superman-laptop avahi-autoipd(eth1)[5897]: Successfully dropped root privileges.
Oct 30 08:53:22 superman-laptop avahi-autoipd(eth1)[5897]: Starting with address 169.254.3.94
Oct 30 08:53:23 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 08:53:27 superman-laptop avahi-autoipd(eth1)[5897]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 30 08:53:27 superman-laptop avahi-daemon[5364]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 30 08:53:27 superman-laptop avahi-daemon[5364]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 08:53:27 superman-laptop avahi-daemon[5364]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 30 08:53:31 superman-laptop avahi-autoipd(eth1)[5897]: Successfully claimed IP address 169.254.3.94
Oct 30 08:53:31 superman-laptop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth1 
Oct 30 08:53:31 superman-laptop avahi-autoipd(eth1)[5897]: Got SIGTERM, quitting.
Oct 30 08:53:31 superman-laptop avahi-autoipd(eth1)[5897]: Callout STOP, address 169.254.3.94 on interface eth1
Oct 30 08:53:31 superman-laptop avahi-daemon[5364]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 30 08:53:31 superman-laptop avahi-daemon[5364]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 30 08:53:31 superman-laptop avahi-daemon[5364]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 08:53:31 superman-laptop avahi-autoipd(eth1)[5898]: client: RTNETLINK answers: No such process
Oct 30 08:53:33 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct 30 08:53:33 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 08:53:33 superman-laptop dhclient: DHCPOFFER from 150.216.226.254
Oct 30 08:53:33 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 08:53:34 superman-laptop dhclient: DHCPACK from 150.216.226.254
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Registering new address record for 150.216.175.134 on eth1.IPv4.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Withdrawing address record for 150.216.175.134 on eth1.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Registering new address record for 150.216.175.134 on eth1.IPv4.
Oct 30 08:53:34 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 30 08:53:34 superman-laptop dhclient: bound to 150.216.175.134 -- renewal in 1605 seconds.
Oct 30 08:53:34 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>    address 150.216.175.134 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>    broadcast 150.216.175.255 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>    gateway 150.216.175.254 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 08:53:34 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Withdrawing address record for 150.216.175.134 on eth1.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Withdrawing address record for 2002:96d8:e122:a:216:ceff:fe37:332 on eth1.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Withdrawing address record for 2002:96d8:e0b3:a:216:ceff:fe37:332 on eth1.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 08:53:34 superman-laptop avahi-daemon[5364]: Registering new address record for 150.216.175.134 on eth1.IPv4.
Oct 30 08:53:35 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 08:53:35 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 08:53:35 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 30 08:53:35 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 08:53:35 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 30 08:53:35 superman-laptop ntpdate[6070]: can't find host clock.tricity.wsu.edu 
Oct 30 08:53:35 superman-laptop ntpdate[6070]: the NTP socket is in use, exiting
Oct 30 08:53:36 superman-laptop avahi-daemon[5364]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:38 superman-laptop avahi-daemon[5364]: Registering new address record for 2002:96d8:e122:a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:38 superman-laptop avahi-daemon[5364]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 08:53:38 superman-laptop avahi-daemon[5364]: Registering new address record for 2002:96d8:e0b3:a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:53:38 superman-laptop avahi-daemon[5364]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:56:53 superman-laptop NetworkManager: <debug> [1193749013.854230] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A0:00 to 00:17:0F:8C:D8:40 on wireless network 'taho' 
Oct 30 08:56:53 superman-laptop NetworkManager: <debug> [1193749013.866574] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 08:57:03 superman-laptop NetworkManager: <debug> [1193749023.854176] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:A0:00 to 00:17:0F:8C:D8:40 on wireless network 'taho' 
Oct 30 08:57:56 superman-laptop ntpd[5484]: Listening on interface #4 eth1, 2002:96d8:e0b3:a:216:ceff:fe37:332#123 Enabled
Oct 30 08:57:56 superman-laptop ntpd[5484]: Listening on interface #5 eth1, fec0::a:216:ceff:fe37:332#123 Enabled
Oct 30 08:57:56 superman-laptop ntpd[5484]: Listening on interface #6 eth1, 2002:96d8:e122:a:216:ceff:fe37:332#123 Enabled
Oct 30 08:57:56 superman-laptop ntpd[5484]: Listening on interface #7 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 30 08:57:56 superman-laptop ntpd[5484]: Listening on interface #8 eth1, 150.216.175.134#123 Enabled
Oct 30 08:58:01 superman-laptop NetworkManager: <debug> [1193749081.133690] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'taho' 
Oct 30 08:58:01 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / taho 
Oct 30 08:58:01 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 08:58:01 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5863
Oct 30 08:58:01 superman-laptop dhclient: killed old client process, removed PID file
Oct 30 08:58:01 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Oct 30 08:58:01 superman-laptop avahi-daemon[5364]: Withdrawing address record for 150.216.175.134 on eth1.
Oct 30 08:58:01 superman-laptop avahi-daemon[5364]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:58:01 superman-laptop avahi-daemon[5364]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:02 superman-laptop avahi-daemon[5364]: Withdrawing address record for 2002:96d8:e0b3:a:216:ceff:fe37:332 on eth1.
Oct 30 08:58:02 superman-laptop avahi-daemon[5364]: Withdrawing address record for 2002:96d8:e122:a:216:ceff:fe37:332 on eth1.
Oct 30 08:58:02 superman-laptop avahi-daemon[5364]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 08:58:02 superman-laptop avahi-daemon[5364]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:02 superman-laptop avahi-daemon[5364]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 08:58:02 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 08:58:03 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 08:58:04 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 30 08:58:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 08:58:04 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 08:58:05 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 08:58:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 08:58:05 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 08:58:05 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Oct 30 08:58:05 superman-laptop avahi-daemon[5364]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:05 superman-laptop NetworkManager: <debug> [1193749085.886184] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:8C:D8:40 to 00:17:0F:8C:A0:00 on wireless network 'taho' 
Oct 30 08:58:05 superman-laptop NetworkManager: <debug> [1193749085.888721] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 08:58:05 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 08:58:06 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 08:58:07 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 30 08:58:07 superman-laptop avahi-daemon[5364]: Registering new address record for 2002:96d8:e0b3:a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:07 superman-laptop avahi-daemon[5364]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 08:58:08 superman-laptop avahi-daemon[5364]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:08 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 08:58:12 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 30 08:58:12 superman-laptop dhclient: DHCPOFFER from 150.216.226.254
Oct 30 08:58:12 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 08:58:12 superman-laptop dhclient: DHCPACK from 150.216.226.254
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Registering new address record for 150.216.175.134 on eth1.IPv4.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Withdrawing address record for 150.216.175.134 on eth1.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Registering new address record for 150.216.175.134 on eth1.IPv4.
Oct 30 08:58:12 superman-laptop dhclient: bound to 150.216.175.134 -- renewal in 1772 seconds.
Oct 30 08:58:12 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>    address 150.216.175.134 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>    broadcast 150.216.175.255 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>    gateway 150.216.175.254 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 08:58:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Withdrawing address record for 150.216.175.134 on eth1.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Withdrawing address record for 2002:96d8:e0b3:a:216:ceff:fe37:332 on eth1.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 08:58:12 superman-laptop avahi-daemon[5364]: Registering new address record for 150.216.175.134 on eth1.IPv4.
Oct 30 08:58:13 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 08:58:13 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 08:58:13 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 30 08:58:13 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 30 08:58:13 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 08:58:13 superman-laptop NetworkManager: <debug> [1193749093.155626] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 08:58:13 superman-laptop ntpdate[6276]: can't find host clock.tricity.wsu.edu 
Oct 30 08:58:13 superman-laptop ntpdate[6276]: the NTP socket is in use, exiting
Oct 30 08:58:14 superman-laptop avahi-daemon[5364]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:16 superman-laptop avahi-daemon[5364]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:16 superman-laptop avahi-daemon[5364]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 08:58:17 superman-laptop avahi-daemon[5364]: Registering new address record for 2002:96d8:e0b3:a:216:ceff:fe37:332 on eth1.*.
Oct 30 08:58:17 superman-laptop avahi-daemon[5364]: Registering new address record for 2002:96d8:e122:a:216:ceff:fe37:332 on eth1.*.
Oct 30 09:04:20 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:04:21 superman-laptop last message repeated 5 times
Oct 30 09:04:21 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62009 on interface 'eth1.0'
Oct 30 09:04:22 superman-laptop last message repeated 3 times
Oct 30 09:04:24 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62008 on interface 'eth1.0'
Oct 30 09:04:24 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62009 on interface 'eth1.0'
Oct 30 09:04:37 superman-laptop last message repeated 3 times
Oct 30 09:04:52 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62008 on interface 'eth1.0'
Oct 30 09:04:52 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62009 on interface 'eth1.0'
Oct 30 09:05:16 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:05:33 superman-laptop last message repeated 9 times
Oct 30 09:05:34 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62009 on interface 'eth1.0'
Oct 30 09:05:49 superman-laptop last message repeated 4 times
Oct 30 09:09:16 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:09:16 superman-laptop last message repeated 4 times
Oct 30 09:09:16 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62030 on interface 'eth1.0'
Oct 30 09:09:17 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62031 on interface 'eth1.0'
Oct 30 09:09:18 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62030 on interface 'eth1.0'
Oct 30 09:09:18 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62031 on interface 'eth1.0'
Oct 30 09:09:20 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62030 on interface 'eth1.0'
Oct 30 09:09:20 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62031 on interface 'eth1.0'
Oct 30 09:09:38 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:09:38 superman-laptop last message repeated 4 times
Oct 30 09:14:53 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:14:55 superman-laptop last message repeated 8 times
Oct 30 09:14:55 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62061 on interface 'eth1.0'
Oct 30 09:14:55 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62062 on interface 'eth1.0'
Oct 30 09:14:56 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62061 on interface 'eth1.0'
Oct 30 09:14:56 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62062 on interface 'eth1.0'
Oct 30 09:15:26 superman-laptop last message repeated 6 times
Oct 30 09:16:12 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:16:13 superman-laptop last message repeated 3 times
Oct 30 09:16:13 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62062 on interface 'eth1.0'
Oct 30 09:16:44 superman-laptop last message repeated 8 times
Oct 30 09:17:16 superman-laptop last message repeated 3 times
Oct 30 09:18:34 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62061 on interface 'eth1.0'
Oct 30 09:18:34 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62062 on interface 'eth1.0'
Oct 30 09:18:34 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:19:18 superman-laptop last message repeated 14 times
Oct 30 09:19:19 superman-laptop last message repeated 5 times
Oct 30 09:19:19 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62062 on interface 'eth1.0'
Oct 30 09:19:20 superman-laptop last message repeated 2 times
Oct 30 09:19:21 superman-laptop avahi-daemon[5364]: Invalid legacy unicast query packet.
Oct 30 09:19:21 superman-laptop last message repeated 5 times
Oct 30 09:19:22 superman-laptop avahi-daemon[5364]: Recieved repsonse with invalid source port 62062 on interface 'eth1.0'
Oct 30 09:19:34 superman-laptop last message repeated 10 times
Oct 30 09:19:40 superman-laptop init: tty4 main process (4458) killed by TERM signal
Oct 30 09:19:40 superman-laptop init: tty5 main process (4459) killed by TERM signal
Oct 30 09:19:40 superman-laptop init: tty2 main process (4461) killed by TERM signal
Oct 30 09:19:40 superman-laptop init: tty3 main process (4463) killed by TERM signal
Oct 30 09:19:40 superman-laptop init: tty1 main process (4465) killed by TERM signal
Oct 30 09:19:40 superman-laptop init: tty6 main process (4466) killed by TERM signal
Oct 30 09:19:40 superman-laptop avahi-daemon[5364]: Got SIGTERM, quitting.
Oct 30 09:19:40 superman-laptop avahi-daemon[5364]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.175.134.
Oct 30 09:19:43 superman-laptop rpc.statd[4331]: Caught signal 15, un-registering and exiting.
Oct 30 09:19:45 superman-laptop mountd[5179]: Caught signal 15, un-registering and exiting.
Oct 30 11:59:25 superman-laptop NetworkManager: <info>  starting... 
Oct 30 11:59:25 superman-laptop NetworkManager: <debug> [1193759965.783591] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.051699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.052292] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.109990] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.110924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.111574] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.112603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.113497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.113875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.114248] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.114632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.115002] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.115365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.115727] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.116089] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.116451] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.116812] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.117173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.117533] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.117894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.118254] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.118632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.119394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.119768] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.120153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.121057] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.121983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.122388] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.122759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.123513] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.123880] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.124236] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.124603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.125060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.125417] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.166599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.167031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.167409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.167811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.168195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.168555] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.168930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.169289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.169647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.170006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.170381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.170830] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.172917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.173553] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.173989] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.174443] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.174885] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.175322] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.175757] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.176190] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.176620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.177047] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.177481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.177936] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.178378] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.178811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.179242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.179684] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.180111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.180553] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.248648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 30 11:59:26 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.860459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.861038] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.861480] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.861915] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.862349] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.862796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.863229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.863662] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.864118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.864551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.864983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.865430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.865862] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.866296] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.874792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.875338] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.875761] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.876178] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.876615] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.877034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.877451] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.877867] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.878285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.878731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.879145] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.879578] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.879994] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.880409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.880824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 30 11:59:26 superman-laptop NetworkManager: <debug> [1193759966.881250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: Successfully dropped root privileges.
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: avahi-daemon 0.6.20 starting up.
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: Successfully called chroot().
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: Successfully dropped remaining capabilities.
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: No service file found in /etc/avahi/services.
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: Network interface enumeration completed.
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 30 11:59:27 superman-laptop avahi-daemon[5323]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 2629095806.
Oct 30 11:59:28 superman-laptop hcid[5359]: Bluetooth HCI daemon
Oct 30 11:59:28 superman-laptop hcid[5359]: Starting SDP server
Oct 30 11:59:28 superman-laptop hcid[5359]: Created local server at unix:abstract=/var/run/dbus-EBo9YxiGQa,guid=e941a1af4ca25364fe5d6a00472754e0
Oct 30 11:59:28 superman-laptop audio[5371]: Bluetooth Audio daemon
Oct 30 11:59:28 superman-laptop audio[5371]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 30 11:59:28 superman-laptop audio[5371]: Unix socket created: 5
Oct 30 11:59:28 superman-laptop input[5372]: Bluetooth Input daemon
Oct 30 11:59:28 superman-laptop input[5372]: Registered input manager path:/org/bluez/input
Oct 30 11:59:28 superman-laptop audio[5371]: add_service_record: got record id 0x10000
Oct 30 11:59:28 superman-laptop audio[5371]: add_service_record: got record id 0x10001
Oct 30 11:59:28 superman-laptop audio[5371]: Registered manager path:/org/bluez/audio
Oct 30 11:59:28 superman-laptop NetworkManager: <debug> [1193759968.922755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 30 11:59:30 superman-laptop ntpd[5442]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 30 11:59:30 superman-laptop ntpd[5443]: precision = 1.000 usec
Oct 30 11:59:30 superman-laptop ntpd[5443]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 30 11:59:30 superman-laptop ntpd[5443]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 30 11:59:30 superman-laptop ntpd[5443]: Listening on interface #2 lo, ::1#123 Enabled
Oct 30 11:59:30 superman-laptop ntpd[5443]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 30 11:59:30 superman-laptop ntpd[5443]: kernel time sync status 0040
Oct 30 11:59:30 superman-laptop ntpd[5443]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: host name not found: ntp.ubuntu.com
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: host name not found: clock.tricity.wsu.edu
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: host name not found: wuarchive.wustl.edu
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: host name not found: gilbreth.ecn.purdue.edu
Oct 30 11:59:33 superman-laptop ntpd_initres[5521]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 30 12:01:44 superman-laptop hcid[5359]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 30 12:01:44 superman-laptop hcid[5359]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 12:01:51 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 12:01:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 12:01:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 12:01:52 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 12:01:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 12:01:54 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 30 12:01:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 12:01:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 12:01:55 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 12:01:55 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 12:01:55 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 12:01:56 superman-laptop avahi-daemon[5323]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 12:01:57 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 12:01:59 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 12:01:59 superman-laptop dhclient: DHCPOFFER from 150.216.226.254
Oct 30 12:01:59 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 12:01:59 superman-laptop dhclient: DHCPACK from 150.216.226.254
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 12:01:59 superman-laptop dhclient: bound to 150.216.230.28 -- renewal in 1751 seconds.
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>    address 150.216.230.28 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>    broadcast 150.216.230.255 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>    gateway 150.216.230.254 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 12:01:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 12:01:59 superman-laptop avahi-daemon[5323]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 12:02:00 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 12:02:00 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 12:02:00 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 30 12:02:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 12:02:00 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 30 12:02:01 superman-laptop ntpdate[5932]: can't find host clock.tricity.wsu.edu 
Oct 30 12:02:01 superman-laptop ntpdate[5932]: the NTP socket is in use, exiting
Oct 30 12:02:01 superman-laptop avahi-daemon[5323]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 12:04:31 superman-laptop ntpd[5443]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 30 12:04:31 superman-laptop ntpd[5443]: Listening on interface #5 eth1, 150.216.230.28#123 Enabled
Oct 30 12:06:39 superman-laptop avahi-daemon[5323]: Registering new address record for fec0::5:216:ceff:fe37:332 on eth1.*.
Oct 30 12:06:39 superman-laptop avahi-daemon[5323]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 12:06:39 superman-laptop avahi-daemon[5323]: Registering new address record for 2002:96d8:e1a3:5:216:ceff:fe37:332 on eth1.*.
Oct 30 12:09:31 superman-laptop ntpd[5443]: Listening on interface #6 eth1, 2002:96d8:e1a3:5:216:ceff:fe37:332#123 Enabled
Oct 30 12:09:31 superman-laptop ntpd[5443]: Listening on interface #7 eth1, fec0::5:216:ceff:fe37:332#123 Enabled
Oct 30 12:14:50 superman-laptop avahi-daemon[5323]: Registering new address record for 2002:96d8:e122:a:216:ceff:fe37:332 on eth1.*.
Oct 30 12:14:50 superman-laptop avahi-daemon[5323]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 12:19:31 superman-laptop ntpd[5443]: Listening on interface #8 eth1, fec0::a:216:ceff:fe37:332#123 Enabled
Oct 30 12:19:31 superman-laptop ntpd[5443]: Listening on interface #9 eth1, 2002:96d8:e122:a:216:ceff:fe37:332#123 Enabled
Oct 30 12:29:49 superman-laptop avahi-daemon[5323]: Registering new address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.*.
Oct 30 12:31:10 superman-laptop dhclient: DHCPREQUEST on eth1 to 150.216.226.254 port 67
Oct 30 12:31:10 superman-laptop dhclient: DHCPACK from 150.216.243.174
Oct 30 12:31:10 superman-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Oct 30 12:31:10 superman-laptop dhclient: bound to 150.216.230.28 -- renewal in 1501 seconds.
Oct 30 12:34:31 superman-laptop ntpd[5443]: Listening on interface #10 eth1, 2002:96d8:e63c:a:216:ceff:fe37:332#123 Enabled
Oct 30 12:36:04 superman-laptop init: tty4 main process (4377) killed by TERM signal
Oct 30 12:36:04 superman-laptop init: tty3 main process (4382) killed by TERM signal
Oct 30 12:36:04 superman-laptop init: tty5 main process (4378) killed by TERM signal
Oct 30 12:36:04 superman-laptop init: tty1 main process (4384) killed by TERM signal
Oct 30 12:36:04 superman-laptop init: tty6 main process (4385) killed by TERM signal
Oct 30 12:36:04 superman-laptop init: tty2 main process (4380) killed by TERM signal
Oct 30 12:36:04 superman-laptop avahi-daemon[5323]: Got SIGTERM, quitting.
Oct 30 12:36:04 superman-laptop avahi-daemon[5323]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 12:36:06 superman-laptop rpc.statd[4250]: Caught signal 15, un-registering and exiting.
Oct 30 12:36:08 superman-laptop mountd[5136]: Caught signal 15, un-registering and exiting.
Oct 30 13:22:25 superman-laptop NetworkManager: <info>  starting... 
Oct 30 13:22:25 superman-laptop NetworkManager: <debug> [1193764945.737088] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.011795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.012662] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.014152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.014776] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.015265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.087187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.088984] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.090738] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.092898] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.094116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.094901] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.096071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.137938] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.138442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.138902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.139331] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.139750] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.140254] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.140680] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.141140] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.141558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.141972] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.142386] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.142822] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.143251] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.143671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.144170] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.144574] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.146583] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.147015] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.147442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.147864] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.148273] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.148778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.149210] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.149634] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.150062] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.150488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.150913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.151340] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.151764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.152207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.152631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.153123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.153550] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.154041] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.154499] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.154924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.155351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.155776] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.156195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.156620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.157068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.157504] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.157935] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.158368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.158797] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.159227] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.159656] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.160086] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.160516] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.160960] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.161403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.161832] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.229903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 30 13:22:26 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.848318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.848961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.849416] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.849849] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.850267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.850681] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.851096] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.851510] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.851924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.852338] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.852760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.853175] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.853587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.854031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.854462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.854877] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.855290] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.855722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.856134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.856558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.865183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.865838] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.866467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.867055] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.867645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.868257] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.868859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.869445] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.870029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 30 13:22:26 superman-laptop NetworkManager: <debug> [1193764946.870610] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: Successfully dropped root privileges.
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: avahi-daemon 0.6.20 starting up.
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: Successfully called chroot().
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: Successfully dropped remaining capabilities.
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: No service file found in /etc/avahi/services.
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: Network interface enumeration completed.
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 30 13:22:27 superman-laptop avahi-daemon[5327]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 701149353.
Oct 30 13:22:28 superman-laptop hcid[5363]: Bluetooth HCI daemon
Oct 30 13:22:28 superman-laptop hcid[5363]: Starting SDP server
Oct 30 13:22:28 superman-laptop hcid[5363]: Created local server at unix:abstract=/var/run/dbus-nawi2ZNlTD,guid=158195eaa59156da97ca950047276854
Oct 30 13:22:28 superman-laptop audio[5375]: Bluetooth Audio daemon
Oct 30 13:22:28 superman-laptop audio[5375]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 30 13:22:28 superman-laptop audio[5375]: Unix socket created: 5
Oct 30 13:22:28 superman-laptop input[5376]: Bluetooth Input daemon
Oct 30 13:22:28 superman-laptop input[5376]: Registered input manager path:/org/bluez/input
Oct 30 13:22:28 superman-laptop audio[5375]: add_service_record: got record id 0x10000
Oct 30 13:22:28 superman-laptop audio[5375]: add_service_record: got record id 0x10001
Oct 30 13:22:28 superman-laptop audio[5375]: Registered manager path:/org/bluez/audio
Oct 30 13:22:28 superman-laptop NetworkManager: <debug> [1193764948.718597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 30 13:22:31 superman-laptop ntpd[5446]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 30 13:22:31 superman-laptop ntpd[5447]: precision = 1.000 usec
Oct 30 13:22:31 superman-laptop ntpd[5447]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 30 13:22:31 superman-laptop ntpd[5447]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 30 13:22:31 superman-laptop ntpd[5447]: Listening on interface #2 lo, ::1#123 Enabled
Oct 30 13:22:31 superman-laptop ntpd[5447]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 30 13:22:31 superman-laptop ntpd[5447]: kernel time sync status 0040
Oct 30 13:22:31 superman-laptop ntpd[5447]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: host name not found: ntp.ubuntu.com
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: host name not found: clock.tricity.wsu.edu
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: host name not found: wuarchive.wustl.edu
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: host name not found: gilbreth.ecn.purdue.edu
Oct 30 13:22:33 superman-laptop ntpd_initres[5475]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 30 13:22:50 superman-laptop hcid[5363]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 30 13:22:50 superman-laptop hcid[5363]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 13:22:53 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (6/10). 
Oct 30 13:22:55 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 13:22:56 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 13:22:57 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 13:22:57 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 13:22:57 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 13:22:57 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:23:00 superman-laptop avahi-daemon[5327]: Registering new address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:23:00 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:23:00 superman-laptop avahi-daemon[5327]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:23:01 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:23:01 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 13:23:05 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 13:23:05 superman-laptop dhclient: DHCPACK from 150.216.226.254
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:23:05 superman-laptop dhclient: bound to 150.216.230.28 -- renewal in 1708 seconds.
Oct 30 13:23:05 superman-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>    address 150.216.230.28 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>    broadcast 150.216.230.255 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>    gateway 150.216.230.254 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 13:23:05 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Withdrawing address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:23:05 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:23:06 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 13:23:06 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 13:23:06 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 30 13:23:06 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 13:23:06 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 30 13:23:06 superman-laptop ntpdate[5963]: can't find host clock.tricity.wsu.edu 
Oct 30 13:23:07 superman-laptop ntpdate[5963]: the NTP socket is in use, exiting
Oct 30 13:23:08 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:23:09 superman-laptop avahi-daemon[5327]: Registering new address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:23:09 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:23:09 superman-laptop avahi-daemon[5327]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:24:04 superman-laptop NetworkManager: <debug> [1193765044.420955] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Oct 30 13:24:08 superman-laptop NetworkManager: <debug> [1193765048.420920] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Oct 30 13:24:16 superman-laptop NetworkManager: <debug> [1193765056.420910] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7D:50 to 00:17:0F:20:7B:B0 on wireless network 'taho' 
Oct 30 13:24:24 superman-laptop NetworkManager: <info>  eth1: link timed out. 
Oct 30 13:24:24 superman-laptop NetworkManager: <info>  SWITCH: found better connection 'eth1/taho' than current connection 'eth1/taho'.  same_ssid=1, have_link=0 
Oct 30 13:24:24 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Oct 30 13:24:24 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 13:24:24 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:24:24 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5809
Oct 30 13:24:24 superman-laptop dhclient: killed old client process, removed PID file
Oct 30 13:24:24 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Oct 30 13:24:24 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:24:24 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:24:24 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 13:24:25 superman-laptop avahi-daemon[5327]: Withdrawing address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.
Oct 30 13:24:25 superman-laptop avahi-daemon[5327]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 13:24:25 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:24:25 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Oct 30 13:24:25 superman-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Oct 30 13:24:26 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 13:24:26 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 13:24:26 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 13:24:32 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:24:43 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:24:44 superman-laptop NetworkManager: <debug> [1193765084.492763] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'taho' 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / taho 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 13:24:44 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 13:24:45 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 13:24:45 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant6^I' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:24:46 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 13:24:47 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:24:49 superman-laptop avahi-daemon[5327]: Registering new address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:24:49 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:24:49 superman-laptop avahi-daemon[5327]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:24:51 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:24:58 superman-laptop NetworkManager: <debug> [1193765098.132902] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Oct 30 13:24:58 superman-laptop NetworkManager: <debug> [1193765098.135088] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 13:24:58 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:24:59 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 30 13:24:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 13:24:59 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 13:25:00 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 13:25:00 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Oct 30 13:25:00 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 13:25:00 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 13:25:01 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 13:25:01 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 30 13:25:02 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:25:04 superman-laptop NetworkManager: <debug> [1193765104.317031] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Oct 30 13:25:04 superman-laptop NetworkManager: <debug> [1193765104.318917] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 13:25:04 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:25:06 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Oct 30 13:25:19 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct 30 13:25:27 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 30 13:25:32 superman-laptop dhclient: No DHCPOFFERS received.
Oct 30 13:25:32 superman-laptop dhclient: Trying recorded lease 192.168.2.2
Oct 30 13:25:32 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 13:25:32 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:25:32 superman-laptop avahi-daemon[5327]: Registering new address record for 192.168.2.2 on eth1.IPv4.
Oct 30 13:25:35 superman-laptop avahi-daemon[5327]: Withdrawing address record for 192.168.2.2 on eth1.
Oct 30 13:25:35 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 13:25:35 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:25:35 superman-laptop avahi-autoipd(eth1)[6122]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 30 13:25:35 superman-laptop avahi-autoipd(eth1)[6122]: Successfully called chroot().
Oct 30 13:25:35 superman-laptop avahi-autoipd(eth1)[6122]: Successfully dropped root privileges.
Oct 30 13:25:35 superman-laptop avahi-autoipd(eth1)[6122]: Starting with address 169.254.3.94
Oct 30 13:25:39 superman-laptop avahi-autoipd(eth1)[6122]: Callout BIND, address 169.254.3.94 on interface eth1
Oct 30 13:25:39 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 30 13:25:39 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:25:39 superman-laptop avahi-daemon[5327]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Oct 30 13:25:43 superman-laptop avahi-autoipd(eth1)[6122]: Successfully claimed IP address 169.254.3.94
Oct 30 13:25:43 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Oct 30 13:25:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Oct 30 13:25:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Oct 30 13:25:43 superman-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Oct 30 13:25:43 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Oct 30 13:25:43 superman-laptop dhclient: Trying recorded lease 192.168.2.4
Oct 30 13:25:43 superman-laptop avahi-autoipd(eth1)[6122]: A routable address has been configured.
Oct 30 13:25:43 superman-laptop avahi-autoipd(eth1)[6122]: Callout UNBIND, address 169.254.3.94 on interface eth1
Oct 30 13:25:43 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Oct 30 13:25:43 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Oct 30 13:25:43 superman-laptop avahi-daemon[5327]: Registering new address record for 192.168.2.4 on eth1.IPv4.
Oct 30 13:25:43 superman-laptop avahi-daemon[5327]: Withdrawing address record for 169.254.3.94 on eth1.
Oct 30 13:25:44 superman-laptop NetworkManager: <info>  Activation (eth1) failed for access point (taho) 
Oct 30 13:25:44 superman-laptop NetworkManager: <info>  Activation (eth1) failed. 
Oct 30 13:25:44 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:25:44 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6103
Oct 30 13:25:44 superman-laptop dhclient: killed old client process, removed PID file
Oct 30 13:25:44 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Oct 30 13:25:44 superman-laptop dhclient: send_packet: Network is unreachable
Oct 30 13:25:44 superman-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Oct 30 13:25:44 superman-laptop avahi-autoipd(eth1)[6122]: Got SIGTERM, quitting.
Oct 30 13:25:44 superman-laptop avahi-daemon[5327]: Withdrawing address record for 192.168.2.4 on eth1.
Oct 30 13:25:44 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Oct 30 13:25:44 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:25:45 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 30 13:25:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:45 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 30 13:25:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:45 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 30 13:25:45 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:45 superman-laptop avahi-daemon[5327]: Withdrawing address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.
Oct 30 13:25:45 superman-laptop avahi-daemon[5327]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 13:25:45 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:25:45 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:25:49 superman-laptop NetworkManager: <debug> [1193765149.299388] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'taho' 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / taho 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 13:25:49 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant9^I' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:50 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 13:25:51 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 30 13:25:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 13:25:51 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 13:25:51 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 13:25:52 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 13:25:52 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Oct 30 13:25:52 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 13:25:52 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 13:25:53 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:25:53 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 13:25:53 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct 30 13:25:53 superman-laptop avahi-autoipd(eth1)[6205]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 30 13:25:53 superman-laptop avahi-autoipd(eth1)[6205]: Successfully called chroot().
Oct 30 13:25:53 superman-laptop avahi-autoipd(eth1)[6205]: Successfully dropped root privileges.
Oct 30 13:25:53 superman-laptop avahi-autoipd(eth1)[6205]: Starting with address 169.254.3.94
Oct 30 13:25:54 superman-laptop dhclient: DHCPOFFER from 150.216.226.254
Oct 30 13:25:54 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 13:25:54 superman-laptop dhclient: DHCPACK from 150.216.226.254
Oct 30 13:25:54 superman-laptop avahi-autoipd(eth1)[6205]: Got SIGTERM, quitting.
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 30 13:25:54 superman-laptop dhclient: bound to 150.216.230.28 -- renewal in 1794 seconds.
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  Activation (eth1) failed for access point (taho) 
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  Activation (eth1) failed. 
Oct 30 13:25:54 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:25:54 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6190
Oct 30 13:25:54 superman-laptop dhclient: killed old client process, removed PID file
Oct 30 13:25:54 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:25:54 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:25:55 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 30 13:25:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:55 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 30 13:25:55 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:25:55 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 30 13:25:55 superman-laptop avahi-daemon[5327]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:25:55 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:25:55 superman-laptop avahi-daemon[5327]: Registering new address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:25:56 superman-laptop avahi-daemon[5327]: Withdrawing address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.
Oct 30 13:25:56 superman-laptop avahi-daemon[5327]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 13:26:07 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Oct 30 13:26:07 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'TERMINATE'.  Response: 'TIMEOUT[CLI]' 
Oct 30 13:26:07 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't terminate wpasupplicant cleanly. 
Oct 30 13:26:12 superman-laptop NetworkManager: <debug> [1193765172.683496] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'taho' 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / taho 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 13:26:12 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Oct 30 13:26:13 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 13:26:13 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 13:26:13 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Oct 30 13:26:13 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:26:13 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 13:26:14 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 13:26:14 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 13:26:15 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 13:26:15 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Oct 30 13:26:15 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 13:26:15 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 13:26:16 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct 30 13:26:16 superman-laptop dhclient: DHCPOFFER from 150.216.226.254
Oct 30 13:26:16 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:26:16 superman-laptop dhclient: DHCPACK from 150.216.226.254
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:26:16 superman-laptop dhclient: bound to 150.216.230.28 -- renewal in 1377 seconds.
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>    address 150.216.230.28 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>    broadcast 150.216.230.255 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>    gateway 150.216.230.254 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 13:26:16 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Withdrawing address record for fec0::a:216:ceff:fe37:332 on eth1.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 13:26:16 superman-laptop avahi-daemon[5327]: Registering new address record for 150.216.230.28 on eth1.IPv4.
Oct 30 13:26:17 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 13:26:17 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 13:26:17 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 30 13:26:17 superman-laptop NetworkManager: <debug> [1193765177.593588] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 13:26:17 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 30 13:26:17 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 13:26:17 superman-laptop ntpdate[6341]: can't find host clock.tricity.wsu.edu 
Oct 30 13:26:17 superman-laptop ntpdate[6341]: the NTP socket is in use, exiting
Oct 30 13:26:19 superman-laptop avahi-daemon[5327]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 13:26:19 superman-laptop avahi-daemon[5327]: Registering new address record for fec0::a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:26:19 superman-laptop avahi-daemon[5327]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 13:26:19 superman-laptop avahi-daemon[5327]: Registering new address record for 2002:96d8:e63c:a:216:ceff:fe37:332 on eth1.*.
Oct 30 13:26:56 superman-laptop NetworkManager: <debug> [1193765216.064916] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Oct 30 13:26:56 superman-laptop NetworkManager: <debug> [1193765216.066878] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 13:27:00 superman-laptop NetworkManager: <debug> [1193765220.064922] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Oct 30 13:27:00 superman-laptop NetworkManager: <debug> [1193765220.066903] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 13:27:12 superman-laptop NetworkManager: <debug> [1193765232.089075] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Oct 30 13:27:12 superman-laptop NetworkManager: <debug> [1193765232.091115] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'taho' 
Oct 30 13:27:32 superman-laptop ntpd[5447]: Listening on interface #4 eth1, fec0::a:216:ceff:fe37:332#123 Enabled
Oct 30 13:27:32 superman-laptop ntpd[5447]: Listening on interface #5 eth1, 2002:96d8:e63c:a:216:ceff:fe37:332#123 Enabled
Oct 30 13:27:32 superman-laptop ntpd[5447]: Listening on interface #6 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 30 13:27:32 superman-laptop ntpd[5447]: Listening on interface #7 eth1, 150.216.230.28#123 Enabled
Oct 30 13:27:58 superman-laptop NetworkManager: <debug> [1193765278.157309] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'taho' 
Oct 30 13:27:58 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / taho 
Oct 30 13:27:58 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 13:27:58 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6279
Oct 30 13:27:58 superman-laptop dhclient: killed old client process, removed PID file
Oct 30 13:27:58 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Oct 30 13:27:58 superman-laptop avahi-daemon[5327]: Withdrawing address record for 150.216.230.28 on eth1.
Oct 30 13:27:58 superman-laptop avahi-daemon[5327]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.230.28.
Oct 30 13:27:58 superman-laptop avahi-daemon[5327]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 13:27:59 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Oct 30 13:27:59 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:27:59 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Oct 30 13:28:09 superman-laptop init: tty4 main process (4415) killed by TERM signal
Oct 30 13:28:09 superman-laptop init: tty5 main process (4416) killed by TERM signal
Oct 30 13:28:09 superman-laptop init: tty2 main process (4420) killed by TERM signal
Oct 30 13:28:09 superman-laptop init: tty3 main process (4421) killed by TERM signal
Oct 30 13:28:09 superman-laptop init: tty1 main process (4422) killed by TERM signal
Oct 30 13:28:09 superman-laptop init: tty6 main process (4423) killed by TERM signal
Oct 30 13:28:10 superman-laptop avahi-daemon[5327]: Got SIGTERM, quitting.
Oct 30 13:28:11 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Oct 30 13:28:11 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'AP_SCAN 0'.  Response: 'TIMEOUT[CLI]' 
Oct 30 13:28:11 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't set AP_SCAN 0 
Oct 30 13:28:11 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Oct 30 13:28:11 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 13:28:11 superman-laptop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 11.  Generating backtrace... 
Oct 30 13:28:11 superman-laptop NetworkManager: ******************* START **********************************
Oct 30 13:28:11 superman-laptop NetworkManager: (no debugging symbols found)
Oct 30 13:28:11 superman-laptop NetworkManager: Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Oct 30 13:28:11 superman-laptop NetworkManager: (no debugging symbols found)
Oct 30 13:28:11 superman-laptop last message repeated 12 times
Oct 30 13:28:11 superman-laptop NetworkManager: [Thread debugging using libthread_db enabled]
Oct 30 13:28:11 superman-laptop NetworkManager: [New Thread -1212082512 (LWP 4846)]
Oct 30 13:28:11 superman-laptop NetworkManager: [New Thread -1228870768 (LWP 5792)]
Oct 30 13:28:11 superman-laptop NetworkManager: [New Thread -1220478064 (LWP 5163)]
Oct 30 13:28:11 superman-laptop NetworkManager: [New Thread -1212085360 (LWP 5044)]
Oct 30 13:28:11 superman-laptop NetworkManager: (no debugging symbols found)
Oct 30 13:28:11 superman-laptop last message repeated 4 times
Oct 30 13:28:11 superman-laptop NetworkManager: 0xffffe410 in __kernel_vsyscall ()
Oct 30 13:28:11 superman-laptop NetworkManager: ******************* END **********************************
Oct 30 13:28:12 superman-laptop rpc.statd[4288]: Caught signal 15, un-registering and exiting.
Oct 30 13:28:14 superman-laptop mountd[5139]: Caught signal 15, un-registering and exiting.
Oct 30 16:02:47 superman-laptop NetworkManager: <info>  starting... 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.637171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.923321] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.923829] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.924280] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.924722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.925171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.925538] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.925917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.997609] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.998383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 30 16:02:47 superman-laptop NetworkManager: <debug> [1193774567.999019] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.000297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.000859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.001303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.001768] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.002371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.002808] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.003238] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.003665] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.004093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.004555] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.004980] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.005403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.005840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.006263] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.006685] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.007108] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.007530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.007971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.008395] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.008833] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.009267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.009699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.010132] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.010569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.011005] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.011427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.011853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.012290] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.012748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.013181] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.013613] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.014071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.014502] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.014929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.015376] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.015807] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.016234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.016672] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.017093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.017524] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.017949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.018376] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.018804] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.019232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.019657] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.020085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.020527] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.020950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.021474] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.021995] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.022427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.022843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.023273] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.023688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.092634] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 30 16:02:48 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.765462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.766162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.766741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.767312] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.767886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.776532] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.777212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.777791] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.778370] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.778945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.779517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.780088] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.780676] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.781251] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.781824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.782399] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.782971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.783540] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.784108] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.784697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.785265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.785831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.786400] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.786968] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.787537] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.788132] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.788719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.789283] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.789848] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 30 16:02:48 superman-laptop NetworkManager: <debug> [1193774568.790422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: Successfully dropped root privileges.
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: avahi-daemon 0.6.20 starting up.
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: Successfully called chroot().
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: Successfully dropped remaining capabilities.
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: No service file found in /etc/avahi/services.
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: Network interface enumeration completed.
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 30 16:02:49 superman-laptop avahi-daemon[5373]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 3035746560.
Oct 30 16:02:49 superman-laptop hcid[5408]: Bluetooth HCI daemon
Oct 30 16:02:49 superman-laptop hcid[5408]: Starting SDP server
Oct 30 16:02:50 superman-laptop hcid[5408]: Created local server at unix:abstract=/var/run/dbus-EyHmU8qEcO,guid=aea99814b47eff64081ae40047278dea
Oct 30 16:02:50 superman-laptop audio[5420]: Bluetooth Audio daemon
Oct 30 16:02:50 superman-laptop audio[5420]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 30 16:02:50 superman-laptop audio[5420]: Unix socket created: 5
Oct 30 16:02:50 superman-laptop input[5421]: Bluetooth Input daemon
Oct 30 16:02:50 superman-laptop input[5421]: Registered input manager path:/org/bluez/input
Oct 30 16:02:50 superman-laptop audio[5420]: add_service_record: got record id 0x10000
Oct 30 16:02:50 superman-laptop audio[5420]: add_service_record: got record id 0x10001
Oct 30 16:02:50 superman-laptop audio[5420]: Registered manager path:/org/bluez/audio
Oct 30 16:02:50 superman-laptop NetworkManager: <debug> [1193774570.600882] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 30 16:02:52 superman-laptop ntpd[5491]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 30 16:02:52 superman-laptop ntpd[5492]: precision = 1.000 usec
Oct 30 16:02:52 superman-laptop ntpd[5492]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 30 16:02:52 superman-laptop ntpd[5492]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 30 16:02:52 superman-laptop ntpd[5492]: Listening on interface #2 lo, ::1#123 Enabled
Oct 30 16:02:52 superman-laptop ntpd[5492]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 30 16:02:52 superman-laptop ntpd[5492]: kernel time sync status 0040
Oct 30 16:02:52 superman-laptop ntpd[5492]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: host name not found: ntp.ubuntu.com
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: host name not found: clock.tricity.wsu.edu
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: host name not found: wuarchive.wustl.edu
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: host name not found: gilbreth.ecn.purdue.edu
Oct 30 16:02:54 superman-laptop ntpd_initres[5520]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 30 16:03:11 superman-laptop hcid[5408]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 30 16:03:11 superman-laptop hcid[5408]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Forghani'. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, but NO valid key exists.  New key needed. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Forghani'. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Forghani' received. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 16:03:18 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, and a key exists.  No new key needed. 
Oct 30 16:03:20 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 16:03:20 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 16:03:20 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 30 16:03:20 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 466f726768616e69' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 16:03:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 16:03:22 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Forghani'. 
Oct 30 16:03:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 16:03:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 16:03:23 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 16:03:23 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 16:03:23 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 16:03:23 superman-laptop avahi-daemon[5373]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 16:03:25 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 16:03:27 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 16:03:27 superman-laptop dhclient: DHCPOFFER from 192.168.2.1
Oct 30 16:03:27 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 16:03:27 superman-laptop dhclient: DHCPACK from 192.168.2.1
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Registering new address record for 192.168.2.2 on eth1.IPv4.
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 16:03:27 superman-laptop dhclient: bound to 192.168.2.2 -- renewal in 953709040 seconds.
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>    address 192.168.2.2 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>    broadcast 192.168.2.255 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>    gateway 192.168.2.1 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>    nameserver 192.168.2.1 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>    nameserver 192.168.10.1 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>    domain name 'Forghani1' 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 16:03:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Withdrawing address record for 192.168.2.2 on eth1.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 16:03:27 superman-laptop avahi-daemon[5373]: Registering new address record for 192.168.2.2 on eth1.IPv4.
Oct 30 16:03:28 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 16:03:28 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 16:03:28 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 30 16:03:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 16:03:28 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 30 16:03:30 superman-laptop avahi-daemon[5373]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 16:04:00 superman-laptop ntpdate[6016]: can't find host clock.tricity.wsu.edu 
Oct 30 16:04:30 superman-laptop ntpdate[6016]: the NTP socket is in use, exiting
Oct 30 16:07:53 superman-laptop ntpd[5492]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 30 16:07:53 superman-laptop ntpd[5492]: Listening on interface #5 eth1, 192.168.2.2#123 Enabled
Oct 30 17:25:50 superman-laptop init: tty4 main process (4460) killed by TERM signal
Oct 30 17:25:50 superman-laptop init: tty5 main process (4461) killed by TERM signal
Oct 30 17:25:50 superman-laptop init: tty2 main process (4466) killed by TERM signal
Oct 30 17:25:50 superman-laptop init: tty3 main process (4467) killed by TERM signal
Oct 30 17:25:50 superman-laptop init: tty1 main process (4468) killed by TERM signal
Oct 30 17:25:50 superman-laptop init: tty6 main process (4469) killed by TERM signal
Oct 30 17:25:50 superman-laptop avahi-daemon[5373]: Got SIGTERM, quitting.
Oct 30 17:25:50 superman-laptop avahi-daemon[5373]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 17:25:52 superman-laptop rpc.statd[4333]: Caught signal 15, un-registering and exiting.
Oct 30 17:25:54 superman-laptop mountd[5184]: Caught signal 15, un-registering and exiting.
Oct 30 19:42:47 superman-laptop NetworkManager: <info>  starting... 
Oct 30 19:42:47 superman-laptop NetworkManager: <debug> [1193787767.723703] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.014392] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.014872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.015297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.016116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.076796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.077425] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.077897] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.079418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.080378] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.081634] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.082401] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.085133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.085988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.087386] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.129339] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.129785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.130195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.130557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.130918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.131332] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.131836] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.132235] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.132596] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.134564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.134934] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.135291] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.135645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.135999] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.136351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.136819] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.137204] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.137568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.137940] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.138291] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.138657] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.139034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.139441] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.139926] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.140320] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.140697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.141060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.141418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.141775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.142150] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.142505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.142860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.143215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.143571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.143925] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.144278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.144633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.144987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.145356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.145710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.146083] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.146436] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.146793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.147160] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.147514] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.147893] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.148250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.148632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.148994] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.149367] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.217383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 30 19:42:48 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.832568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.833409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.834016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.834598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.835167] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.835739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.836311] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.836881] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.837450] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.846098] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.846730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.847312] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.847929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.848510] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.849139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.849725] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.850357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.850939] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.851501] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.852065] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.852628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.853200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.853781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.854485] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.855141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.855831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.856492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.857163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.857850] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Oct 30 19:42:48 superman-laptop NetworkManager: <debug> [1193787768.858526] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: Successfully dropped root privileges.
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: avahi-daemon 0.6.20 starting up.
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: Successfully called chroot().
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: Successfully dropped remaining capabilities.
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: No service file found in /etc/avahi/services.
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: Network interface enumeration completed.
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 30 19:42:49 superman-laptop avahi-daemon[5355]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 1490234928.
Oct 30 19:42:49 superman-laptop hcid[5391]: Bluetooth HCI daemon
Oct 30 19:42:50 superman-laptop hcid[5391]: Starting SDP server
Oct 30 19:42:50 superman-laptop hcid[5391]: Created local server at unix:abstract=/var/run/dbus-6SjuRHWXdE,guid=22364a8c6dda6a1fb1130d004727c17a
Oct 30 19:42:50 superman-laptop audio[5403]: Bluetooth Audio daemon
Oct 30 19:42:50 superman-laptop audio[5403]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 30 19:42:50 superman-laptop input[5404]: Bluetooth Input daemon
Oct 30 19:42:50 superman-laptop audio[5403]: Unix socket created: 5
Oct 30 19:42:50 superman-laptop input[5404]: Registered input manager path:/org/bluez/input
Oct 30 19:42:50 superman-laptop audio[5403]: add_service_record: got record id 0x10000
Oct 30 19:42:50 superman-laptop audio[5403]: add_service_record: got record id 0x10001
Oct 30 19:42:50 superman-laptop audio[5403]: Registered manager path:/org/bluez/audio
Oct 30 19:42:50 superman-laptop NetworkManager: <debug> [1193787770.678244] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Oct 30 19:42:52 superman-laptop ntpd[5474]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Oct 30 19:42:52 superman-laptop ntpd[5475]: precision = 1.000 usec
Oct 30 19:42:52 superman-laptop ntpd[5475]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Oct 30 19:42:52 superman-laptop ntpd[5475]: Listening on interface #1 wildcard, ::#123 Disabled
Oct 30 19:42:52 superman-laptop ntpd[5475]: Listening on interface #2 lo, ::1#123 Enabled
Oct 30 19:42:52 superman-laptop ntpd[5475]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Oct 30 19:42:52 superman-laptop ntpd[5475]: kernel time sync status 0040
Oct 30 19:42:52 superman-laptop ntpd[5475]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: host name not found: ntp.ubuntu.com
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: couldn't resolve `ntp.ubuntu.com', giving up on it
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: host name not found: clock.tricity.wsu.edu
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: host name not found: wuarchive.wustl.edu
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: host name not found: gilbreth.ecn.purdue.edu
Oct 30 19:42:54 superman-laptop ntpd_initres[5554]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Oct 30 19:43:15 superman-laptop hcid[5391]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Oct 30 19:43:15 superman-laptop hcid[5391]: Default authorization agent (:1.18, /org/bluez/auth) registered
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/Forghani'. 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, but NO valid key exists.  New key needed. 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Forghani'. 
Oct 30 19:43:20 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 19:43:22 superman-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Forghani' received. 
Oct 30 19:43:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 19:43:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 30 19:43:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 19:43:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 19:43:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 30 19:43:22 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Forghani' is encrypted, and a key exists.  No new key needed. 
Oct 30 19:43:23 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Oct 30 19:43:23 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (6/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (7/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (8/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (9/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (10/10). 
Oct 30 19:43:24 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (11/10). 
Oct 30 19:43:25 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (12/10). 
Oct 30 19:43:25 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (13/10). 
Oct 30 19:43:25 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (14/10). 
Oct 30 19:43:25 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (15/10). 
Oct 30 19:43:25 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 466f726768616e69' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Oct 30 19:43:26 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 30 19:43:27 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Forghani'. 
Oct 30 19:43:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 19:43:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 19:43:28 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 30 19:43:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 19:43:28 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 30 19:43:28 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Oct 30 19:43:29 superman-laptop avahi-daemon[5355]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 19:43:30 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 30 19:43:32 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct 30 19:43:32 superman-laptop dhclient: DHCPACK from 192.168.2.1
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Registering new address record for 192.168.2.2 on eth1.IPv4.
Oct 30 19:43:32 superman-laptop dhclient: bound to 192.168.2.2 -- renewal in 953695835 seconds.
Oct 30 19:43:32 superman-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>    address 192.168.2.2 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>    broadcast 192.168.2.255 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>    gateway 192.168.2.1 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>    nameserver 192.168.2.1 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>    nameserver 192.168.10.1 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>    domain name 'Forghani1' 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 19:43:32 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Withdrawing address record for 192.168.2.2 on eth1.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: New relevant interface eth1.IPv4 for mDNS.
Oct 30 19:43:32 superman-laptop avahi-daemon[5355]: Registering new address record for 192.168.2.2 on eth1.IPv4.
Oct 30 19:43:33 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 19:43:33 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 19:43:33 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 30 19:43:33 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 19:43:33 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 30 19:43:34 superman-laptop avahi-daemon[5355]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Oct 30 19:44:04 superman-laptop ntpdate[5989]: can't find host clock.tricity.wsu.edu 
Oct 30 19:44:34 superman-laptop ntpdate[5989]: the NTP socket is in use, exiting
Oct 30 19:47:53 superman-laptop ntpd[5475]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Oct 30 19:47:53 superman-laptop ntpd[5475]: Listening on interface #5 eth1, 192.168.2.2#123 Enabled
Oct 30 19:53:00 superman-laptop init: tty4 main process (4449) killed by TERM signal
Oct 30 19:53:00 superman-laptop init: tty5 main process (4450) killed by TERM signal
Oct 30 19:53:00 superman-laptop init: tty2 main process (4452) killed by TERM signal
Oct 30 19:53:00 superman-laptop init: tty3 main process (4454) killed by TERM signal
Oct 30 19:53:00 superman-laptop init: tty1 main process (4456) killed by TERM signal
Oct 30 19:53:00 superman-laptop init: tty6 main process (4457) killed by TERM signal
Oct 30 19:53:00 superman-laptop avahi-daemon[5355]: Got SIGTERM, quitting.
Oct 30 19:53:00 superman-laptop avahi-daemon[5355]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.2.
Oct 30 19:53:02 superman-laptop rpc.statd[4322]: Caught signal 15, un-registering and exiting.
Oct 30 19:53:04 superman-laptop mountd[5167]: Caught signal 15, un-registering and exiting.
Oct 31 10:53:10 superman-laptop NetworkManager: <info>  starting...

---

### Post by Lambert on 2007-10-31
A couple things I possibly see, don't have time right now to give a full look at this but one thing I can suggest is to stop the avahi dameon and see if it helps.

```

sudo ifconfig eth1:avahi down

```

```

sudo /etc/init.d/avahi-daemon stop

```

Also install the package nscd from the repositories. After these two steps is there a difference in your network?

---

### Post by sasanf on 2007-11-02
Disabling avahi hasn't seemed the help.  When I issued the first command, nothing happened.  I got an error message.  When I issued the second command, the avahi service did get stopped.  I found what looks to be a great tutorial, on another thread, on getting the 1390 WLAN card to work under many flavors of Ubuntu (7.10 included).  The tutorial also states the the driver included with Ubuntu is broken.  I am going to assume since the tutorial is also intended for 7.10 that the driver included with 7.10 is also partially broken (not as much as 7.04, but broken nonetheless).  Here is a link to the thread: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092).  

I haven't been able to try it as I am only able to connect to the internet via a wireless connection; since my wireless connection is working sporadically in Ubuntu, I will have to wait until I get home and connect to the internet via a wired connection.  I am ,regretfully, writing this post via Wind:(ws.  I'll post when I have news using the ndiswrapper.  I think it will work.  I set up my friends workstation with Ubuntu 7.10 and his Netgear wireless wasn't recognized.  I used Ndiswrapper to get his Netgear to work in Ubuntu.  His Netgear works great.

I hope the Ubuntu developers are aware of the problem with the Broadcom driver.  I will also post my logs for November 1st and November 2nd as soon as possible.  Thanks again for all of your help.

---

### Post by sasanf on 2007-11-02
I just realized that when I tried your suggestion concerning avahi that I didn't install the nscd package.  At the moment, I prefer to follow the tutorial I referred to in my previous post.  If the tutorial doesn't work, I will reinstall Ubuntu fresh and try your suggestions again.

---

### Post by sasanf on 2007-11-03
I configured my wireless card via the tutorial and so far it seems to be working very well.  If it stops, I'll repost.  I'll also go ahead and post my logs from the last few days (maybe they will help the developers discover what the problem is).

---

### Post by sasanf on 2007-11-03
Note From SasanF: I configured ndiswrapper late afternoon Nov. 2 2007

Nov  1 10:48:57 superman-laptop NetworkManager: <debug> [1193928537.177671] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 10:49:01 superman-laptop NetworkManager: <debug> [1193928541.181482] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 10:49:11 superman-laptop init: tty4 main process (4443) killed by TERM signal
Nov  1 10:49:11 superman-laptop init: tty5 main process (4444) killed by TERM signal
Nov  1 10:49:11 superman-laptop init: tty2 main process (4446) killed by TERM signal
Nov  1 10:49:11 superman-laptop init: tty3 main process (4448) killed by TERM signal
Nov  1 10:49:11 superman-laptop init: tty1 main process (4450) killed by TERM signal
Nov  1 10:49:11 superman-laptop init: tty6 main process (4451) killed by TERM signal
Nov  1 10:49:12 superman-laptop avahi-daemon[5355]: Got SIGTERM, quitting.
Nov  1 10:49:12 superman-laptop avahi-daemon[5355]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 10:49:13 superman-laptop NetworkManager: <debug> [1193928553.185601] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 10:49:14 superman-laptop rpc.statd[4316]: Caught signal 15, un-registering and exiting.
Nov  1 10:49:16 superman-laptop mountd[5184]: Caught signal 15, un-registering and exiting.
Nov  1 12:13:18 superman-laptop NetworkManager: <info>  starting... 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.658863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.828961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.829629] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.830120] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.831903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.891074] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.891783] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.892212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.892703] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.893190] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.893613] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.894276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.894798] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.895725] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.896197] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.896643] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.897084] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.897535] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.897982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.898429] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.899462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.899937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.900381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.900830] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.901279] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.901737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.902211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.902652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.903095] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.903533] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.903973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.904413] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.904859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.905301] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.905783] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.906230] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.906675] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.907136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.907579] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.908014] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.908477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.909503] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.909964] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.910423] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.911329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.911768] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.912223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.955044] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.955564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.956042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.956530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.957101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.957590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.958198] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.958663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.960807] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.961291] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.961757] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.962236] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.962853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.963328] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.963755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.964182] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.964616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <debug> [1193933598.965045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Nov  1 12:13:18 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Nov  1 12:13:18 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.035434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Nov  1 12:13:19 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.609906] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.610523] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.610954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.611376] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.611792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.612209] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.612621] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.613034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.613467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.613923] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.614355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.614786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.615230] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.615708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.616141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.616573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.617021] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.617461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.617910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.618344] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.618763] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.619179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.619596] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.620013] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.620429] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.620861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.621276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.621714] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.622155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Nov  1 12:13:19 superman-laptop NetworkManager: <debug> [1193933599.622605] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: Successfully dropped root privileges.
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: avahi-daemon 0.6.20 starting up.
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: Successfully called chroot().
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: Successfully dropped remaining capabilities.
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: No service file found in /etc/avahi/services.
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: Network interface enumeration completed.
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  1 12:13:20 superman-laptop avahi-daemon[5374]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 125102952.
Nov  1 12:13:20 superman-laptop hcid[5410]: Bluetooth HCI daemon
Nov  1 12:13:20 superman-laptop hcid[5410]: Starting SDP server
Nov  1 12:13:20 superman-laptop hcid[5410]: Created local server at unix:abstract=/var/run/dbus-kiWSSgJhKC,guid=06fb288d12507299fab14b004729fb20
Nov  1 12:13:20 superman-laptop audio[5422]: Bluetooth Audio daemon
Nov  1 12:13:20 superman-laptop audio[5422]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  1 12:13:20 superman-laptop audio[5422]: Unix socket created: 5
Nov  1 12:13:20 superman-laptop input[5423]: Bluetooth Input daemon
Nov  1 12:13:20 superman-laptop input[5423]: Registered input manager path:/org/bluez/input
Nov  1 12:13:20 superman-laptop audio[5422]: add_service_record: got record id 0x10000
Nov  1 12:13:20 superman-laptop audio[5422]: add_service_record: got record id 0x10001
Nov  1 12:13:20 superman-laptop audio[5422]: Registered manager path:/org/bluez/audio
Nov  1 12:13:21 superman-laptop ntpd[5476]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Nov  1 12:13:21 superman-laptop ntpd[5477]: precision = 1.000 usec
Nov  1 12:13:21 superman-laptop NetworkManager: <debug> [1193933601.577461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Nov  1 12:13:21 superman-laptop ntpd[5477]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Nov  1 12:13:21 superman-laptop ntpd[5477]: Listening on interface #1 wildcard, ::#123 Disabled
Nov  1 12:13:21 superman-laptop ntpd[5477]: Listening on interface #2 lo, ::1#123 Enabled
Nov  1 12:13:21 superman-laptop ntpd[5477]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Nov  1 12:13:21 superman-laptop ntpd[5477]: kernel time sync status 0040
Nov  1 12:13:21 superman-laptop ntpd[5477]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: host name not found: ntp.ubuntu.com
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: host name not found: clock.tricity.wsu.edu
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: host name not found: wuarchive.wustl.edu
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: host name not found: gilbreth.ecn.purdue.edu
Nov  1 12:13:23 superman-laptop ntpd_initres[5538]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Nov  1 12:14:15 superman-laptop hcid[5410]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Nov  1 12:14:15 superman-laptop hcid[5410]: Default authorization agent (:1.18, /org/bluez/auth) registered
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Nov  1 12:14:22 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:14:23 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  1 12:14:23 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov  1 12:14:23 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Nov  1 12:14:23 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Nov  1 12:14:23 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  1 12:14:24 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  1 12:14:25 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  1 12:14:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  1 12:14:25 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  1 12:14:25 superman-laptop avahi-daemon[5374]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Nov  1 12:14:26 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  1 12:14:28 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov  1 12:14:28 superman-laptop dhclient: DHCPOFFER from 150.216.226.254
Nov  1 12:14:28 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov  1 12:14:28 superman-laptop dhclient: DHCPACK from 150.216.226.254
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: Registering new address record for 150.216.228.182 on eth1.IPv4.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: Withdrawing address record for 150.216.228.182 on eth1.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 12:14:28 superman-laptop avahi-daemon[5374]: Registering new address record for 150.216.228.182 on eth1.IPv4.
Nov  1 12:14:28 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Nov  1 12:14:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  1 12:14:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Nov  1 12:14:28 superman-laptop dhclient: bound to 150.216.228.182 -- renewal in 1565 seconds.
Nov  1 12:14:29 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>    address 150.216.228.182 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>    broadcast 150.216.228.255 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>    gateway 150.216.228.254 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:14:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  1 12:14:29 superman-laptop avahi-daemon[5374]: Withdrawing address record for 150.216.228.182 on eth1.
Nov  1 12:14:29 superman-laptop avahi-daemon[5374]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 12:14:29 superman-laptop avahi-daemon[5374]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  1 12:14:29 superman-laptop avahi-daemon[5374]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Nov  1 12:14:29 superman-laptop avahi-daemon[5374]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 12:14:29 superman-laptop avahi-daemon[5374]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 12:14:29 superman-laptop avahi-daemon[5374]: Registering new address record for 150.216.228.182 on eth1.IPv4.
Nov  1 12:14:30 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Nov  1 12:14:30 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov  1 12:14:30 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Nov  1 12:14:30 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  1 12:14:30 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  1 12:14:30 superman-laptop ntpdate[5972]: can't find host clock.tricity.wsu.edu 
Nov  1 12:14:31 superman-laptop ntpdate[5972]: the NTP socket is in use, exiting
Nov  1 12:14:32 superman-laptop avahi-daemon[5374]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Nov  1 12:17:14 superman-laptop avahi-daemon[5374]: Got SIGTERM, quitting.
Nov  1 12:17:14 superman-laptop avahi-daemon[5374]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 12:18:22 superman-laptop ntpd[5477]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Nov  1 12:18:22 superman-laptop ntpd[5477]: Listening on interface #5 eth1, 150.216.228.182#123 Enabled
Nov  1 12:40:33 superman-laptop dhclient: DHCPREQUEST on eth1 to 150.216.226.254 port 67
Nov  1 12:40:33 superman-laptop dhclient: DHCPACK from 150.216.243.174
Nov  1 12:40:33 superman-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Nov  1 12:40:33 superman-laptop dhclient: bound to 150.216.228.182 -- renewal in 1579 seconds.
Nov  1 12:52:23 superman-laptop NetworkManager: <debug> [1193935943.113514] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:52:27 superman-laptop NetworkManager: <debug> [1193935947.113519] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:52:37 superman-laptop NetworkManager: <debug> [1193935957.113518] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:52:43 superman-laptop NetworkManager: <debug> [1193935963.117673] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7D:50 to 00:17:0F:20:7B:B0 on wireless network 'taho' 
Nov  1 12:57:47 superman-laptop NetworkManager: <debug> [1193936267.341667] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:57:51 superman-laptop NetworkManager: <debug> [1193936271.341522] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:58:05 superman-laptop NetworkManager: <info>  eth1: link timed out. 
Nov  1 12:58:05 superman-laptop NetworkManager: <info>  SWITCH: found better connection 'eth1/taho' than current connection 'eth1/taho'.  same_ssid=1, have_link=0 
Nov  1 12:58:05 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Nov  1 12:58:05 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  1 12:58:05 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 12:58:05 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5884
Nov  1 12:58:05 superman-laptop dhclient: killed old client process, removed PID file
Nov  1 12:58:05 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Nov  1 12:58:06 superman-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Nov  1 12:58:07 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  1 12:58:07 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov  1 12:58:07 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:58:08 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  1 12:58:08 superman-laptop NetworkManager: <debug> [1193936288.307801] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:58:10 superman-laptop NetworkManager: <debug> [1193936290.309510] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7D:50 to 00:17:0F:20:7B:B0 on wireless network 'taho' 
Nov  1 12:58:13 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:58:22 superman-laptop ntpd[5477]: Deleting interface #4 eth1, fe80::216:ceff:fe37:332#123, interface stats: received=0, sent=0, dropped=0, active_time=2400 secs
Nov  1 12:58:22 superman-laptop ntpd[5477]: Deleting interface #5 eth1, 150.216.228.182#123, interface stats: received=0, sent=0, dropped=0, active_time=2400 secs
Nov  1 12:58:23 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:58:30 superman-laptop NetworkManager: <debug> [1193936310.309523] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:58:31 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Nov  1 12:58:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  1 12:58:31 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  1 12:58:32 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  1 12:58:32 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Nov  1 12:58:32 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  1 12:58:32 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  1 12:58:33 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  1 12:58:34 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:58:34 superman-laptop NetworkManager: <debug> [1193936314.393488] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:58:35 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov  1 12:58:38 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Nov  1 12:58:44 superman-laptop NetworkManager: <debug> [1193936324.405516] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7D:50 to 00:17:0F:20:7B:B0 on wireless network 'taho' 
Nov  1 12:58:45 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Nov  1 12:58:47 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:58:52 superman-laptop NetworkManager: <info>  eth1: link timed out. 
Nov  1 12:58:52 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:58:54 superman-laptop NetworkManager: <debug> [1193936334.405523] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:58:58 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:58:58 superman-laptop NetworkManager: <debug> [1193936338.405478] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:59:00 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov  1 12:59:06 superman-laptop dhclient: No DHCPOFFERS received.
Nov  1 12:59:06 superman-laptop dhclient: Trying recorded lease 192.168.2.3
Nov  1 12:59:08 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:59:09 superman-laptop avahi-autoipd(eth1)[6345]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Nov  1 12:59:09 superman-laptop avahi-autoipd(eth1)[6345]: Successfully called chroot().
Nov  1 12:59:09 superman-laptop avahi-autoipd(eth1)[6345]: Successfully dropped root privileges.
Nov  1 12:59:09 superman-laptop avahi-autoipd(eth1)[6345]: Starting with address 169.254.3.94
Nov  1 12:59:10 superman-laptop NetworkManager: <debug> [1193936350.405516] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7B:B0 to 00:17:0F:20:7D:50 on wireless network 'taho' 
Nov  1 12:59:14 superman-laptop NetworkManager: <debug> [1193936354.405624] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:17:0F:20:7D:50 to 00:17:0F:20:7B:B0 on wireless network 'taho' 
Nov  1 12:59:14 superman-laptop avahi-autoipd(eth1)[6345]: Callout BIND, address 169.254.3.94 on interface eth1
Nov  1 12:59:18 superman-laptop avahi-autoipd(eth1)[6345]: Successfully claimed IP address 169.254.3.94
Nov  1 12:59:18 superman-laptop dhclient: Trying recorded lease 192.168.2.4
Nov  1 12:59:18 superman-laptop avahi-autoipd(eth1)[6345]: A routable address has been configured.
Nov  1 12:59:18 superman-laptop avahi-autoipd(eth1)[6345]: Callout UNBIND, address 169.254.3.94 on interface eth1
Nov  1 12:59:19 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 12:59:21 superman-laptop avahi-autoipd(eth1)[6345]: No longer a routable address configured, restarting probe process.
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  1 12:59:21 superman-laptop dhclient: Trying recorded lease 192.168.0.87
Nov  1 12:59:21 superman-laptop avahi-autoipd(eth1)[6345]: A routable address has been configured.
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  Activation (eth1) failed for access point (taho) 
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  Activation (eth1) failed. 
Nov  1 12:59:21 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 12:59:21 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6326
Nov  1 12:59:21 superman-laptop dhclient: killed old client process, removed PID file
Nov  1 12:59:21 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Nov  1 12:59:21 superman-laptop dhclient: send_packet: Network is unreachable
Nov  1 12:59:21 superman-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Nov  1 12:59:21 superman-laptop avahi-autoipd(eth1)[6345]: Got SIGTERM, quitting.
Nov  1 12:59:22 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Nov  1 12:59:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:22 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Nov  1 12:59:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:22 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Nov  1 12:59:22 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:27 superman-laptop NetworkManager: <debug> [1193936367.133745] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'taho' 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / taho 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  1 12:59:27 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant7^I' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:28 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  1 12:59:29 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Nov  1 12:59:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  1 12:59:29 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  1 12:59:30 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  1 12:59:30 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Nov  1 12:59:30 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  1 12:59:30 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  1 12:59:31 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  1 12:59:31 superman-laptop avahi-autoipd(eth1)[6440]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Nov  1 12:59:31 superman-laptop avahi-autoipd(eth1)[6440]: Successfully called chroot().
Nov  1 12:59:31 superman-laptop avahi-autoipd(eth1)[6440]: Successfully dropped root privileges.
Nov  1 12:59:31 superman-laptop avahi-autoipd(eth1)[6440]: Starting with address 169.254.3.94
Nov  1 12:59:32 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov  1 12:59:32 superman-laptop dhclient: DHCPOFFER from 150.216.226.254
Nov  1 12:59:32 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov  1 12:59:32 superman-laptop dhclient: DHCPACK from 150.216.226.254
Nov  1 12:59:32 superman-laptop avahi-autoipd(eth1)[6440]: Got SIGTERM, quitting.
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  1 12:59:33 superman-laptop dhclient: bound to 150.216.228.182 -- renewal in 1668 seconds.
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  Activation (eth1) failed for access point (taho) 
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  Activation (eth1) failed. 
Nov  1 12:59:33 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 12:59:33 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6425
Nov  1 12:59:33 superman-laptop dhclient: killed old client process, removed PID file
Nov  1 12:59:33 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Nov  1 12:59:34 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Nov  1 12:59:34 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 12:59:34 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Nov  1 12:59:46 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Nov  1 12:59:46 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'AP_SCAN 0'.  Response: 'TIMEOUT[CLI]' 
Nov  1 12:59:46 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't set AP_SCAN 0 
Nov  1 12:59:46 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Nov  1 12:59:58 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Nov  1 12:59:58 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'TERMINATE'.  Response: 'TIMEOUT[CLI]' 
Nov  1 12:59:58 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't terminate wpasupplicant cleanly. 
Nov  1 13:00:09 superman-laptop init: tty4 main process (4460) killed by TERM signal
Nov  1 13:00:09 superman-laptop init: tty5 main process (4461) killed by TERM signal
Nov  1 13:00:09 superman-laptop init: tty2 main process (4463) killed by TERM signal
Nov  1 13:00:09 superman-laptop init: tty3 main process (4465) killed by TERM signal
Nov  1 13:00:09 superman-laptop init: tty1 main process (4467) killed by TERM signal
Nov  1 13:00:09 superman-laptop init: tty6 main process (4468) killed by TERM signal
Nov  1 13:00:11 superman-laptop rpc.statd[4333]: Caught signal 15, un-registering and exiting.
Nov  1 13:00:13 superman-laptop mountd[5186]: Caught signal 15, un-registering and exiting.
Nov  1 13:58:00 superman-laptop NetworkManager: <info>  starting... 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.407152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.714101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.714723] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.715430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.716988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.776841] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.777563] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.778833] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.779860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.780901] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.781367] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.781793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.782232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.782641] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.783130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.783741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.784795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.785297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.786240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.827278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.827902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.828335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.828740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.829144] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.829551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.829955] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.830363] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.830769] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.831176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.831582] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.836547] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.837003] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.837415] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.837824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.838256] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.838663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.839074] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.840266] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.840699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.841108] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.841527] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.841931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.842334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.842755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.843204] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.844357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.845992] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.846650] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.847066] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.847464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.848824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.852884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.853488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.854637] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.855068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.855474] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.855907] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.856334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.856741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.857141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.857556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.857957] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.858359] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.858778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.860603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.861023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Nov  1 13:58:00 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Nov  1 13:58:00 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  1 13:58:00 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  1 13:58:00 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov  1 13:58:00 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov  1 13:58:00 superman-laptop NetworkManager: <debug> [1193939880.928878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Nov  1 13:58:01 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  1 13:58:01 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  1 13:58:01 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Nov  1 13:58:01 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.505747] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.506277] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.506699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.507113] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.507547] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.507977] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.508384] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.508792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.509216] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.509624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.510032] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.510439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.510917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.511333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.519910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.520581] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.521236] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.521924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.522592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.523253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.523974] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.524654] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.525338] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.526012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.526707] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.527398] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.528115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.528840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Nov  1 13:58:01 superman-laptop NetworkManager: <debug> [1193939881.529552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: Successfully dropped root privileges.
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: avahi-daemon 0.6.20 starting up.
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: Successfully called chroot().
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: Successfully dropped remaining capabilities.
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: No service file found in /etc/avahi/services.
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: Network interface enumeration completed.
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  1 13:58:02 superman-laptop avahi-daemon[5359]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 1835696010.
Nov  1 13:58:02 superman-laptop hcid[5394]: Bluetooth HCI daemon
Nov  1 13:58:02 superman-laptop hcid[5394]: Starting SDP server
Nov  1 13:58:02 superman-laptop hcid[5394]: Created local server at unix:abstract=/var/run/dbus-GOHUgpiAJC,guid=83ed4ca8f826cddf2f101000472a13aa
Nov  1 13:58:02 superman-laptop audio[5406]: Bluetooth Audio daemon
Nov  1 13:58:02 superman-laptop audio[5406]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  1 13:58:02 superman-laptop audio[5406]: Unix socket created: 5
Nov  1 13:58:02 superman-laptop input[5407]: Bluetooth Input daemon
Nov  1 13:58:02 superman-laptop input[5407]: Registered input manager path:/org/bluez/input
Nov  1 13:58:02 superman-laptop audio[5406]: add_service_record: got record id 0x10000
Nov  1 13:58:02 superman-laptop audio[5406]: add_service_record: got record id 0x10001
Nov  1 13:58:02 superman-laptop audio[5406]: Registered manager path:/org/bluez/audio
Nov  1 13:58:03 superman-laptop NetworkManager: <debug> [1193939883.432091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Nov  1 13:58:05 superman-laptop ntpd[5477]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Nov  1 13:58:05 superman-laptop ntpd[5478]: precision = 1.000 usec
Nov  1 13:58:05 superman-laptop ntpd[5478]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Nov  1 13:58:05 superman-laptop ntpd[5478]: Listening on interface #1 wildcard, ::#123 Disabled
Nov  1 13:58:05 superman-laptop ntpd[5478]: Listening on interface #2 lo, ::1#123 Enabled
Nov  1 13:58:05 superman-laptop ntpd[5478]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Nov  1 13:58:05 superman-laptop ntpd[5478]: kernel time sync status 0040
Nov  1 13:58:05 superman-laptop ntpd[5478]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: host name not found: ntp.ubuntu.com
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: host name not found: clock.tricity.wsu.edu
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: host name not found: wuarchive.wustl.edu
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: host name not found: gilbreth.ecn.purdue.edu
Nov  1 13:58:07 superman-laptop ntpd_initres[5528]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Nov  1 13:58:28 superman-laptop hcid[5394]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Nov  1 13:58:28 superman-laptop hcid[5394]: Default authorization agent (:1.17, /org/bluez/auth) registered
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Nov  1 13:58:38 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (6/10). 
Nov  1 13:58:39 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  1 13:58:40 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  1 13:58:41 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  1 13:58:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  1 13:58:41 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  1 13:58:41 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 13:58:42 superman-laptop avahi-daemon[5359]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Nov  1 13:58:42 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  1 13:58:43 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Nov  1 13:58:49 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Nov  1 13:59:01 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Nov  1 13:59:13 superman-laptop dhclient: No DHCPOFFERS received.
Nov  1 13:59:13 superman-laptop dhclient: Trying recorded lease 192.168.2.3
Nov  1 13:59:13 superman-laptop avahi-daemon[5359]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Nov  1 13:59:13 superman-laptop avahi-daemon[5359]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 13:59:13 superman-laptop avahi-daemon[5359]: Registering new address record for 192.168.2.3 on eth1.IPv4.
Nov  1 13:59:16 superman-laptop avahi-daemon[5359]: Withdrawing address record for 192.168.2.3 on eth1.
Nov  1 13:59:16 superman-laptop avahi-daemon[5359]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.3.
Nov  1 13:59:16 superman-laptop avahi-daemon[5359]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  1 13:59:16 superman-laptop avahi-autoipd(eth1)[5982]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Nov  1 13:59:16 superman-laptop avahi-autoipd(eth1)[5982]: Successfully called chroot().
Nov  1 13:59:16 superman-laptop avahi-autoipd(eth1)[5982]: Successfully dropped root privileges.
Nov  1 13:59:16 superman-laptop avahi-autoipd(eth1)[5982]: Starting with address 169.254.3.94
Nov  1 13:59:21 superman-laptop avahi-autoipd(eth1)[5982]: Callout BIND, address 169.254.3.94 on interface eth1
Nov  1 13:59:21 superman-laptop avahi-daemon[5359]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Nov  1 13:59:21 superman-laptop avahi-daemon[5359]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 13:59:21 superman-laptop avahi-daemon[5359]: Registering new address record for 169.254.3.94 on eth1.IPv4.
Nov  1 13:59:25 superman-laptop avahi-autoipd(eth1)[5982]: Successfully claimed IP address 169.254.3.94
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  1 13:59:25 superman-laptop dhclient: Trying recorded lease 192.168.2.4
Nov  1 13:59:25 superman-laptop avahi-autoipd(eth1)[5982]: A routable address has been configured.
Nov  1 13:59:25 superman-laptop avahi-autoipd(eth1)[5982]: Callout UNBIND, address 169.254.3.94 on interface eth1
Nov  1 13:59:25 superman-laptop avahi-daemon[5359]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.3.94.
Nov  1 13:59:25 superman-laptop avahi-daemon[5359]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Nov  1 13:59:25 superman-laptop avahi-daemon[5359]: Registering new address record for 192.168.2.4 on eth1.IPv4.
Nov  1 13:59:25 superman-laptop avahi-daemon[5359]: Withdrawing address record for 169.254.3.94 on eth1.
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  Activation (eth1) failed for access point (taho) 
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  Activation (eth1) failed. 
Nov  1 13:59:25 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 13:59:25 superman-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5914
Nov  1 13:59:25 superman-laptop dhclient: killed old client process, removed PID file
Nov  1 13:59:25 superman-laptop dhclient: DHCPRELEASE on eth1 to 150.216.226.254 port 67
Nov  1 13:59:25 superman-laptop dhclient: send_packet: Network is unreachable
Nov  1 13:59:25 superman-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Nov  1 13:59:25 superman-laptop avahi-autoipd(eth1)[5982]: Got SIGTERM, quitting.
Nov  1 13:59:25 superman-laptop avahi-daemon[5359]: Withdrawing address record for 192.168.2.4 on eth1.
Nov  1 13:59:25 superman-laptop avahi-daemon[5359]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.4.
Nov  1 13:59:25 superman-laptop avahi-daemon[5359]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  1 13:59:26 superman-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Nov  1 13:59:26 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 13:59:26 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Nov  1 13:59:35 superman-laptop avahi-autoipd(eth1)[6013]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Nov  1 13:59:35 superman-laptop avahi-autoipd(eth1)[6013]: Successfully called chroot().
Nov  1 13:59:35 superman-laptop avahi-autoipd(eth1)[6013]: Successfully dropped root privileges.
Nov  1 13:59:35 superman-laptop avahi-autoipd(eth1)[6013]: Starting with address 169.254.3.94
Nov  1 13:59:38 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Nov  1 13:59:38 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'AP_SCAN 0'.  Response: 'TIMEOUT[CLI]' 
Nov  1 13:59:38 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't set AP_SCAN 0 
Nov  1 13:59:38 superman-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Nov  1 13:59:39 superman-laptop avahi-daemon[5359]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Nov  1 13:59:39 superman-laptop avahi-autoipd(eth1)[6013]: SIOCSIFFLAGS failed: Permission denied
Nov  1 13:59:50 superman-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Nov  1 13:59:50 superman-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'TERMINATE'.  Response: 'TIMEOUT[CLI]' 
Nov  1 13:59:50 superman-laptop NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't terminate wpasupplicant cleanly. 
Nov  1 14:24:54 superman-laptop init: tty4 main process (4452) killed by TERM signal
Nov  1 14:24:54 superman-laptop init: tty5 main process (4453) killed by TERM signal
Nov  1 14:24:54 superman-laptop init: tty2 main process (4455) killed by TERM signal
Nov  1 14:24:54 superman-laptop init: tty1 main process (4459) killed by TERM signal
Nov  1 14:24:54 superman-laptop init: tty6 main process (4460) killed by TERM signal
Nov  1 14:24:54 superman-laptop init: tty3 main process (4457) killed by TERM signal
Nov  1 14:24:54 superman-laptop avahi-daemon[5359]: Got SIGTERM, quitting.
Nov  1 14:24:56 superman-laptop rpc.statd[4325]: Caught signal 15, un-registering and exiting.
Nov  1 14:24:58 superman-laptop mountd[5171]: Caught signal 15, un-registering and exiting.
Nov  1 20:13:19 superman-laptop NetworkManager: <info>  starting... 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.315206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.605673] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.606357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.606894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.607330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.607784] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.608186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.608722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4311'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.609083] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.609531] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.609887] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.610243] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.610597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.610950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.611325] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.671741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.672423] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.673616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.674287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.674779] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.675619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.676060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.676461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.677000] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.677390] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.678244] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.678611] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.678973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.679350] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.679710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.680072] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.680439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.680804] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.681172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.682058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.682431] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.682796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.683201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.725036] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.725438] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.725808] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.726178] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.726587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.727094] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.727519] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.727894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.728262] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.728627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.728990] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.729353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.729733] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.730096] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.730456] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.730815] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.731195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.731545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.731906] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.732266] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.732624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.732984] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.733375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.735425] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.735797] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.736157] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.736517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.736919] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_0c_d4_0e'). 
Nov  1 20:13:19 superman-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Nov  1 20:13:19 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  1 20:13:19 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  1 20:13:19 superman-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov  1 20:13:19 superman-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov  1 20:13:19 superman-laptop NetworkManager: <debug> [1193962399.804789] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_37_03_32'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Nov  1 20:13:20 superman-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  1 20:13:20 superman-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  1 20:13:20 superman-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Nov  1 20:13:20 superman-laptop NetworkManager: <info>  Deactivating device eth1. 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.518341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.518821] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.519309] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.519898] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.520494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.521072] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.521650] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.522227] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.522809] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.531220] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.531915] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.532497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.533149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.533731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.534342] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.534932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.535567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.536155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.536739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.537329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.537949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS721060G9SA00_MPCCN8Y3HUVHUL'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.538556] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AC8484628484313E'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.539183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8c8c88f2_ec2d_48fd_85a5_e96b540dd137'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.539861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_15435f8c_09df_48e7_94f3_8985afefad7e'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.540558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.541145] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.541716] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.542287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Nov  1 20:13:20 superman-laptop NetworkManager: <debug> [1193962400.542854] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_GCC4244'). 
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: Successfully dropped root privileges.
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: avahi-daemon 0.6.20 starting up.
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: Successfully called chroot().
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: Successfully dropped remaining capabilities.
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: No service file found in /etc/avahi/services.
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: Network interface enumeration completed.
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  1 20:13:21 superman-laptop avahi-daemon[5369]: Server startup complete. Host name is superman-laptop.local. Local service cookie is 3556698129.
Nov  1 20:13:21 superman-laptop hcid[5405]: Bluetooth HCI daemon
Nov  1 20:13:21 superman-laptop hcid[5405]: Starting SDP server
Nov  1 20:13:21 superman-laptop hcid[5405]: Created local server at unix:abstract=/var/run/dbus-5228hx46Bm,guid=239e302f3f2014643c3e9200472a6ba1
Nov  1 20:13:21 superman-laptop audio[5417]: Bluetooth Audio daemon
Nov  1 20:13:21 superman-laptop audio[5417]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  1 20:13:21 superman-laptop audio[5417]: Unix socket created: 5
Nov  1 20:13:21 superman-laptop input[5418]: Bluetooth Input daemon
Nov  1 20:13:21 superman-laptop input[5418]: Registered input manager path:/org/bluez/input
Nov  1 20:13:21 superman-laptop audio[5417]: add_service_record: got record id 0x10000
Nov  1 20:13:21 superman-laptop audio[5417]: add_service_record: got record id 0x10001
Nov  1 20:13:21 superman-laptop audio[5417]: Registered manager path:/org/bluez/audio
Nov  1 20:13:22 superman-laptop NetworkManager: <debug> [1193962402.504693] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Introducing_Char'). 
Nov  1 20:13:24 superman-laptop ntpd[5488]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Nov  1 20:13:24 superman-laptop ntpd[5489]: precision = 1.000 usec
Nov  1 20:13:24 superman-laptop ntpd[5489]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Nov  1 20:13:24 superman-laptop ntpd[5489]: Listening on interface #1 wildcard, ::#123 Disabled
Nov  1 20:13:24 superman-laptop ntpd[5489]: Listening on interface #2 lo, ::1#123 Enabled
Nov  1 20:13:24 superman-laptop ntpd[5489]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Nov  1 20:13:24 superman-laptop ntpd[5489]: kernel time sync status 0040
Nov  1 20:13:24 superman-laptop ntpd[5489]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: host name not found: ntp.ubuntu.com
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: host name not found: clock.tricity.wsu.edu
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: couldn't resolve `clock.tricity.wsu.edu', giving up on it
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: host name not found: wuarchive.wustl.edu
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: couldn't resolve `wuarchive.wustl.edu', giving up on it
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: host name not found: gilbreth.ecn.purdue.edu
Nov  1 20:13:26 superman-laptop ntpd_initres[5530]: couldn't resolve `gilbreth.ecn.purdue.edu', giving up on it
Nov  1 20:18:31 superman-laptop hcid[5405]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Nov  1 20:18:31 superman-laptop hcid[5405]: Default authorization agent (:1.17, /org/bluez/auth) registered
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Will activate connection 'eth1/taho'. 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Activation (eth1) started... 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'taho' is unencrypted, no key needed. 
Nov  1 20:18:38 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 20:18:39 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: response was '0' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7461686f' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov  1 20:18:40 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  1 20:18:41 superman-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'taho'. 
Nov  1 20:18:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  1 20:18:41 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  1 20:18:42 superman-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  1 20:18:42 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  1 20:18:42 superman-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  1 20:18:42 superman-laptop avahi-daemon[5369]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Nov  1 20:18:44 superman-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  1 20:18:46 superman-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  1 20:18:48 superman-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov  1 20:18:48 superman-laptop dhclient: DHCPOFFER from 1.1.1.1
Nov  1 20:18:48 superman-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov  1 20:18:48 superman-laptop dhclient: DHCPACK from 1.1.1.1
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: Registering new address record for 150.216.228.182 on eth1.IPv4.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: Withdrawing address record for 150.216.228.182 on eth1.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 20:18:48 superman-laptop avahi-daemon[5369]: Registering new address record for 150.216.228.182 on eth1.IPv4.
Nov  1 20:18:48 superman-laptop dhclient: bound to 150.216.228.182 -- renewal in 1731 seconds.
Nov  1 20:18:48 superman-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Nov  1 20:18:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  1 20:18:48 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>    address 150.216.228.182 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>    netmask 255.255.255.0 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>    broadcast 150.216.228.255 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>    gateway 150.216.228.254 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>    nameserver 150.216.240.61 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>    nameserver 150.216.1.252 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>    domain name 'wireless.ecu.edu' 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov  1 20:18:49 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  1 20:18:49 superman-laptop avahi-daemon[5369]: Withdrawing address record for 150.216.228.182 on eth1.
Nov  1 20:18:49 superman-laptop avahi-daemon[5369]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 20:18:49 superman-laptop avahi-daemon[5369]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  1 20:18:49 superman-laptop avahi-daemon[5369]: Withdrawing address record for fe80::216:ceff:fe37:332 on eth1.
Nov  1 20:18:49 superman-laptop avahi-daemon[5369]: Joining mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 20:18:49 superman-laptop avahi-daemon[5369]: New relevant interface eth1.IPv4 for mDNS.
Nov  1 20:18:49 superman-laptop avahi-daemon[5369]: Registering new address record for 150.216.228.182 on eth1.IPv4.
Nov  1 20:18:50 superman-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Nov  1 20:18:50 superman-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov  1 20:18:50 superman-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Nov  1 20:18:50 superman-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  1 20:18:50 superman-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  1 20:18:51 superman-laptop ntpdate[5976]: can't find host clock.tricity.wsu.edu 
Nov  1 20:18:51 superman-laptop ntpdate[5976]: the NTP socket is in use, exiting
Nov  1 20:18:52 superman-laptop avahi-daemon[5369]: Registering new address record for fe80::216:ceff:fe37:332 on eth1.*.
Nov  1 20:23:25 superman-laptop ntpd[5489]: Listening on interface #4 eth1, fe80::216:ceff:fe37:332#123 Enabled
Nov  1 20:23:25 superman-laptop ntpd[5489]: Listening on interface #5 eth1, 150.216.228.182#123 Enabled
Nov  1 20:41:01 superman-laptop init: tty4 main process (4463) killed by TERM signal
Nov  1 20:41:01 superman-laptop init: tty5 main process (4464) killed by TERM signal
Nov  1 20:41:01 superman-laptop init: tty2 main process (4466) killed by TERM signal
Nov  1 20:41:01 superman-laptop init: tty3 main process (4468) killed by TERM signal
Nov  1 20:41:01 superman-laptop init: tty1 main process (4470) killed by TERM signal
Nov  1 20:41:01 superman-laptop init: tty6 main process (4471) killed by TERM signal
Nov  1 20:41:01 superman-laptop avahi-daemon[5369]: Got SIGTERM, quitting.
Nov  1 20:41:01 superman-laptop avahi-daemon[5369]: Leaving mDNS multicast group on interface eth1.IPv4 with address 150.216.228.182.
Nov  1 20:41:04 superman-laptop rpc.statd[4336]: Caught signal 15, un-registering and exiting.
Nov  1 20:41:06 superman-laptop mountd[5181]: Caught signal 15, un-registering and exiting.
Nov  2 07:47:51 superman-laptop NetworkManager: <info>  starting...

---

