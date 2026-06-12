---
title: "acx111 based wlan card stopped working after update"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by mdnielsen on 2008-07-24
I installed a fresh install of Hardy today and ran updates. After I ran the updates (23x of them) the card stopped working. It is seen by the wireless manager, but doesn't show any networks to connect to. I have searched this forum and google, please help. Below is all the information that I can think to include that may help.

iwconfig:
```
wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Monitor  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
(I can even set the card into monitor mode, as you can see)

dmesg | grep acx:
```
[   42.084606] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   42.084619] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   43.652853] acx: found ACX111-based wireless network card at 0000:01:0d.0, irq:11, phymem1:0xFF8FE000, phymem2:0xFF8C0000, mem1:0xe0998000, mem1_size:8192, mem2:0xe0b00000, mem2_size:131072
[   43.653427] acx: loading firmware for acx1111 chipset with radio ID 16
[   47.183651] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   47.184413] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
[   47.184496] usbcore: registered new interface driver acx_usb
[ 2336.267420]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[ 2336.267488]  [<e0accf90>] acx_e_after_interrupt_task+0x0/0x440 [acx]
[ 2336.267504]  [<e0aca736>] acx_s_cmd_start_scan+0xc6/0x100 [acx]
[ 2336.267538]  [<e0acd179>] acx_e_after_interrupt_task+0x1e9/0x440 [acx]
[ 6886.024320]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[ 6886.024387]  [<e0accf90>] acx_e_after_interrupt_task+0x0/0x440 [acx]
[ 6886.024403]  [<e0aca736>] acx_s_cmd_start_scan+0xc6/0x100 [acx]
[ 6886.024437]  [<e0acd179>] acx_e_after_interrupt_task+0x1e9/0x440 [acx]
[ 7348.035417]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[ 7348.035483]  [<e0accf90>] acx_e_after_interrupt_task+0x0/0x440 [acx]
[ 7348.035500]  [<e0aca736>] acx_s_cmd_start_scan+0xc6/0x100 [acx]
[ 7348.035533]  [<e0acd179>] acx_e_after_interrupt_task+0x1e9/0x440 [acx]
[10185.294193]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[10185.294260]  [<e0accf90>] acx_e_after_interrupt_task+0x0/0x440 [acx]
[10185.294276]  [<e0aca736>] acx_s_cmd_start_scan+0xc6/0x100 [acx]
[10185.294310]  [<e0acd179>] acx_e_after_interrupt_task+0x1e9/0x440 [acx]
[13605.220699]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[13605.220772]  [<e0accf90>] acx_e_after_interrupt_task+0x0/0x440 [acx]
[13605.220788]  [<e0aca736>] acx_s_cmd_start_scan+0xc6/0x100 [acx]
[13605.220822]  [<e0acd179>] acx_e_after_interrupt_task+0x1e9/0x440 [acx]
[14740.804684]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[14740.804749]  [<e0accf90>] acx_e_after_interrupt_task+0x0/0x440 [acx]
[14740.804765]  [<e0aca736>] acx_s_cmd_start_scan+0xc6/0x100 [acx]
[14740.804799]  [<e0acd179>] acx_e_after_interrupt_task+0x1e9/0x440 [acx]
[18479.739157]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[18479.739224]  [<e0accf90>] acx_e_after_interrupt_task+0x0/0x440 [acx]
[18479.739240]  [<e0aca736>] acx_s_cmd_start_scan+0xc6/0x100 [acx]
[18479.739273]  [<e0acd179>] acx_e_after_interrupt_task+0x1e9/0x440 [acx]
[20461.042758]  [<e0ad2c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
[20461.042829]  [<e0ac88e0>] acx_ioctl_commit+0x0/0x40 [acx]
[20461.042847]  [<e0acc303>] acx_s_update_card_settings+0x683/0xd10 [acx]
[20461.042962]  [<e0ac88e0>] acx_ioctl_commit+0x0/0x40 [acx]
[20461.042980]  [<e0ac8908>] acx_ioctl_commit+0x28/0x40 [acx]
[20461.043067]  [<e0ac8920>] acx_ioctl_set_freq+0x0/0xe0 [acx]
[20461.043084]  [<e0ac8920>] acx_ioctl_set_freq+0x0/0xe0 [acx]
```

lshw:
```
*-network:1
description: Wireless interface
product: ACX 111 54Mbps Wireless Interface
vendor: Texas Instruments
physical id: d
bus info: pci@0000:01:0d.0
logical name: wlan0
version: 00
serial: 00:40:f4:c7:f9:92
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical wireless
configuration: broadcast=yes driver=acx_pci latency=64 module=acx promiscuous=yes wireless=IEEE 802.11b+/g+

```

ifconfig:
```
wlan0     Link encap:UNSPEC  HWaddr 00-40-F4-C7-F9-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe000 
```
(I don't know why the MAC shows up wrong, perhaps this is a clue?)

---

### Post by dmizer on 2008-07-24
try ndiswrapper instead.  it gets better speed and works with wpa encrypted networks.  step by step (copy paste) directions here: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

---

### Post by mdnielsen on 2008-07-24
I would, but I want to use this card for monitoring traffic for wireless security ;) As far as I understand, I need the acx for that and cannot use ndis.

---

### Post by dmizer on 2008-07-24
> **mdnielsen said:**
> I would, but I want to use this card for monitoring traffic for wireless security ;) As far as I understand, I need the acx for that and cannot use ndis.

well, while this is true the acx module has been flaky as long as i can remember (pre breezy at least).  the only way i've ever been able to make this card work reliably and consistently is by using ndiswrapper.

might try simple things, like rebooting the router.

---

### Post by mdnielsen on 2008-07-24
Ok, this is a bit embarrassing. Amateur mistake.... The MAC address was really bothering me, so I just moved PCI slots to see if that was the problem. Works great. Thanks for your help.

---

### Post by dmizer on 2008-07-24
> **mdnielsen said:**
> Ok, this is a bit embarrassing. Amateur mistake.... The MAC address was really bothering me, so I just moved PCI slots to see if that was the problem. Works great. Thanks for your help.

wow, well ... at least it wasn't a difficult fix. :KS

---

