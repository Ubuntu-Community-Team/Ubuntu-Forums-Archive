---
title: "My ubuntu 20.04 can not find wifi adapter !!!"
date: 2021-01-02
forum: Networking &amp; Wireless
---

### Post by fairbird on 2021-01-02
As in the tittle ... I try to use my wifi adapter on my ubuntu 20.04 but can not be find ... I have tried some solutions from here and by used google but nothing help me..
Also I have source driver (RTL8188EUS_linux_v4.1.4_6773.20130222) inside cd and tried also but can not compile it was old

```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.4.0-58-generic/build M=/home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222 modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-58-generic'
CC [M] /home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_cmd.o
In file included from /home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_cmd.c:23:
/home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_service.h: In function ‘_init_timer’:
/home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_service.h:956:8: error: ‘_timer’ {aka ‘struct timer_list’} has no member named ‘data’
956 | ptimer->data = (unsigned long)cntx;
| ^~
/home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_service.h:957:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
957 | init_timer(ptimer);
| ^~~~~~~~~~
| _init_timer
In file included from /home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_cmd.c:23:
/home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_service.h: In function ‘thread_enter’:
/home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_service.h:1423:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
1423 | daemonize("%s", name);
| ^~~~~~~~~
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:275: /home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_cmd.o] Error 1
make[1]: *** [Makefile:1757: /home/raed/Desktop/rtl8188EUS_linux_v4.1.4_6773.20130222] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-58-generic'
make: *** [Makefile:678: modules] Error 2
```


Also I tried to download and compile it from source but same thing can not be find it on ubuntu
 [https://github.com/aircrack-ng/rtl8188eus.git](https://github.com/aircrack-ng/rtl8188eus.git)


```
~$ sudo lshw -c network
*-network 
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: enp2s0
version: 15
serial: f4:8e:38:7f:70:ad
size: 1Gbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.42.0.1 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
resources: irq:16 ioport:e000(size=256) memory:f7004000-f7004fff memory:f7000000-f7003fff
*-network
description: Ethernet interface
physical id: 1
logical name: docker0
serial: 02:42:be:a5:3b:1b
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes


~$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 413c:2113 Dell Computer Corp. Dell KB216 Wired Keyboard
Bus 001 Device 006: ID 413c:301a Dell Computer Corp. Dell MS116 USB Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
00:14.0 USB controller: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation H110 Chipset LPC/eSPI Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller (rev 31)
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)

~$ sudo lsmod
Module Size Used by
ccm 20480 0
rt73usb 36864 0
rt2x00usb 24576 1 rt73usb
rt2x00lib 61440 2 rt73usb,rt2x00usb
mac80211 843776 2 rt2x00lib,rt2x00usb
crc_itu_t 16384 1 rt73usb
libarc4 16384 1 mac80211
rfcomm 81920 4
nf_conntrack_netlink 45056 0
nfnetlink 16384 2 nf_conntrack_netlink
xfrm_user 36864 1
xfrm_algo 16384 1 xfrm_user
xt_addrtype 16384 2
xt_MASQUERADE 20480 2
xt_state 16384 0
xt_conntrack 16384 2
ipt_REJECT 16384 2
nf_reject_ipv4 16384 1 ipt_REJECT
xt_tcpudp 20480 4
bpfilter 32768 0
nf_nat_h323 24576 0
nf_conntrack_h323 81920 1 nf_nat_h323
nf_nat_pptp 20480 0
nf_conntrack_pptp 24576 1 nf_nat_pptp
nf_nat_tftp 16384 0
nf_conntrack_tftp 20480 1 nf_nat_tftp
nf_nat_sip 20480 0
nf_conntrack_sip 36864 1 nf_nat_sip
nf_nat_irc 20480 0
nf_conntrack_irc 20480 1 nf_nat_irc
nf_nat_ftp 20480 0
nf_conntrack_ftp 24576 1 nf_nat_ftp
iptable_nat 16384 1
nf_nat 40960 8 nf_nat_irc,nf_nat_ftp,nf_nat_tftp,nf_nat_pptp,nf_nat_h323,iptable_nat,xt_MASQUERADE,nf_nat_sip
nf_conntrack 139264 17 xt_conntrack,nf_nat_irc,nf_nat,nf_conntrack_tftp,nf_nat_ftp,xt_state,nf_conntrack_pptp,nf_nat_tftp,nf_conntrack_sip,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_irc,nf_conntrack_netlink,nf_conntrack_ftp,nf_nat_h323,xt_MASQUERADE,nf_nat_sip
nf_defrag_ipv6 24576 1 nf_conntrack
nf_defrag_ipv4 16384 1 nf_conntrack
libcrc32c 16384 2 nf_conntrack,nf_nat
aufs 262144 0
cfg80211 704512 2 rt2x00lib,mac80211
cmac 16384 3
algif_hash 16384 1
algif_skcipher 16384 1
af_alg 24576 6 algif_hash,algif_skcipher
bnep 24576 2
binfmt_misc 24576 1
btusb 57344 0
btrtl 24576 1 btusb
btbcm 16384 1 btusb
btintel 24576 1 btusb
intel_rapl_msr 20480 0
bluetooth 548864 31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
intel_rapl_common 24576 1 intel_rapl_msr
ecdh_generic 16384 2 bluetooth
joydev 24576 0
ecc 28672 1 ecdh_generic
input_leds 16384 0
8188eu 729088 0
x86_pkg_temp_thermal 20480 0
intel_powerclamp 20480 0
coretemp 20480 0
snd_hda_codec_hdmi 61440 1
kvm_intel 282624 0
snd_hda_codec_realtek 126976 1
snd_hda_codec_generic 81920 1 snd_hda_codec_realtek
kvm 663552 1 kvm_intel
ledtrig_audio 16384 2 snd_hda_codec_generic,snd_hda_codec_realtek
mei_hdcp 24576 0
crct10dif_pclmul 16384 1
ghash_clmulni_intel 16384 0
snd_hda_intel 53248 2
snd_intel_dspcfg 24576 1 snd_hda_intel
aesni_intel 372736 4
snd_hda_codec 135168 4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
crypto_simd 16384 1 aesni_intel
cryptd 24576 3 crypto_simd,ghash_clmulni_intel
glue_helper 16384 1 aesni_intel
snd_hda_core 90112 5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
i915 1986560 18
rapl 20480 0
snd_hwdep 20480 1 snd_hda_codec
intel_cstate 20480 0
snd_pcm 106496 4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi 20480 0
snd_seq_midi_event 16384 1 snd_seq_midi
drm_kms_helper 184320 1 i915
snd_rawmidi 36864 1 snd_seq_midi
serio_raw 20480 0
i2c_algo_bit 16384 1 i915
snd_seq 69632 2 snd_seq_midi,snd_seq_midi_event
dell_wmi 20480 0
snd_seq_device 16384 3 snd_seq,snd_seq_midi,snd_rawmidi
fb_sys_fops 16384 1 drm_kms_helper
sparse_keymap 16384 1 dell_wmi
syscopyarea 16384 1 drm_kms_helper
sysfillrect 16384 1 drm_kms_helper
sysimgblt 16384 1 drm_kms_helper
snd_timer 36864 2 snd_seq,snd_pcm
acpi_pad 184320 0
snd 90112 15 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me 40960 1
soundcore 16384 1 snd
mei 106496 3 mei_hdcp,mei_me
intel_pch_thermal 16384 0
dell_smbios 28672 1 dell_wmi
dcdbas 20480 1 dell_smbios
wmi_bmof 16384 0
dell_wmi_descriptor 20480 2 dell_wmi,dell_smbios
mac_hid 16384 0
sch_fq_codel 20480 2
overlay 114688 0
iptable_filter 16384 1
ip6table_filter 16384 0
ip6_tables 32768 1 ip6table_filter
nfsd 405504 13
br_netfilter 28672 0
bridge 176128 1 br_netfilter
stp 16384 1 bridge
auth_rpcgss 94208 1 nfsd
llc 16384 2 bridge,stp
nfs_acl 16384 1 nfsd
lockd 102400 1 nfsd
arp_tables 24576 0
grace 16384 2 nfsd,lockd
sunrpc 393216 18 nfsd,a
```

---

### Post by morrownr on 2021-01-02
I'm a little confused. You said "wifi adapter" which tells me you have a USB WiFi adapter. When we look at "lsusb" I don't see anything that looks like a USB WiFi adapter. I do see a Realtek based ethernet controller in the "lspci" info but that isn't for wifi. Was your USB WiFi adapter plugged into the system when you ran "lsusb?"

I do see what appears to be Ralink USB WiFi drivers under the list of modules. Could you run "lsusb" with the adapter plugged into the system and post the results? ...and maybe give us a url to the product?

For what it is worth, the chances of 7 year old source code compiling correctly and working are about zero when it comes to networking equipment. Recommend you check your kernel version and then check what kernel is supported by the driver before expending any effort.

---

### Post by fairbird on 2021-01-02
Thank you for answer ...
It is ok now I solve it ...

Change usb input to other one and recompile driver again .. 
And now the usb wifi works just fine

---

### Post by morrownr on 2021-01-02
For what it is worth, here is an active site working driver for that chipset: [https://github.com/aircrack-ng/rtl8188eus](https://github.com/aircrack-ng/rtl8188eus)

I was reading the most recent issue on that site and it appears that adapter is supported in-kernel meaning you should not have to compile a driver. It seems that the system was not seeing the adapter so it was not supporting it.

---

### Post by fairbird on 2021-01-03
No ... it is not rtl8188eus driver I was wrong ...
The correct driver is rtl8188fu
>   *-network:0       description: Wireless interface
       physical id: 1
       bus info: usb@1:10
       logical name: wlx00e020300378
       serial: 00:e0:20:30:03:78
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188fu ip=192.168.100.42 multicast=yes wireless=IEEE 802.11bgn




---

