---
title: "wifi networks device not ready -- RT2800"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by tara_ons on 2015-04-30
Ubuntu is installed with wifi networks device not ready.

**uname -r**
3.16.0-36-generic

**lspci -nnk | grep -iA2 net **
```
 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06) 
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432] 
     Kernel driver in use: r8169 
 04:05.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601] 
    Subsystem: Ralink corp. Device [1814:2860] 
    Kernel driver in use: rt2800pci 

```
 **iwconfig **
 ```
eth0      no wireless extensions. 

 wlan0     IEEE 802.11bgn  ESSID: off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
           Retry short limit:7   RTS thr: off   Fragment thr: off 
           Power Management: off 
            
 lo        no wireless extensions.
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 20:cf:30:93:d3:4b  
          inet addr:192.168.128.102  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe93:d34b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21712673 (21.7 MB)  TX bytes:1664377 (1.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:285603 (285.6 KB)  TX bytes:285603 (285.6 KB)

```

 

 **rfkill list **
```
 0: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
```
 

 **lsmod** 
 ```
Module                  Size  Used by 
 rfcomm                 69509  0  
 bnep                   19624  2  
 bluetooth             446409  10 bnep,rfcomm 
 6lowpan_iphc           18702  1 bluetooth 
 radeon               1412941  3  
 snd_hda_codec_realtek    77467  1  
 snd_hda_codec_hdmi     47548  1  
 snd_hda_codec_generic    68972  1 snd_hda_codec_realtek 
 snd_hda_intel          30469  5  
 snd_hda_controller     30228  1 snd_hda_intel 
 snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller 
 snd_hwdep              17698  1 snd_hda_codec 
 snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller 
 snd_seq_midi           13564  0  
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_rawmidi            30876  1 snd_seq_midi 
 arc4                   12608  2  
 kvm_amd                60328  0  
 rt2800pci              13630  0  
 rt2800mmio             20986  1 rt2800pci 
 rt2800lib              89076  2 rt2800pci,rt2800mmio 
 rt2x00pci              13287  1 rt2800pci 
 rt2x00mmio             13603  2 rt2800pci,rt2800mmio 
 kvm                   452043  1 kvm_amd 
 rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio 
 mac80211              652718  3 rt2x00lib,rt2x00pci,rt2800lib 
 snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi 
 edac_core              56549  0  
 cfg80211              494362  2 mac80211,rt2x00lib 
 serio_raw              13483  0  
 edac_mce_amd           22578  0  
 k10temp                13144  0  
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi 
 eeprom_93cx6           13344  1 rt2800pci 
 crc_ccitt              12707  1 rt2800lib 
 snd_timer              29562  2 snd_pcm,snd_seq 
 snd                    79468  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device 
 i2c_piix4              22166  0  
 ttm                    93588  1 radeon 
 soundcore              15047  2 snd,snd_hda_codec 
 drm_kms_helper         61574  1 radeon 
 asus_atk0110           18666  0  
 tpm_infineon           17131  0  
 drm                   311018  6 ttm,drm_kms_helper,radeon 
 i2c_algo_bit           13413  1 radeon 
 wmi                    19193  0  
 shpchp                 37047  0  
 mac_hid                13227  0  
 parport_pc             32741  1  
 ppdev                  17671  0  
 lp                     17759  0  
 parport                42348  3 lp,ppdev,parport_pc 
 hid_generic            12559  0  
 usbhid                 52616  0  
 hid                   110426  2 hid_generic,usbhid 
 pata_acpi              13053  0  
 r8169                  71694  0  
 psmouse               106561  0  
 ahci                   34062  2  
 libahci                32424  1 ahci 
 pata_atiixp            13279  0  
 pata_via               13677  0  
 mii                    13934  1 r8169 
```
 

 **nm-tool **
  
 ```
NetworkManager Tool 
  
 State: connected (global) 
  
 - Device: wlan0 ---------------------------------------------------------------- 
   Type:              802.11 WiFi 
   Driver:            rt2800pci 
   State:             unavailable 
   Default:           no 
   HW Address:        D2: FB: D0 :0F: 86: FA 
  
   Capabilities: 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points  
  
  
 - Device: eth0  [Wired connection 1] ------------------------------------------- 
   Type:              Wired 
   Driver:            r8169 
   State:             connected 
   Default:           yes 
   HW Address:        20:CF:30:93: D3:4B 

  
   Capabilities: 
     Carrier Detect:  yes 
     Speed:           100 Mb/s 
  
   Wired Properties 
     Carrier:         on 
  
   IPv4 Settings: 
     Address:         192.168.128.102 
     Prefix:          24 (255.255.255.0) 
     Gateway:         192.168.128.1 
  
     DNS:             208.67.222.222 
     DNS:             208.67.220.220
```

Please help.

---

### Post by tara_ons on 2015-04-30
**Hardware information: **
**lshw -C network **

 ```
  *-network                
        description: Ethernet interface 

        product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        logical name: eth0 
        version: 06 
        serial: 20: cf:30:93:d3:4b 

        size: 100Mbit/s 
        capacity: 1Gbit/s 

        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-1.fw ip=192.168.128.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
        resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff 
   *-network **DISABLED **

        description: Wireless interface 

        product: RT2800 802.11n PCI 
        vendor: Ralink corp. 
        physical id: 5 
        bus info: pci@0000:04:05.0 

        logical name: wlan0 
        version: 00 
        serial: 82:1f:e5: cf:33:85 

        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=rt2800pci driverversion=3.16.0-36-generic firmware=0.34 latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:20 memory:feb00000-feb0ffff
```

---

### Post by Elfy on 2015-04-30
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

It's likely to help those who'll be able to do so if you pop by this [post]("http://ubuntuforums.org/showthread.php?t=370108&p=2210334&viewfull=1#post2210334") 

Follow the instructions to grab and run the wireless script.

---

### Post by tara_ons on 2015-04-30
I have run the wireless script and have attached the wireless-info.tar.gz file.

---

### Post by tara_ons on 2015-05-02
I have run the wireless script and have attached the results in the previous reply.

dmesg is as follows :
```

[  113.069759] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  113.069775] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  113.598499] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  113.598514] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  114.131193] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  114.131209] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  114.651880] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  114.651895] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  115.184558] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  115.184573] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  115.665159] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  115.665166] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  116.185902] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  116.185916] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  116.714598] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  116.714613] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  117.239288] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  117.239303] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  117.759973] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  117.759989] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  118.284658] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  118.284673] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  118.813356] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  118.813371] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  119.330034] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  119.330047] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  119.850719] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  119.850734] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  120.359392] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  120.359407] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  120.872066] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  120.872081] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  121.388758] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  121.388773] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  121.893408] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  121.893423] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  122.402072] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  122.402086] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  122.930748] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  122.930760] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  123.439440] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  123.439454] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  123.952114] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  123.952126] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  124.468794] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  124.468808] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  124.973449] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  124.973461] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  125.478121] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  125.478134] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  125.982785] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  125.982796] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  126.491471] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  126.491483] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  126.996114] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  126.996128] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  127.496751] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  127.496765] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  128.001443] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  128.001458] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  128.502099] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  128.502113] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  128.998743] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  128.998757] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  129.519439] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  129.519455] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  130.032150] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  130.032164] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  130.532772] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  130.532789] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  131.049493] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  131.049509] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  131.562085] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  131.562102] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  132.074799] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  132.074816] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  132.583451] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  132.583467] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  133.096117] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  133.096133] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  133.604804] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  133.604819] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  134.117477] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  134.117489] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  134.626159] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  134.626176] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  135.130820] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  135.130835] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  135.639479] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  135.639493] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  136.136131] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  136.136145] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  136.644800] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  136.644813] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  137.149471] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  137.149485] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  137.650122] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  137.650134] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  138.154794] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  138.154809] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

```

Kindly please help to fix this problem.

---

### Post by Elfy on 2015-05-04
bump

---

### Post by wildmanne39 on 2015-05-04
I think we may have to compile a new driver with all those errors, but first do you have wireless enable in network manger? I ask because it is not even scanning.
Thanks

---

### Post by wildmanne39 on 2015-05-04
I have been researching you have two error messages, one is a kernel error and the other is a driver error, So I guess we should try a new kernel and hopefully that will fix both issues.
Download these packages one line at a time:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.3-vivid/linux-headers-3.18.3-031803_3.18.3-031803.201501161810_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.3-vivid/linux-headers-3.18.3-031803-generic_3.18.3-031803.201501161810_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.3-vivid/linux-image-3.18.3-031803-generic_3.18.3-031803.201501161810_amd64.deb

```
Then install them:
```
sudo dpkg -i linux-headers-3.18.3*.deb linux-image-3.18.3*.deb
```
Then update grub and reboot then select the new kernel:
```
sudo update-grub
sudo reboot
```
with this driver we may have to still set a driver parameter or two, if it does not connect post a new file from the wireless script.
Thanks

---

### Post by tara_ons on 2015-05-06
When I try to install the packages, it says "Possible missing firmware /lib/firmware/rtl_nic/rtl8107e-2.fw for module r8169"

```

Selecting previously unselected package linux-headers-3.18.3-031803.
(Reading database ... 350667 files and directories currently installed.)
Preparing to unpack linux-headers-3.18.3-031803_3.18.3-031803.201501161810_all.deb ...
Unpacking linux-headers-3.18.3-031803 (3.18.3-031803.201501161810) ...
Selecting previously unselected package linux-headers-3.18.3-031803-generic.
Preparing to unpack linux-headers-3.18.3-031803-generic_3.18.3-031803.201501161810_amd64.deb ...
Unpacking linux-headers-3.18.3-031803-generic (3.18.3-031803.201501161810) ...
Selecting previously unselected package linux-image-3.18.3-031803-generic.
Preparing to unpack linux-image-3.18.3-031803-generic_3.18.3-031803.201501161810_amd64.deb ...
Done.
Unpacking linux-image-3.18.3-031803-generic (3.18.3-031803.201501161810) ...
Setting up linux-headers-3.18.3-031803 (3.18.3-031803.201501161810) ...
Setting up linux-headers-3.18.3-031803-generic (3.18.3-031803.201501161810) ...
Setting up linux-image-3.18.3-031803-generic (3.18.3-031803.201501161810) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
update-initramfs: Generating /boot/initrd.img-3.18.3-031803-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8107e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8107e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168h-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168h-1.fw for module r8169
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.18.3-031803-generic
Found initrd image: /boot/initrd.img-3.18.3-031803-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found initrd image: /boot/initrd.img-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by wildmanne39 on 2015-05-06
Is your ethernet working? that is what the firmware is for.
Did that help with your wireless issue?
If you cannot connect with wifi, please click on wireless script in my signature and post the file it creates here using code tags.
Thanks

---

### Post by tara_ons on 2015-05-06
I have updated grub as you mentioned.
I still have the same problem.

```


########## wireless info START ##########

Report from: 07 May 2015 11:40 KST +0900

Booted last: 07 May 2015 11:40 KST +0900

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169

04:05.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Ralink corp. Device [1814:2860]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800pci              13674  0 
rt2800mmio             21082  1 rt2800pci
rt2800lib              95583  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13661  2 rt2800pci,rt2800mmio
rt2x00lib              56113  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              697212  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              520257  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19379  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.128.102  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe93:d34b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27268 (27.2 KB)  TX bytes:26590 (26.5 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.128.1   0.0.0.0         UG    0      0        0 eth0
192.168.128.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.128.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.128.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Asia/Seoul (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     3FF1176BB7F7770CA8BC1EE
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5E8DE289EF26F4FFC0BAE56
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     5A3FAD96F0E24DA9DF06D17
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2AE29A8EC35C16DFCABA32E
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B297AFAD070E693659C4908
depends:        rt2x00lib
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BA57869D6451486D8D7903E
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.18.3-031803-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F2E189013C3BA380B28AA09
depends:        cfg80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.18.3-031803-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   56.544726] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   56.544733] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   56.913377] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   56.913384] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   57.282038] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   57.282044] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   57.650714] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   57.650720] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   58.019354] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   58.019361] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   58.388017] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   58.388024] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   58.756728] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   58.756745] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   59.125353] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   59.125360] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   59.498049] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   59.498056] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   59.866715] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   59.866722] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   60.235389] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   60.235395] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   60.604042] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   60.604046] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   60.976716] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   60.976721] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   61.345387] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   61.345391] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   61.714055] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   61.714059] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   62.082725] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   62.082729] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   62.451404] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   62.451411] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   62.820065] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   62.820072] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   63.196758] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   63.196764] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   63.573430] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   63.573436] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   63.950103] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   63.950109] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   64.326794] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   64.326799] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   64.703464] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   64.703472] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   65.080162] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   65.080169] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   65.448833] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   65.448839] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   65.817489] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   65.817495] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   66.186155] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   66.186160] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   66.554825] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   66.554831] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   66.923514] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   66.923518] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   67.288151] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   67.288157] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   67.656818] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   67.656824] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   68.025497] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   68.025503] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   68.410178] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   68.410183] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   68.778846] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   68.778849] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   69.147511] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   69.147515] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   69.516180] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   69.516184] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   69.884856] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   69.884860] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   70.253524] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   70.253528] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   70.622183] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   70.622187] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   70.990874] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   70.990879] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   71.359504] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   71.359510] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   71.728180] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   71.728185] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   72.096873] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   72.096879] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   72.417439] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   72.417446] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   72.786154] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   72.786161] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   73.158777] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   73.158782] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   73.527446] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   73.527453] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   73.896123] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   73.896128] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   74.264796] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   74.264804] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   74.641588] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   74.641595] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

########## wireless info END ############


```

Thanks...

---

### Post by wildmanne39 on 2015-05-06
Please do:
```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
it looks like you are in Asia and your router is set to U.S.
if you are in Asia then:
Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set US
```Of course, substitute your country code if not United States. 
Set it permanently:
```
gksudo gedit /etc/default/crda
```Use whatever text editor you have installed if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=your country code
```Proofread carefully, save and close the text editor.
If this does not work which I do not think it will at this point we can compile just a new driver.
After you do everything above reboot your router and remove your wifi connection in network manager and reboot the computer.

---

### Post by tara_ons on 2015-05-07
Still the same problem...

```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf

options rt2800pci nohwcrypt=1

```

```

sudo modprobe -rfv rt2800pci

rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod crc_ccitt
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211

```

```

sudo modprobe -v rt2800pci

insmod /lib/modules/3.18.3-031803-generic/kernel/lib/crc-ccitt.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/net/wireless/cfg80211.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/net/mac80211/mac80211.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
insmod /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko nohwcrypt=1

```

```

sudo iw reg set KR

```

```

gksudo gedit /etc/default/crda

```

I edited to KR in crda.

Thanks...

---

### Post by tara_ons on 2015-05-07
sudo cat /var/log/syslog | grep -e firmware -e wlan | tail -n45 results the following:

```

sudo cat /var/log/syslog | grep -e firmware -e wlan | tail -n45

May  7 14:35:24 tara-ons wpa_supplicant[899]: wlan0: Failed to initialize driver interface
May  7 14:35:24 tara-ons NetworkManager[796]: <error> [1430976924.979431] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
May  7 14:35:24 tara-ons NetworkManager[796]: <info> (wlan0): supplicant interface state: starting -> down
May  7 14:35:25 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:25 tara-ons wpa_supplicant[899]: nl80211: Could not set interface 'wlan0' UP
May  7 14:35:25 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:25 tara-ons wpa_supplicant[899]: WEXT: Could not set interface 'wlan0' UP
May  7 14:35:25 tara-ons wpa_supplicant[899]: wlan0: Failed to initialize driver interface
May  7 14:35:25 tara-ons NetworkManager[796]: <error> [1430976925.719558] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
May  7 14:35:25 tara-ons NetworkManager[796]: <info> (wlan0): supplicant interface state: starting -> down
May  7 14:35:26 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:26 tara-ons wpa_supplicant[899]: nl80211: Could not set interface 'wlan0' UP
May  7 14:35:26 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:26 tara-ons wpa_supplicant[899]: WEXT: Could not set interface 'wlan0' UP
May  7 14:35:26 tara-ons wpa_supplicant[899]: wlan0: Failed to initialize driver interface
May  7 14:35:26 tara-ons NetworkManager[796]: <error> [1430976926.459564] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
May  7 14:35:26 tara-ons NetworkManager[796]: <info> (wlan0): supplicant interface state: starting -> down
May  7 14:35:26 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:26 tara-ons wpa_supplicant[899]: nl80211: Could not set interface 'wlan0' UP
May  7 14:35:27 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:27 tara-ons wpa_supplicant[899]: WEXT: Could not set interface 'wlan0' UP
May  7 14:35:27 tara-ons wpa_supplicant[899]: wlan0: Failed to initialize driver interface
May  7 14:35:27 tara-ons NetworkManager[796]: <error> [1430976927.203535] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
May  7 14:35:27 tara-ons NetworkManager[796]: <info> (wlan0): supplicant interface state: starting -> down
May  7 14:35:27 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:27 tara-ons wpa_supplicant[899]: nl80211: Could not set interface 'wlan0' UP
May  7 14:35:27 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:27 tara-ons wpa_supplicant[899]: WEXT: Could not set interface 'wlan0' UP
May  7 14:35:27 tara-ons wpa_supplicant[899]: wlan0: Failed to initialize driver interface
May  7 14:35:27 tara-ons NetworkManager[796]: <error> [1430976927.947527] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
May  7 14:35:27 tara-ons NetworkManager[796]: <info> (wlan0): supplicant interface state: starting -> down
May  7 14:35:28 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:28 tara-ons wpa_supplicant[899]: nl80211: Could not set interface 'wlan0' UP
May  7 14:35:28 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:28 tara-ons wpa_supplicant[899]: WEXT: Could not set interface 'wlan0' UP
May  7 14:35:28 tara-ons wpa_supplicant[899]: wlan0: Failed to initialize driver interface
May  7 14:35:28 tara-ons NetworkManager[796]: <error> [1430976928.687466] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
May  7 14:35:28 tara-ons NetworkManager[796]: <info> (wlan0): supplicant interface state: starting -> down
May  7 14:35:29 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:29 tara-ons wpa_supplicant[899]: nl80211: Could not set interface 'wlan0' UP
May  7 14:35:29 tara-ons wpa_supplicant[899]: Could not set interface wlan0 flags (UP): Input/output error
May  7 14:35:29 tara-ons wpa_supplicant[899]: WEXT: Could not set interface 'wlan0' UP
May  7 14:35:29 tara-ons wpa_supplicant[899]: wlan0: Failed to initialize driver interface
May  7 14:35:29 tara-ons NetworkManager[796]: <error> [1430976929.431560] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
May  7 14:35:29 tara-ons NetworkManager[796]: <info> (wlan0): supplicant interface state: starting -> down

```

---

### Post by wildmanne39 on 2015-05-07
Download the file below to your desktop:
Right click it and select Extract Here. Now open a terminal and do:
```
sudo apt-get install build-essential linux-headers-generic
cd ~/Desktop/backports-4.1-rc1-1
make defconfig-wifi
make
sudo make install
```
Watch for error, this may take a few minutes.
[https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1-rc1/backports-4.1-rc1-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1-rc1/backports-4.1-rc1-1.tar.gz)

---

### Post by tara_ons on 2015-05-07
```

sudo make install

Building modules, stage 2.
  MODPOST 122 modules
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/compat/compat.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/compat/cordic.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/bcma/bcma.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/usb/cdc_ether.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/usb/cdc_ncm.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/usb/rndis_host.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/usb/usbnet.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/adm8211.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/airo.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/airo_cs.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/at76c50x-usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ar5523/ar5523.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath10k/ath10k_core.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath5k/ath5k.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath6kl/ath6kl_core.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath9k/ath9k.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath9k/ath9k_common.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/carl9170/carl9170.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/wcn36xx/wcn36xx.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ath/wil6210/wil6210.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/atmel.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/atmel_cs.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/atmel_pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/b43/b43.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/b43legacy/b43legacy.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/cw1200/cw1200_core.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/cw1200/cw1200_wlan_sdio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/cw1200/cw1200_wlan_spi.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ipw2x00/ipw2100.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ipw2x00/ipw2200.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ipw2x00/libipw.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/iwlegacy/iwl3945.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/iwlegacy/iwl4965.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/iwlegacy/iwlegacy.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/iwlwifi/iwlwifi.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/libertas/libertas.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/libertas/libertas_cs.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/libertas/libertas_sdio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/libertas/libertas_spi.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/libertas/usb8xxx.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/libertas_tf/libertas_tf.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/mac80211_hwsim.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/mwifiex/mwifiex.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/mwifiex/mwifiex_pcie.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/mwifiex/mwifiex_sdio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/mwifiex/mwifiex_usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/mwl8k.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/orinoco.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/orinoco_cs.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/orinoco_nortel.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/orinoco_pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/orinoco_plx.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/orinoco_tmd.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/orinoco_usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/orinoco/spectrum_cs.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/p54/p54common.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/p54/p54pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/p54/p54spi.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/p54/p54usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rndis_wlan.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rsi/rsi_91x.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rsi/rsi_sdio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rsi/rsi_usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2400pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2500pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2500usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2800lib.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2800mmio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2800pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2800usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2x00lib.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2x00mmio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2x00pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt2x00usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt61pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rt2x00/rt73usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtl818x/rtl8180/rtl818x_pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8192ee/rtl8192ee.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl_pci.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtl_usb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wl1251/wl1251.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wl1251/wl1251_sdio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wl1251/wl1251_spi.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wl12xx/wl12xx.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wl18xx/wl18xx.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wlcore/wlcore.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wlcore/wlcore_sdio.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/ti/wlcore/wlcore_spi.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/zd1201.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/net/wireless/zd1211rw/zd1211rw.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/drivers/ssb/ssb.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/net/wireless/cfg80211.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/net/wireless/lib80211.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/net/wireless/lib80211_crypt_ccmp.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/net/wireless/lib80211_crypt_tkip.ko
Can't read private key
  INSTALL /home/tara/Desktop/backports-4.1-rc1-1/net/wireless/lib80211_crypt_wep.ko
Can't read private key
  DEPMOD  3.18.3-031803-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

```

After reboot, wireless script reports as follows :
```


########## wireless info START ##########

Report from: 07 May 2015 16:44 KST +0900

Booted last: 07 May 2015 16:42 KST +0900

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169

04:05.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Ralink corp. Device [1814:2860]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800pci              13622  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              88867  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55250  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              631323  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              529038  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
compat                 22650  3 cfg80211,mac80211,rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19379  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.128.102  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe93:d34b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:633710 (633.7 KB)  TX bytes:130367 (130.3 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.128.1   0.0.0.0         UG    0      0        0 eth0
192.168.128.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.128.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.128.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Asia/Seoul (based on set time zone)

country KR:
    (2402 - 2482 @ 20), (N/A, 20)
    (5170 - 5250 @ 20), (3, 20)
    (5250 - 5330 @ 20), (3, 20), DFS
    (5490 - 5630 @ 20), (3, 30), DFS
    (5735 - 5815 @ 20), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.18.3-031803-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko
version:        backported from Linux (v4.1-rc1-0-gb787f68c3) using backports v4.1-rc1-1-0-g3fade66
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     74D551E569485AC5E51A416
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,compat,eeprom_93cx6
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.18.3-031803-generic/updates/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4A28F78F1DD3DB9D4ED990F
depends:        rt2800lib,rt2x00lib,rt2x00mmio
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/3.18.3-031803-generic/updates/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     077C312F8E09ABDF8DB6C3F
depends:        rt2x00lib,mac80211,crc-ccitt
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 

[rt2x00pci]
filename:       /lib/modules/3.18.3-031803-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8F1DF35A56BE3AAEFD8F696
depends:        rt2x00lib,mac80211
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 

[rt2x00mmio]
filename:       /lib/modules/3.18.3-031803-generic/updates/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B033E1300B1027A953F9543
depends:        rt2x00lib
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/3.18.3-031803-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F1E0981107E5741699AB9BC
depends:        mac80211,cfg80211
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.18.3-031803-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.1-rc1-0-gb787f68c3) using backports v4.1-rc1-1-0-g3fade66
srcversion:     B15AB37082B88116112C794
depends:        cfg80211,compat
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.18.3-031803-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.1-rc1-0-gb787f68c3) using backports v4.1-rc1-1-0-g3fade66
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7362865D6030E016900407B
depends:        compat
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[  110.373330] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  110.373344] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  110.713604] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  110.713619] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  111.049881] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  111.049896] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  111.390236] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  111.390264] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  111.726428] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  111.726445] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  112.066737] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  112.066751] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  112.402969] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  112.402985] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  112.743243] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  112.743259] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  113.083473] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  113.083492] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  113.423805] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  113.423821] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  113.760015] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  113.760023] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  114.100361] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  114.100387] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  114.440560] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  114.440576] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  114.780840] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  114.780856] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  115.117173] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  115.117189] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  115.453490] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  115.453508] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  115.789697] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  115.789713] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  116.133999] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  116.134016] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  116.470244] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  116.470260] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  116.806592] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  116.806609] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  117.142858] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  117.142874] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  117.487062] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  117.487078] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  117.823362] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  117.823379] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  118.163625] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  118.163634] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  118.499921] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  118.499935] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  118.840194] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  118.840209] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  119.184469] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  119.184485] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  119.524751] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  119.524765] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  119.869014] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  119.869029] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  120.209300] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  120.209315] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  120.553575] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  120.553589] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  120.893831] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  120.893845] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  121.238135] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  121.238150] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  121.578409] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  121.578423] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  121.922690] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  121.922704] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  122.262964] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  122.262981] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  122.607244] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  122.607260] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  122.947525] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  122.947540] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  123.291843] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  123.291857] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  123.632092] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  123.632106] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  123.976358] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  123.976373] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  124.316650] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  124.316665] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  124.664957] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  124.664972] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  124.917131] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  124.917146] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  125.253390] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  125.253404] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  125.593641] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  125.593655] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  125.929990] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  125.930006] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  126.270212] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  126.270228] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  126.606488] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  126.606504] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  126.946768] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[  126.946784] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

########## wireless info END ############

```

Thanks...

---

### Post by wildmanne39 on 2015-05-07
If you have not already rebooted please do so now.

---

### Post by tara_ons on 2015-05-07
I have rebooted but

```

##### dmesg #############################

[   33.288746] ieee80211 phy0: rt2800_wait_bbp_rf_ready: Error - BBP/RF register access failed, aborting
[   33.288750] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

```

---

### Post by wildmanne39 on 2015-05-07
I Will look again tomorrow it is very late here.

---

### Post by tara_ons on 2015-05-07
Sure...
Thanks for all your time...

---

### Post by wildmanne39 on 2015-05-07
Are you running wicd instead of network manager? Need to check and make sure wireless is enabled in whichever one you are using.
Your ethernet needs to be unplugged or disables while trying to use wireless.
Thanks

---

### Post by tara_ons on 2015-05-07
I am very new to ubuntu.
wicd is not installed in my machine. 

```

wicd

The program 'wicd' is currently not installed. You can install it by typing:
sudo apt-get install wicd-daemon

```

---

### Post by wildmanne39 on 2015-05-07
Please post the output of:
```
ps aux | grep nm-apple

```
Thanks

---

### Post by tara_ons on 2015-05-08
```

ps aux | grep nm-apple

tara   2060  0.0  0.7 594528 29912 ?        Sl   12:36   0:00 nm-applet
tara   3471  0.0  0.0  17168  2460 pts/10   S+   12:58   0:00 grep --color=auto nm-apple

```

Thanks...

---

### Post by wildmanne39 on 2015-05-08
Go to the top right corner of the screen click on network manager icon  and make sure wireless is enabled. 
Your ethernet needs to be unplugged or disabled while trying to use wireless.
Thanks

---

### Post by tara_ons on 2015-05-08
Kindly please check the attached image.

---

### Post by wildmanne39 on 2015-05-08
Was it already checked? click on edit connection, is wireless set up? Are other wireless devices connected to your router? is wireless enabled in the router?
Thanks

---

### Post by tara_ons on 2015-05-08
In the same n/w, a fedora m/c works fine.
I have run the wireless script in that m/c and it reports as follows. 
But some of the commands are not directly applicable in fedora. So I changed the relevant commands.

```

########## wireless info START ##########

Report from: 08 May 2015 15:11 KST +0900

Booted last: 07 May 2015 16:28 KST +0900

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Fedora
Description:    Fedora release 15 (Lovelock)
Release:    15
Codename:    Lovelock

##### kernel ############################

Linux 2.6.41.1-1.fc15.x86_64 #1 SMP Fri Nov 11 21:36:28 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

ro, rd_LVM_LV=vg_lovelock/lv_root, rd_LVM_LV=vg_lovelock/lv_swap, rd_NO_LUKS, rd_NO_MD, rd_NO_DM, LANG=en_US.UTF-8, SYSFONT=latarcyrheb-sun16, KEYTABLE=us, rhgb, quiet

##### desktop ###########################

LXDE

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169

03:06.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Ralink corp. Device [1814:2860]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 192f:0616 Avago Technologies, Pte. 

##### PCMCIA card info ##################

##### rfkill ############################

./wireless-info: line 176: rfkill: command not found

##### lsmod #############################

rt2800pci               9507  0 
rt2800lib              39527  1 rt2800pci
crc_ccitt               1557  1 rt2800lib
rt2x00pci               5768  1 rt2800pci
rt2x00lib              46254  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              251806  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              151157  2 rt2x00lib,mac80211
rfkill                 16336  3 bluetooth,cfg80211
eeprom_93cx6            1647  1 rt2800pci
wmi                     9049  0 

##### interfaces ########################

default 0.0.0.0
loopback 127.0.0.0
link-local 169.254.0.0

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:42 

vboxnet0  Link encap:Ethernet  HWaddr <MAC 'vboxnet0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:9fff:fef0:daa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:243376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:432785033 (412.7 MiB)  TX bytes:33355037 (31.8 MiB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"XXXXXX"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'XXXXXX' [AN3]>   
          Bit Rate=115.6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:926  Invalid misc:124   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

##### resolv.conf #######################

domain netis
search netis
nameserver 147.46.80.1
nameserver 147.46.37.10

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [XXXXXX] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           115 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
        XXXXXX:         Infra, <MAC 'XXXXXX' [AN3]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 60 WPA2
  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             147.46.80.1
    DNS:             147.46.37.10

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifcfg-rh

##### NetworkManager profiles ###########

##### iw reg get ########################

country KR:
    (2402 - 2482 @ 20), (N/A, 20)
    (5170 - 5250 @ 20), (3, 20)
    (5250 - 5330 @ 20), (3, 20), DFS
    (5490 - 5630 @ 20), (3, 30), DFS
    (5735 - 5815 @ 20), (3, 30)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

vboxnet0  no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 04:8D:38:75:FE:20
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=40/70  Signal level=-70 dBm 
                    Encryption key:on
                    ESSID:"XXXXXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001be3bf50320
                    Extra: Last beacon: 23145ms ago
                    IE: Unknown: 0006534E55564C32
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000600000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C430F000000

vboxnet0  Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/2.6.41.1-1.fc15.x86_64/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C7DAC4A6EC3BFB7F64FC205
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
vermagic:       2.6.41.1-1.fc15.x86_64 SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800lib]
filename:       /lib/modules/2.6.41.1-1.fc15.x86_64/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     8AC93CEF8CA0A249613AB49
depends:        crc-ccitt,rt2x00lib,mac80211
vermagic:       2.6.41.1-1.fc15.x86_64 SMP mod_unload 

[rt2x00pci]
filename:       /lib/modules/2.6.41.1-1.fc15.x86_64/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     07853DB793C85056162CD47
depends:        rt2x00lib,mac80211
vermagic:       2.6.41.1-1.fc15.x86_64 SMP mod_unload 

[rt2x00lib]
filename:       /lib/modules/2.6.41.1-1.fc15.x86_64/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4343E02741086B49D8403E5
depends:        mac80211,cfg80211
vermagic:       2.6.41.1-1.fc15.x86_64 SMP mod_unload 

[mac80211]
filename:       /lib/modules/2.6.41.1-1.fc15.x86_64/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0FCA42DC5F1ED7195D9E23E
depends:        cfg80211
vermagic:       2.6.41.1-1.fc15.x86_64 SMP mod_unload 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[cfg80211]
filename:       /lib/modules/2.6.41.1-1.fc15.x86_64/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     957BED1D79F8EEF52A98E6E
depends:        rfkill
vermagic:       2.6.41.1-1.fc15.x86_64 SMP mod_unload 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

grep: /etc/modules: No such file or directory

##### modprobe options ##################

[/etc/modprobe.d/blacklist.conf]
blacklist i8xx_tco
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist i810fb
blacklist cirrusfb
blacklist intelfb
blacklist kyrofb
blacklist i2c-matroxfb
blacklist hgafb
blacklist nvidiafb
blacklist rivafb
blacklist savagefb
blacklist sstfb
blacklist neofb
blacklist tridentfb
blacklist tdfxfb
blacklist virgefb
blacklist vga16fb
blacklist viafb
blacklist hisax
blacklist hisax_fcpcipnp
blacklist snd-pcsp
blacklist chsc_sch

[/etc/modprobe.d/dist-alsa.conf]
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && /sbin/modprobe snd-seq

[/etc/modprobe.d/dist.conf]
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout
alias block-major-1-* rd
alias block-major-3-* ide-probe-mod
alias block-major-8-* sd_mod
alias block-major-9-* md
alias block-major-11-* sr_mod
alias block-major-13-* xd
alias block-major-15-* cdu31a
alias block-major-16-* gscd
alias block-major-17-* optcd
alias block-major-18-* sjcd
alias block-major-20-* mcdx
alias block-major-22-* ide-probe-mod
alias block-major-23-* mcd
alias block-major-24-* sonycd535
alias block-major-25-* sbpcd
alias block-major-26-* sbpcd
alias block-major-27-* sbpcd
alias block-major-29-* aztcd
alias block-major-32-* cm206
alias block-major-33-* ide-probe-mod
alias block-major-34-* ide-probe-mod
alias block-major-37-* ide-tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide-probe-mod
alias block-major-57-* ide-probe-mod
alias block-major-88-* ide-probe-mod
alias block-major-89-* ide-probe-mod
alias block-major-90-* ide-probe-mod
alias block-major-91-* ide-probe-mod
alias block-major-93-* nftl
alias block-major-113-* viocd
alias char-major-4-* serial
alias char-major-5-* serial
alias char-major-9-* st
alias char-major-10-2 msbusmouse
alias char-major-10-3 atixlmouse
alias char-major-10-135 rtc
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-175 agpgart
alias char-major-10-250 hci_vhci
alias char-major-13-* input
alias char-major-13-0 joydev
alias char-major-13-32 mousedev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* zftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-36-* netlink
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm-mod
alias char-major-188-* usbserial
alias char-major-200-* vxspec
alias char-major-206-* osst
alias char-major-216-* rfcomm
alias dos msdos
alias dummy0 dummy
alias dummy1 dummy
alias iso9660 isofs
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-17 af_packet
alias netalias-2 ip_alias
alias irlan0 irlan
alias irda-dongle-0 tekram
alias irda-dongle-1 esi
alias irda-dongle-2 actisys
alias irda-dongle-3 actisys
alias irda-dongle-4 girbil
alias irda-dongle-5 litelink
alias irda-dongle-6 airport
alias irda-dongle-7 old_belkin
alias plip0 plip
alias plip1 plip
alias tunl0 ipip
alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias slip0 slip
alias slip1 slip
alias tty-ldisc-1 slip
alias tty-ldisc-3 ppp_async
alias tty-ldisc-11 irtty-sir
alias tty-ldisc-14 ppp_synctty
alias tty-ldisc-15 hci_uart
alias ppp-compress-18 ppp_mppe
install ppp-compress-21 /bin/true
alias ppp-compress-24 ppp_deflate
alias ppp-compress-26 ppp_deflate
alias parport_lowlevel parport_pc
alias usbdevfs usbcore
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6
alias cipher_null crypto_null
alias digest_null crypto_null
alias compress_null crypto_null
alias sha384 sha512
install binfmt-0000 /bin/true
install nfsd /sbin/modprobe --first-time --ignore-install nfsd && { /bin/mount -t nfsd nfsd /proc/fs/nfsd > /dev/null 2>&1 || :; }
install sunrpc /sbin/modprobe --first-time --ignore-install sunrpc && { /bin/mount -t rpc_pipefs sunrpc /var/lib/nfs/rpc_pipefs > /dev/null 2>&1 || :; }
install char-major-10 /bin/true
install char-major-10-1 /bin/true
install dummy0 /sbin/modprobe -o dummy0 --ignore-install dummy
install dummy1 /sbin/modprobe -o dummy1 --ignore-install dummy
install net-pf-19 /bin/true
install net-pf-3 /bin/true
install net-pf-6 /bin/true
install ov518_decomp { /sbin/modprobe ov511; } ; /sbin/modprobe --first-time --ignore-install ov518_decomp
install scsi_hostadapter /bin/true
install usbmouse /sbin/modprobe --first-time --ignore-install usbmouse && { /sbin/modprobe hid; /bin/true; }
remove ov518_decomp /sbin/modprobe -r --first-time --ignore-remove ov518_decomp && { /sbin/modprobe -r ov511; /bin/true; }
remove usbmouse { /sbin/modprobe -r hid; } ; /sbin/modprobe -r --first-time --ignore-remove usbmouse
remove sunrpc { /bin/umount /var/lib/nfs/rpc_pipefs > /dev/null 2>&1 || :; } ; /sbin/modprobe -r --ignore-remove sunrpc
remove nfsd { /bin/umount /proc/fs/nfsd > /dev/null 2>&1 || :; } ; /sbin/modprobe -r --first-time --ignore-remove nfsd
alias usb-uhci uhci-hcd
alias usb-ohci ohci-hcd
alias uhci uhci-hcd
alias char-major-116-* snd
alias sound-service-*-0 snd-mixer-oss
alias sound-service-*-1 snd-seq-oss
alias sound-service-*-3 snd-pcm-oss
alias sound-service-*-8 snd-seq-oss
alias sound-service-*-12 snd-pcm-oss
install sound-slot-* /sbin/modprobe snd-card-${MODPROBE_MODULE##sound[_-]slot[_-]}
alias nfs4 nfs
alias rpc_pipefs sunrpc
alias rpc_svc_gss_pipefs sunrpc
install eth1394 /bin/true
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 && /sbin/modprobe snd-emu10k1-synth
alias gre0 ip_gre
alias char-major-89-* i2c-dev

[/etc/modprobe.d/openfwwf.conf]
options b43 nohwcrypt=1 qos=0

##### rc.local ##########################

touch /var/lock/subsys/local

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x0601 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   33.975540] avahi-daemon[887]: Network interface enumeration completed.
[   33.976790] NetworkManager[904]: <info> VPN: loaded org.freedesktop.NetworkManager.openvpn
[   34.531396] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.395174] wlan0: authenticate with <MAC 'XXXXXX' [AN3]> (try 1)
[   37.411680] wlan0: authenticated
[   37.423071] wlan0: associate with <MAC 'XXXXXX' [AN3]> (try 1)
[   37.427359] wlan0: RX AssocResp from <MAC 'XXXXXX' [AN3]> (capab=0x411 status=0 aid=4)
[   37.427364] wlan0: associated
[   37.432385] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.753351] wlan0: IPv6 duplicate address fe80::208:9fff:fef0:daa detected!
[78328.751115] wlan0: deauthenticating from <MAC 'XXXXXX' [AN3]> by local choice (reason=3)
[78329.859156] wlan0: authenticate with <MAC 'XXXXXX' [AN3]> (try 1)
[78329.876160] wlan0: authenticated
[78329.880655] wlan0: associate with <MAC 'XXXXXX' [AN3]> (try 1)
[78329.884361] wlan0: RX ReassocResp from <MAC 'XXXXXX' [AN3]> (capab=0x411 status=0 aid=3)
[78329.884371] wlan0: associated
[78330.628404] wlan0: IPv6 duplicate address fe80::208:9fff:fef0:daa detected!
[79757.579123] wlan0: deauthenticating from <MAC 'XXXXXX' [AN3]> by local choice (reason=3)
[79758.643782] wlan0: authenticate with <MAC 'XXXXXX' [AN3]> (try 1)
[79758.660301] wlan0: authenticated
[79758.660788] wlan0: associate with <MAC 'XXXXXX' [AN3]> (try 1)
[79758.664444] wlan0: RX ReassocResp from <MAC 'XXXXXX' [AN3]> (capab=0x411 status=0 aid=3)
[79758.664455] wlan0: associated
[79759.230350] wlan0: IPv6 duplicate address fe80::208:9fff:fef0:daa detected!

########## wireless info END ############

``` 

Thanks...

---

### Post by wildmanne39 on 2015-05-08
That is good information to see but it does not help much at the moment because your device is still disabled, please post what I asked in post 27, most of it I have asked for twice now.
I am not sure with those errors we can make it work, from my research it looks like other peoples where working but poorly.
Thanks

---

