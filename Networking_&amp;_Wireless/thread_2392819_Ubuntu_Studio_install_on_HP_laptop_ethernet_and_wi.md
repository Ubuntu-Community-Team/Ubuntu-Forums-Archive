---
title: "Ubuntu Studio install on HP laptop ethernet and wifi not working"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by dilbert3818 on 2018-05-25
I did a fresh install of Ubuntu Studio 16.04 on a HP laptop. 

Ethernet and Wifi are not working, or at least not working correctly.

It appears that I get connected to my router and I can ping the router, but I am unable get to the internet using a browser and ping google.com does not work.

[https://pastebin.ubuntu.com/p/npKvR8s74j/](https://pastebin.ubuntu.com/p/npKvR8s74j/)

I've run the wireless info script and have attached the results. I also did the pastebin, but I don't think the full results of the script are shown. [ATTACH]279854[/ATTACH]

I have been looking around the forums, but I have been unable to get either wifi or ethernet to work correctly. I would prefer to be able to connect with both ethernet or wifi.

I did do something like: [COLOR=#111111][FONT=Consolas]echo "options rtl8723be ant_sel=2"  | sudo tee /etc/modprobe.d/rtl8723be.conf [/FONT][/COLOR][FONT=Consolas]to get the wifi signal to work and the strength to be better.[/FONT][COLOR=#111111][FONT=Consolas]

[/FONT][/COLOR]Any help would be appreciated. Thanks.[COLOR=#111111][FONT=Consolas]

[/FONT][/COLOR]

---

### Post by praseodym on 2018-05-26
Which country do you live? US? If yes:
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
Reboot. Also try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by dilbert3818 on 2018-05-26
> **praseodym said:**
> Which country do you live? US? If yes:
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
Reboot. Also try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

thank you for the response. I’ve tried both of those and internet still is not working (WiFi and Ethernet).

---

### Post by Autodave on 2018-05-26
This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by praseodym on 2018-05-26
Please show 
```

lsmod
ifconfig -a
dmesg | egrep 'key|r8|rtl'
```

---

### Post by dilbert3818 on 2018-05-26
lsmod
```

Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
rfcomm                 77824  12
ccm                    20480  6
bnep                   20480  2
nls_iso8859_1          16384  2
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
edac_mce_amd           28672  0
kvm                   589824  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
arc4                   16384  2
aesni_intel           188416  4
aes_x86_64             20480  1 aesni_intel
rtl8723be             102400  0
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
btcoexist             131072  1 rtl8723be
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
joydev                 20480  0
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
input_leds             16384  0
hp_wmi                 16384  0
serio_raw              16384  0
sparse_keymap          16384  1 hp_wmi
mac80211              794624  3 rtl_pci,rtlwifi,rtl8723be
wmi_bmof               16384  0
snd_hda_codec_realtek    94208  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
fam15h_power           16384  0
snd_seq_midi           16384  0
snd_hda_codec_hdmi     49152  1
snd_seq_midi_event     16384  1 snd_seq_midi
k10temp                16384  0
snd_hda_intel          40960  5
i2c_piix4              24576  0
snd_rawmidi            32768  1 snd_seq_midi
btusb                  45056  0
btrtl                  16384  1 btusb
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  39 btrtl,btintel,bnep,btbcm,rfcomm,btusb
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
ecdh_generic           24576  1 bluetooth
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
cfg80211              626688  2 mac80211,rtlwifi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
rtsx_pci_ms            20480  0
memstick               16384  1 rtsx_pci_ms
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
shpchp                 36864  0
soundcore              16384  1 snd
i2c_scmi               16384  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
hp_wireless            16384  0
tpm_crb                16384  0
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
rtsx_pci_sdmmc         24576  0
amdgpu               2031616  4
i2c_algo_bit           16384  1 amdgpu
psmouse               147456  0
ttm                    94208  1 amdgpu
ahci                   36864  3
libahci                32768  1 ahci
drm_kms_helper        167936  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  6 amdgpu,ttm,drm_kms_helper
r8169                  86016  0
wmi                    24576  2 wmi_bmof,hp_wmi
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
video                  40960  0

```

ifconfig
```
eno1      Link encap:Ethernet  HWaddr 3c:a8:2a:b9:0f:0c            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126004 (126.0 KB)  TX bytes:126004 (126.0 KB)


wlo1      Link encap:Ethernet  HWaddr 70:77:81:99:a4:df  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76b2:817d:3e9b:e33e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16959 (16.9 KB)  TX bytes:7622 (7.6 KB)

```

dmesg
```
[    0.000000] percpu: Embedded 45 pages/cpu @ffff885e7ec00000 s146904 r8192 d29224 u524288[    0.000000] pcpu-alloc: s146904 r8192 d29224 u524288 alloc=1*2097152
[    1.767563] Initialise system trusted keyrings
[    1.773869] Asymmetric key parser 'x509' registered
[    1.882961] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.891391] Loaded X.509 cert 'Build time autogenerated kernel key: c866646d02c3195d0819f588e7dd1aee8a7345f1'
[    1.891623] Loaded UEFI:db cert 'Hewlett-Packard Company: HP UEFI Secure Boot 2013 DB key: 1d7cf2c2b92673f69c8ee1ec7063967ab9b62bec' linked to secondary sys keyring
[    1.891645] Loaded UEFI:db cert 'Microsoft Windows Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53' linked to secondary sys keyring
[    1.891666] Loaded UEFI:db cert 'Microsoft Corporation UEFI CA 2011: 13adbf4309bd82709c8cd54f316ed522988a1bd4' linked to secondary sys keyring
[    1.895711] Loaded UEFI:MokListRT cert 'Canonical Ltd. Master Certificate Authority: ad91990bc22ab1f517048c23b6655a268e345a63' linked to secondary sys keyring
[    1.902683] Key type big_key registered
[    2.146320] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.146350] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.146363] r8169 0000:02:00.0: enabling device (0000 -> 0003)
[    2.147194] r8169 0000:02:00.0 eth0: RTL8106e at 0xffff99dd40ccd000, 3c:a8:2a:b9:0f:0c, XID 04900000 IRQ 39
[    2.208871] r8169 0000:02:00.0 eno1: renamed from eth0
[   19.817679] input: HP Wireless hotkeys as /devices/virtual/input/input8
[   19.972594] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   19.972596] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   20.003699] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   20.003718] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   20.026817] input: HP WMI hotkeys as /devices/virtual/input/input13
[   20.052654] rtl8723be 0000:03:00.0: enabling device (0000 -> 0003)
[   20.067449] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[   20.080474] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.080800] rtlwifi: rtlwifi: wireless switch is on
[   20.338378] rtl8723be 0000:03:00.0 wlo1: renamed from wlan0
[   27.653635] r8169 0000:02:00.0 eno1: link down

```

---

### Post by praseodym on 2018-05-26
Cable seems to be unplugged. Lets see if this makes wifi better
```

sudo iwconfig wlo1 power off
```
Change the channel to the fixed No. 6 in your router, bandwidth restricting to 20 MHz instead of 20/40 MHz there, too. No hidden networks, this is not a security feature

---

### Post by dilbert3818 on 2018-05-26
> **praseodym said:**
> Cable seems to be unplugged. Lets see if this makes wifi better
```

sudo iwconfig wlo1 power off
```
Change the channel to the fixed No. 6 in your router, bandwidth restricting to 20 MHz instead of 20/40 MHz there, too. No hidden networks, this is not a security feature

Sorry I was not connected to Ethernet to run the commands. I can be if you need me to.

it shows I am connected to WiFi, I just can&#8217;t get to the internet.

also I am setting this up for my dad, I&#8217;d rather not change my network settings. I just figured I would be able to connect to WiFi or Ethernet without a problem

---

### Post by praseodym on 2018-05-27
Changing the network setting doesn't affect other devices.

---

### Post by dilbert3818 on 2018-05-27
How about the wired connection? I should not have to change WiFi settings on the router to make that work. Should I run those commands wired?

---

### Post by praseodym on 2018-05-27
Please show with cable plugged
```

sudo modprobe -rfv r8169
sudo modprobe -v r8169
ip a
ifconfig -a
dmesg | grep r8
cat /etc/resolv.conf
route -n
```

---

### Post by dilbert3818 on 2018-05-27
Thanks so much for your help. 

sudo modprobe -rfv r8169
```
rmmod r8169
rmmod mii

```


sudo modprobe -v r8169
```
insmod /lib/modules/4.13.0-36-lowlatency/kernel/drivers/net/mii.ko 
insmod /lib/modules/4.13.0-36-lowlatency/kernel/drivers/net/ethernet/realtek/r8169.ko 

```


ip a
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 70:77:81:99:a4:df brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.13/24 brd 192.168.1.255 scope global dynamic wlo1
       valid_lft 86128sec preferred_lft 86128sec
    inet6 fe80::76b2:817d:3e9b:e33e/64 scope link 
       valid_lft forever preferred_lft forever
4: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 3c:a8:2a:b9:0f:0c brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.149/24 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 86384sec preferred_lft 86384sec
    inet6 fe80::b9d:b01c:8bcb:1f87/64 scope link 
       valid_lft forever preferred_lft forever



```


ifconfig -a
```
eno1      Link encap:Ethernet  HWaddr 3c:a8:2a:b9:0f:0c  
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b9d:b01c:8bcb:1f87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1593 (1.5 KB)  TX bytes:5908 (5.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:181608 (181.6 KB)  TX bytes:181608 (181.6 KB)


wlo1      Link encap:Ethernet  HWaddr 70:77:81:99:a4:df  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76b2:817d:3e9b:e33e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25126 (25.1 KB)  TX bytes:7674 (7.6 KB)



```


dmesg | grep r8
```
[    0.000000] percpu: Embedded 45 pages/cpu @ffff8c3afec00000 s146904 r8192 d29224 u524288
[    0.000000] pcpu-alloc: s146904 r8192 d29224 u524288 alloc=1*2097152
[    2.150240] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.150262] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.150271] r8169 0000:02:00.0: enabling device (0000 -> 0003)
[    2.151189] r8169 0000:02:00.0 eth0: RTL8106e at 0xffff9b7f00cd5000, 3c:a8:2a:b9:0f:0c, XID 04900000 IRQ 47
[    2.194840] r8169 0000:02:00.0 eno1: renamed from eth0
[   26.591675] r8169 0000:02:00.0 eno1: link down
[   26.591803] r8169 0000:02:00.0 eno1: link down
[   28.246268] r8169 0000:02:00.0 eno1: link up
[  351.393108] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[  351.393135] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[  351.396133] r8169 0000:02:00.0 eth0: RTL8106e at 0xffff9b7f00c8f000, 3c:a8:2a:b9:0f:0c, XID 04900000 IRQ 47
[  351.401741] r8169 0000:02:00.0 eno1: renamed from eth0
[  351.604431] r8169 0000:02:00.0 eno1: link down
[  351.604537] r8169 0000:02:00.0 eno1: link down
[  353.228493] r8169 0000:02:00.0 eno1: link up



```


cat /etc/resolv.conf
```
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 127.0.0.53

```


route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

```

---

### Post by praseodym on 2018-05-27
Doesn't look bad. Lets see

```
sudo apt-get install ethtool
sudo ethtool eno1
```

---

### Post by dilbert3818 on 2018-05-30
sudo apt-get install ethtool
```
Reading package lists...
Building dependency tree...
Reading state information...
ethtool is already the newest version (1:4.5-1).
The following packages were automatically installed and are no longer required:
  gir1.2-networkmanager-1.0 gir1.2-nma-1.0
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 154 not upgraded.



```


sudo ethtool eno1
```
Settings for eno1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes



```

---

### Post by praseodym on 2018-05-31
Check
```

sudo ethtool -S eno1 duplex full autoneg off
```

---

### Post by dilbert3818 on 2018-06-01
sudo ethtool -S eno1 duplex full autoneg off
```

$ sudo ethtool -S eno1 duplex full autoneg off
ethtool: bad command line argument(s)
For more information run ethtool -h



```

---

### Post by praseodym on 2018-06-01
```
sudo ethtool -s eno1 duplex full autoneg off
```
Try the small s

---

### Post by dilbert3818 on 2018-06-01
Ok. That command ran. There was not any output.

---

### Post by dilbert3818 on 2018-06-02
So I tried pinging. It appears I can ping outside ip addresses, but not by domain name. I am able to ping google.com and kernel.org from another laptop on my network.

```
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.64 bytes from 4.2.2.2: icmp_seq=1 ttl=55 time=23.0 ms
64 bytes from 4.2.2.2: icmp_seq=2 ttl=55 time=25.5 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=55 time=24.4 ms
64 bytes from 4.2.2.2: icmp_seq=4 ttl=55 time=23.4 ms
64 bytes from 4.2.2.2: icmp_seq=5 ttl=55 time=24.9 ms


--- 4.2.2.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 23.053/24.300/25.565/0.937 ms



```

ping google.com
```
ping: unknown host google.com
```

i tried to ping kernel.org and got the same response

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=25.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=23.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=23.5 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=23.0 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=57 time=23.3 ms


--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 23.073/23.719/25.410/0.863 ms



```

---

