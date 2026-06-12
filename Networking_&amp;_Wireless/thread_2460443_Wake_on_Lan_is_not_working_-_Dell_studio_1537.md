---
title: "Wake on Lan is not working - Dell studio 1537"
date: 2021-04-10
forum: Networking &amp; Wireless
---

### Post by epamein on 2021-04-10
hi!
yesterday, i installed "ubuntu-20.04.2-live-server-amd64" on an old laptop, Dell studio 1537. I want to activate Wake on Lan but probably i'm doing something wrong and it's not working.

when i run the following commands the server is not receiving wake up packets,
root@Hra:~# sudo wakeonlan 00:22:19:e2:25:3d
root@Hra:~# sudo etherwake 00:22:19:e2:25:3d

it can receive wake up packet when i add the server's ip
```
root@Hra:~# sudo wakeonlan -i 192.168.1.107 00:22:19:e2:25:3d

```

```
nwntas@dell:~$ sudo tcpdump -i enp6s0 '(udp and port 7) or (udp and port 9)'
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on enp6s0, link-type EN10MB (Ethernet), capture size 262144 bytes
08:41:58.414297 IP PC192.168.1.41.50219 > dell.discard: UDP, length 102

```

i shutdown the server using the following command,
nwntas@dell:~$ sudo systemctl poweroff

Wake on Lan works when the server is on suspend, but not when it's on shutdown.
 Is there any solution for this?

Also, on the same network i can use WoL on an HP laptop with Debian, without any problem.

```
nwntas@dell:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal

```

```
nwntas@dell:~$ lsmod
Module                  Size  Used by
dm_multipath           32768  0
scsi_dh_rdac           16384  0
scsi_dh_emc            16384  0
scsi_dh_alua           20480  0
snd_hda_codec_idt      61440  1
snd_hda_codec_hdmi     61440  1
snd_hda_codec_generic    81920  1 snd_hda_codec_idt
snd_hda_intel          53248  0
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         135168  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_idt
r852                   24576  0
coretemp               20480  0
sm_common              16384  1 r852
nand                  106496  2 r852,sm_common
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_idt
kvm_intel             282624  0
nand_ecc               16384  1 nand
bch                    24576  1 nand
dell_laptop            24576  0
snd_hwdep              20480  1 snd_hda_codec
ledtrig_audio          16384  2 snd_hda_codec_generic,dell_laptop
nandcore               16384  1 nand
kvm                   663552  1 kvm_intel
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
dell_wmi               20480  0
mtd                    65536  2 nand,sm_common
dell_smbios            28672  2 dell_wmi,dell_laptop
dell_smm_hwmon         20480  0
dcdbas                 20480  1 dell_smbios
wmi_bmof               16384  0
ir_rc6_decoder         20480  0
sparse_keymap          16384  1 dell_wmi
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
snd_timer              36864  1 snd_pcm
input_leds             16384  0
serio_raw              20480  0
r592                   20480  0
rc_rc6_mce             16384  0
memstick               20480  1 r592
ite_cir                28672  0
snd                    90112  8 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_hda_codec_idt
rc_core                53248  4 ite_cir,ir_rc6_decoder,rc_rc6_mce
mac_hid                16384  0
soundcore              16384  1 snd
sch_fq_codel           20480  2
ip_tables              32768  0
x_tables               45056  1 ip_tables
autofs4                45056  2
btrfs                1257472  0
zstd_compress         167936  1 btrfs
raid10                 57344  0
raid456               155648  0
async_raid6_recov      24576  1 raid456
async_memcpy           20480  2 raid456,async_raid6_recov
async_pq               24576  2 raid456,async_raid6_recov
async_xor              20480  3 async_pq,raid456,async_raid6_recov
async_tx               20480  5 async_pq,async_memcpy,async_xor,raid456,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              114688  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  2 btrfs,raid456
raid1                  45056  0
raid0                  24576  0
multipath              20480  0
linear                 20480  0
radeon               1474560  1
hid_generic            16384  0
i2c_algo_bit           16384  1 radeon
sdhci_pci              53248  0
usbhid                 57344  0
cqhci                  28672  1 sdhci_pci
ttm                   106496  1 radeon
firewire_ohci          40960  0
psmouse               155648  0
i2c_i801               32768  0
hid                   131072  2 usbhid,hid_generic
sdhci                  65536  1 sdhci_pci
ahci                   40960  2
firewire_core          65536  1 firewire_ohci
libahci                32768  1 ahci
crc_itu_t              16384  1 firewire_core
drm_kms_helper        184320  1 radeon
lpc_ich                24576  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
tg3                   172032  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   491520  4 drm_kms_helper,radeon,ttm
wmi                    32768  4 dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
video                  49152  2 dell_wmi,dell_laptop
```

```
nwntas@dell:~$ sudo nano /etc/netplan/00-installer-config.yaml

# This is the network config written by 'subiquity'
network:
  ethernets:
    enp6s0:
      dhcp4: true
  version: 2

```

```
nwntas@dell:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:22:19:e2:25:3d brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.107/24 brd 192.168.1.255 scope global dynamic enp6s0
       valid_lft 83289sec preferred_lft 83289sec
    inet6 2a02:587:6e0b:2e35:222:19ff:fee2:253d/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 604771sec preferred_lft 86371sec
    inet6 fe80::222:19ff:fee2:253d/64 scope link
       valid_lft forever preferred_lft forever
```

```
nwntas@dell:~$ sudo ethtool enp6s0
Settings for enp6s0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric
        Advertised auto-negotiation: Yes
        Advertised FEC modes: Not reported
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Link partner advertised FEC modes: Not reported
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
        Link detected: yes
```

```
nwntas@dell:~$ sudo nano /etc/systemd/system/wol.service

[Unit]
Description=Configure Wake On LAN

[Service]
Type=oneshot
ExecStart=/sbin/ethtool -s enp6s0 wol g

[Install]
WantedBy=basic.target

nwntas@dell:~$ sudo systemctl daemon-reload
nwntas@dell:~$ sudo systemctl enable wol.service
nwntas@dell:~$ sudo systemctl start wol.service
nwntas@dell:~$ systemctl status wol
&#9679; wol.service - Configure Wake On LAN
     Loaded: loaded (/etc/systemd/system/wol.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Sat 2021-04-10 07:08:31 UTC; 1h 18min ago
   Main PID: 688 (code=exited, status=0/SUCCESS)

Apr 10 07:08:31 dell systemd[1]: Starting Configure Wake On LAN...
Apr 10 07:08:31 dell systemd[1]: wol.service: Succeeded.
Apr 10 07:08:31 dell systemd[1]: Finished Configure Wake On LAN.

```

---

### Post by epamein on 2021-04-11
Any suggestion?

---

### Post by epamein on 2021-04-13
Wake on Lan on suspend mode is useless, especially when you have power outage. I just had a power black out and i had to turn the server on manually.
Is there any way to move this thread at the general discussion? Here it has 0 views  :D

---

### Post by jeremy31 on 2021-04-13
The view counter has not worked on new threads for years

---

### Post by him610 on 2021-04-18
I was under the impression that one had to enable wake-on-lan in the system bios/euve settings 

Here is an explanation of wake-on-lan, [https://en.wikipedia.org/wiki/Wake-on-LAN]("https://en.wikipedia.org/wiki/Wake-on-LAN")
A few paragraphs down the page, we can read, 
> A standard magic packet has the following basic limitations:

Requires destination computer MAC address (also may require a SecureOn password)
Does not provide a delivery confirmation
May not work outside of the local network
Requires hardware support of Wake-on-LAN on destination computer
Most 802.11 wireless interfaces do not maintain a link in low power states and cannot receive a magic packet

The magic packet is the wol packet.

It could be that your Dell 1537 may not have the wol capability.

---

### Post by Tadaen_Sylvermane on 2021-04-19
For a couple of my machines that I was doing WoL with they had 2 or 3 settings all in different places in the efi / bios that had to be changed. It wasn't just one and done. Annoyed me for awhile till I figured it out. The manual was less than helpful.

---

