---
title: "Network (Ethernet/Wired) issues after update (though works on Windows)"
date: 2021-12-28
forum: Networking &amp; Wireless
---

### Post by 1984dc on 2021-12-28
Hi,

After I updated a few months back my ethernet connection failed to connect ("Connection Failed" error), sometimes it seems connected in the network manager, but I can't connect to the internet at all. I managed to get it working again, but it flaked out again after another update and now the same solution (renaming the network and moving to managed networking) doesn't work :(

It might be something to do with my BIOS/a Firmware update (maybe?!) as I tried a live USB (of another similar distro) and had the same issue. Windows 10 works fine on Ethernet and wireless though. 

Goes without saying that I have already checked through the relevant posts on here/mr google (I think!) and nothing has worked as of yet after quite a bit of trying.

My wireless is also out!!!! So I can't connect on that to check stuff. That is just a driver issue though I think so should be easy to fix when I get my wired connection fixed.

Some details:

[B]Ubuntu version: 
[/B]20.4 

[B]/etc/NetworkManager/NetworkManager.conf :
[/B]```
[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=true


[device]
wifi.scan-rand-mac-address=no
```

**/etc/netplan/01-network-manager-all.yaml :**

```

network:
    Version: 2
    Renderer: NetworkManager


```

[B]Output of of sudo lshw -C network :

[/B]```
 *-network                 
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 05
       serial: e0:3f:49:1a:f0:f7
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.11.0-37-generic duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:31 memory:f7100000-f711ffff memory:f7139000-f7139fff ioport:f040(size=32)
  *-network
       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f7400000-f7407fff memory:f7200000-f73fffff

```


Many many thanks for any help with this one, I have been  ](*,) for quite a while now and not really sure which way to go here!

---

### Post by praseodym on 2021-12-28
Please show
```

cat /etc/network/interfaces
dmesg | grep e1
lsmod
```

---

### Post by 1984dc on 2021-12-29
Hi Praedom, 

Not sure how or why, but after running those commands my ethernet now seems to be working.... 

Going to run a few updates and see if this issue doesn't happen again now. 

Many thanks!

---

### Post by 1984dc on 2022-03-29
This has randomly started again. The details you asked for:

[code]

cat /etc/network/interfaces


# The loopback network interface
auto eno1
# The primary network interface
iface eno1 inet dhcp


dmesg | grep e1


[    0.165547] pci 0000:01:00.1: [10de:0e1a] type 00 class 0x040300
[    0.263506] thermal LNXTHERM:01: registered as thermal_zone1
[    0.493416] integrity: Loaded X.509 cert 'Microsoft Windows Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53'
[    0.673861] e1000e: Intel(R) PRO/1000 Network Driver
[    0.673863] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.674135] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.751176] e1000e 0000:00:19.0 0000:00:19.0 (uninitialized): registered PHC clock
[    0.818593] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) e0:3f:49:1a:f0:f7
[    0.818596] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.818634] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.819343] e1000e 0000:00:19.0 eno1: renamed from eth0
[   13.081600] e1000e 0000:00:19.0 eno1: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   30.801631] audit: type=1326 audit(1648575678.819:109): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=2796 comm="snap-store" exe="/snap/snap-store/558/usr/bin/snap-store" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7fe13303576d code=0x50000
[   50.010121] audit: type=1326 audit(1648575698.901:141): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=2796 comm="pool-org.gnome." exe="/snap/snap-store/558/usr/bin/snap-store" sig=0 arch=c000003e syscall=93 compat=0 ip=0x7fe13302c3cb code=0x50000




lsmod


Module                  Size  Used by
rfcomm                 81920  4
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               516096  2 vboxnetadp,vboxnetflt
cmac                   16384  4
algif_hash             16384  2
algif_skcipher         16384  2
af_alg                 28672  10 algif_hash,algif_skcipher
bnep                   24576  2
nls_iso8859_1          16384  1
nvidia_uvm           1036288  0
nvidia_drm             61440  8
nvidia_modeset       1200128  11 nvidia_drm
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
nvidia              35319808  482 nvidia_uvm,nvidia_modeset
coretemp               20480  0
snd_hda_codec_realtek   147456  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  1
snd_hda_intel          53248  6
snd_intel_dspcfg       28672  1 snd_hda_intel
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
snd_hda_codec         147456  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
kvm_intel             303104  0
snd_pcm               114688  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
btusb                  61440  0
kvm                   864256  1 kvm_intel
btrtl                  24576  1 btusb
crct10dif_pclmul       16384  1
btbcm                  20480  1 btusb
ghash_clmulni_intel    16384  0
btintel                32768  1 btusb
snd_seq_midi           20480  0
mei_hdcp               24576  0
snd_seq_midi_event     16384  1 snd_seq_midi
bluetooth             651264  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
aesni_intel           376832  6
snd_rawmidi            36864  1 snd_seq_midi
wl                   6455296  0
ecdh_generic           16384  1 bluetooth
ecc                    36864  1 ecdh_generic
input_leds             16384  0
joydev                 28672  0
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
crypto_simd            16384  1 aesni_intel
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel
drm_kms_helper        253952  1 nvidia_drm
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
rapl                   20480  0
intel_cstate           20480  0
eeepc_wmi              16384  0
wmi_bmof               16384  0
mxm_wmi                16384  0
snd_timer              40960  2 snd_seq,snd_pcm
efi_pstore             16384  0
at24                   24576  0
cec                    53248  1 drm_kms_helper
cfg80211              888832  1 wl
snd                    94208  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  1
rc_core                61440  1 cec
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
mei                   131072  3 mei_hdcp,mei_me
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  3
ipmi_devintf           20480  0
ipmi_msghandler       114688  1 ipmi_devintf
msr                    16384  0
parport_pc             45056  0
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
drm                   557056  12 drm_kms_helper,nvidia,nvidia_drm
ip_tables              32768  0
x_tables               49152  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   139264  2 usbhid,hid_generic
mfd_aaeon              16384  0
asus_wmi               36864  2 eeepc_wmi,mfd_aaeon
sparse_keymap          16384  1 asus_wmi
crc32_pclmul           16384  0
i2c_i801               36864  0
firewire_ohci          45056  0
i2c_smbus              20480  1 i2c_i801
firewire_core          65536  1 firewire_ohci
ahci                   40960  6
lpc_ich                24576  0
libahci                36864  1 ahci
crc_itu_t              16384  1 firewire_core
e1000e                266240  0
xhci_pci               24576  0
xhci_pci_renesas       20480  1 xhci_pci
video                  53248  1 asus_wmi
wmi                    32768  4 asus_wmi,wmi_bmof,mfd_aaeon,mxm_wmi

[/code ]

Any help would be hugely appreciated!!!!

---

### Post by praseodym on 2022-03-29
/etc/network/Interfaces must Look like this only

auto lo
iface lo inet loopback

Reboot after changing

---

### Post by 1984dc on 2022-03-31
That has worked! Thanks :)

---

