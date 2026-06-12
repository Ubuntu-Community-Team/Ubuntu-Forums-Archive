---
title: "No internet but it's connected to wifi -  using Alfa AWUS036H + ubuntu 14.04"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by oragano on 2014-06-04
hi,

I'm new to ubuntu.  After some reading and trying to fix wifi unsuccessfully. Your help would greatly appreciated.

I could access internet upon first opening browser and then it couldn't access anymore while it's still connected to wifi.  Wireless security is set at "wpa2-aes".  I have dual boot with windows xp and it has **_no_** problem with accessing internet.

iwconfig
```

wlan0     IEEE 802.11bg  ESSID:"TELUS0340"  
             Mode:Managed  Frequency:2.437 GHz  Access Point: 18:9F:A9:5D:D2:88   
             Bit Rate=54 Mb/s   Tx-Power=27 dBm   
             Retry  long limit:7   RTS thr:off   Fragment thr:off
             Power Management:off
             Link Quality=58/70  Signal level=-52 dBm  
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:107  Invalid misc:227   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.

```

lsusb
```

Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:000e A4 Tech Co., Ltd X-F710F Optical Mouse 3xFire Gaming Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 01:1e:8c:86:68:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:163991 (163.9 KB)  TX bytes:163991 (163.9 KB)


wlan0     Link encap:Ethernet  HWaddr 01:c0:ca:31:04:86  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe31:486/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:385391 (385.3 KB)  TX bytes:156803 (156.8 KB)

```

nm-tool
```

NetworkManager Tool


State: connected (global)


- Device: wlan0  [TELUS0340] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        01:C0:CA:31:04:86


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    YELLOW:          Infra, C8:D3:A3:69:0A:35, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Leollan:         Infra, 20:76:00:79:1E:E4, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    TO:              Infra, 00:1E:58:FD:A3:69, Freq 2432 MHz, Rate 54 Mb/s, Strength 85 WEP
    TELUS1883:       Infra, C8:B3:73:60:E9:AD, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    *TELUS0340:      Infra, 18:9F:A9:5D:D2:88, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    DIRECT-QH[TV]HVCSAMSUNG: Infra, 9A:0C:82:FC:EA:B9, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2
    sudesh2011:      Infra, 20:76:00:C9:27:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    dlink:           Infra, 0C:50:76:80:9E:26, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WEP


  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254
    DNS:             75.153.176.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        01:1E:8C:86:68:AB


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

sudo lshw -C network
```

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 01:1e:8c:86:68:ab
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:ee00(size=256) memory:fdcff000-fdcfffff memory:fdd00000-fdd1ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 01:c0:ca:31:04:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.67 link=yes multicast=yes wireless=IEEE 802.11bg
oragano@oragano-System-Product-Name:~$ lsmod
Module                  Size  Used by
ctr                    12905  2 
ccm                    17496  2 
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
dm_crypt               22622  0 
arc4                   12536  2 
rtl8187                60157  0 
mac80211              545990  1 rtl8187
snd_hda_codec_realtek    51029  1 
cfg80211              409394  2 mac80211,rtl8187
snd_hda_intel          42730  3 
eeprom_93cx6           13168  1 rtl8187
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm_amd                50537  0 
snd_timer              28584  2 snd_pcm,snd_seq
kvm                   388083  1 kvm_amd
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
k8temp                 12842  0 
sp5100_tco             13643  0 
soundcore              12600  1 snd
i2c_piix4              17723  0 
asus_atk0110           18201  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
mac_hid                13037  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  2 hid_generic,usbhid
nouveau               969577  3 
mxm_wmi                12893  1 nouveau
wmi                    18673  2 mxm_wmi,nouveau
video                  18903  1 nouveau
i2c_algo_bit           13197  1 nouveau
r8169                  61562  0 
ttm                    72698  1 nouveau
pata_atiixp            13058  0 
drm_kms_helper         46907  1 nouveau
drm                   243792  5 ttm,drm_kms_helper,nouveau
mii                    13654  1 r8169
floppy                 55378  0 
ahci                   25579  2 
libahci                26754  1 ahci
ati_agp                13177  0 

```

---

### Post by oragano on 2014-06-04
ping -c 4 196.168.1.254
```

PING 196.168.1.254 (196.168.1.254) 56(84) bytes of data.


--- 196.168.1.254 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

```


ping -c 4 8.8.8.8
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.


--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

```

---

### Post by oragano on 2014-06-11
Anyone please...

---

### Post by BearChang on 2015-04-24
Hi,I also encountered the same problem.Did you solve it?:KS

---

