---
title: "iwlwifi weak signal for Intel AC 9462"
date: 2020-11-27
forum: Networking &amp; Wireless
---

### Post by *g!t5^_)*(H on 2020-11-27
I have problems with the integrated Wifi card, on a '[chuwi herobox]("https://www.chuwi.com/product/items/Chuwi-HeroBox.html")'

Wireless signal may be 90% on windows and 30% on Linux using the same machine and location.
It is unusable because of the disconnections and the speed.

I don't know how to solve it, tried every tutorial about similar problems without success.

Here is some information, in case someone can help me.

*(I am using on USB Wifi module to connect, due the problems with the integrated AC 9462 card. Ignore that USB Wifi NIC from the information)*

**Kernel version (from /proc/version):**

Linux version 5.8.0-29-generic (buildd@lgw01-amd64-055) (gcc (Ubuntu 10.2.0-13ubuntu1) 10.2.0, GNU ld (GNU Binutils for Ubuntu) 2.35.1) #31-Ubuntu SMP Fri Nov 6 12:37:59 UTC 2020

**This is the network interface I am having problems with:**

  *-network                
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlo2
       version: 03
       serial: zz:zz:zz:zz:zz:zz
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-29-generic firmware=46.8902351f.0 9000-pu-b0-jf-b0- latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:44 memory:a1214000-a1217fff

And some information about the system:

```

// ...............................................................
dmesg | grep iwl
[    4.384796] iwlwifi 0000:00:0c.0: enabling device (0000 -> 0002)
[    4.427242] iwlwifi 0000:00:0c.0: WRT: Overriding region id 0
[    4.427246] iwlwifi 0000:00:0c.0: WRT: Overriding region id 1
[    4.427248] iwlwifi 0000:00:0c.0: WRT: Overriding region id 2
[    4.427249] iwlwifi 0000:00:0c.0: WRT: Overriding region id 3
[    4.427250] iwlwifi 0000:00:0c.0: WRT: Overriding region id 4
[    4.427252] iwlwifi 0000:00:0c.0: WRT: Overriding region id 6
[    4.427253] iwlwifi 0000:00:0c.0: WRT: Overriding region id 8
[    4.427255] iwlwifi 0000:00:0c.0: WRT: Overriding region id 9
[    4.427256] iwlwifi 0000:00:0c.0: WRT: Overriding region id 10
[    4.427258] iwlwifi 0000:00:0c.0: WRT: Overriding region id 11
[    4.427259] iwlwifi 0000:00:0c.0: WRT: Overriding region id 15
[    4.427260] iwlwifi 0000:00:0c.0: WRT: Overriding region id 16
[    4.427262] iwlwifi 0000:00:0c.0: WRT: Overriding region id 18
[    4.427263] iwlwifi 0000:00:0c.0: WRT: Overriding region id 19
[    4.427264] iwlwifi 0000:00:0c.0: WRT: Overriding region id 20
[    4.427266] iwlwifi 0000:00:0c.0: WRT: Overriding region id 21
[    4.427271] iwlwifi 0000:00:0c.0: Found debug destination: EXTERNAL_DRAM
[    4.427272] iwlwifi 0000:00:0c.0: Found debug configuration: 0
[    4.427963] iwlwifi 0000:00:0c.0: loaded firmware version 46.8902351f.0 9000-pu-b0-jf-b0-46.ucode op_mode iwlmvm
[    4.428017] iwlwifi 0000:00:0c.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[    4.468457] iwlwifi 0000:00:0c.0: Detected Intel(R) Wireless-AC 9462, REV=0x318
[    4.520267] iwlwifi 0000:00:0c.0: base HW address: ??:??:??:??:??:??
[    4.563865] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.908016] iwlwifi 0000:00:0c.0 wlo2: renamed from wlan0
[    6.753774] iwlwifi 0000:00:0c.0: Conflict between TLV & NVM regarding enabling LAR (TLV = enabled NVM =disabled)
[ 2358.401391] iwlwifi 0000:00:0c.0: No beacon heard and the time event is over already...

// ...............................................................
cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 122
model name : Intel(R) Celeron(R) N4100 CPU @ 1.10GHz
stepping : 1
microcode : 0x32
cpu MHz : 1160.376
cache size : 4096 KB
physical id : 0
siblings : 4
core id : 0
cpu cores : 4
apicid : 0
initial apicid : 0
fpu : yes
fpu_exception : yes
cpuid level : 24
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave rdrand lahf_lm 3dnowprefetch cpuid_fault cat_l2 pti cdp_l2 ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust smep erms mpx rdt_a rdseed smap clflushopt intel_pt sha_ni xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts umip rdpid md_clear arch_capabilities
vmx flags : vnmi preemption_timer posted_intr invvpid ept_x_only ept_ad ept_1gb flexpriority apicv tsc_offset vtpr mtf vapic ept vpid unrestricted_guest vapic_reg vid ple shadow_vmcs ept_mode_based_exec tsc_scaling
bugs : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass
bogomips : 2188.80
clflush size : 64
cache_alignment : 64
address sizes : 39 bits physical, 48 bits virtual
power management:

processor : 1
vendor_id : GenuineIntel
cpu family : 6
model : 122
model name : Intel(R) Celeron(R) N4100 CPU @ 1.10GHz
stepping : 1
microcode : 0x32
cpu MHz : 1316.799
cache size : 4096 KB
physical id : 0
siblings : 4
core id : 1
cpu cores : 4
apicid : 2
initial apicid : 2
fpu : yes
fpu_exception : yes
cpuid level : 24
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave rdrand lahf_lm 3dnowprefetch cpuid_fault cat_l2 pti cdp_l2 ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust smep erms mpx rdt_a rdseed smap clflushopt intel_pt sha_ni xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts umip rdpid md_clear arch_capabilities
vmx flags : vnmi preemption_timer posted_intr invvpid ept_x_only ept_ad ept_1gb flexpriority apicv tsc_offset vtpr mtf vapic ept vpid unrestricted_guest vapic_reg vid ple shadow_vmcs ept_mode_based_exec tsc_scaling
bugs : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass
bogomips : 2188.80
clflush size : 64
cache_alignment : 64
address sizes : 39 bits physical, 48 bits virtual
power management:

processor : 2
vendor_id : GenuineIntel
cpu family : 6
model : 122
model name : Intel(R) Celeron(R) N4100 CPU @ 1.10GHz
stepping : 1
microcode : 0x32
cpu MHz : 1577.476
cache size : 4096 KB
physical id : 0
siblings : 4
core id : 2
cpu cores : 4
apicid : 4
initial apicid : 4
fpu : yes
fpu_exception : yes
cpuid level : 24
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave rdrand lahf_lm 3dnowprefetch cpuid_fault cat_l2 pti cdp_l2 ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust smep erms mpx rdt_a rdseed smap clflushopt intel_pt sha_ni xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts umip rdpid md_clear arch_capabilities
vmx flags : vnmi preemption_timer posted_intr invvpid ept_x_only ept_ad ept_1gb flexpriority apicv tsc_offset vtpr mtf vapic ept vpid unrestricted_guest vapic_reg vid ple shadow_vmcs ept_mode_based_exec tsc_scaling
bugs : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass
bogomips : 2188.80
clflush size : 64
cache_alignment : 64
address sizes : 39 bits physical, 48 bits virtual
power management:

processor : 3
vendor_id : GenuineIntel
cpu family : 6
model : 122
model name : Intel(R) Celeron(R) N4100 CPU @ 1.10GHz
stepping : 1
microcode : 0x32
cpu MHz : 1227.360
cache size : 4096 KB
physical id : 0
siblings : 4
core id : 3
cpu cores : 4
apicid : 6
initial apicid : 6
fpu : yes
fpu_exception : yes
cpuid level : 24
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave rdrand lahf_lm 3dnowprefetch cpuid_fault cat_l2 pti cdp_l2 ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust smep erms mpx rdt_a rdseed smap clflushopt intel_pt sha_ni xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts umip rdpid md_clear arch_capabilities
vmx flags : vnmi preemption_timer posted_intr invvpid ept_x_only ept_ad ept_1gb flexpriority apicv tsc_offset vtpr mtf vapic ept vpid unrestricted_guest vapic_reg vid ple shadow_vmcs ept_mode_based_exec tsc_scaling
bugs : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass
bogomips : 2188.80
clflush size : 64
cache_alignment : 64
address sizes : 39 bits physical, 48 bits virtual
power management:


// ...............................................................
cat /proc/modules
rfcomm 81920 4 - Live 0x0000000000000000
xt_conntrack 16384 1 - Live 0x0000000000000000
xt_MASQUERADE 20480 1 - Live 0x0000000000000000
nf_conntrack_netlink 49152 0 - Live 0x0000000000000000
xfrm_user 36864 1 - Live 0x0000000000000000
xfrm_algo 16384 1 xfrm_user, Live 0x0000000000000000
nft_counter 16384 15 - Live 0x0000000000000000
xt_addrtype 16384 2 - Live 0x0000000000000000
nft_compat 20480 4 - Live 0x0000000000000000
nft_chain_nat 16384 4 - Live 0x0000000000000000
nf_nat 49152 2 xt_MASQUERADE,nft_chain_nat, Live 0x0000000000000000
nf_conntrack 147456 4 xt_conntrack,xt_MASQUERADE,nf_conntrack_netlink,nf_nat, Live 0x0000000000000000
nf_defrag_ipv6 24576 1 nf_conntrack, Live 0x0000000000000000
nf_defrag_ipv4 16384 1 nf_conntrack, Live 0x0000000000000000
libcrc32c 16384 2 nf_nat,nf_conntrack, Live 0x0000000000000000
nf_tables 196608 45 nft_counter,nft_compat,nft_chain_nat, Live 0x0000000000000000
nfnetlink 16384 4 nf_conntrack_netlink,nft_compat,nf_tables, Live 0x0000000000000000
br_netfilter 28672 0 - Live 0x0000000000000000
bridge 200704 1 br_netfilter, Live 0x0000000000000000
stp 16384 1 bridge, Live 0x0000000000000000
llc 16384 2 bridge,stp, Live 0x0000000000000000
ccm 20480 0 - Live 0x0000000000000000
aufs 262144 0 - Live 0x0000000000000000
cmac 16384 7 - Live 0x0000000000000000
algif_hash 16384 3 - Live 0x0000000000000000
algif_skcipher 16384 3 - Live 0x0000000000000000
overlay 126976 0 - Live 0x0000000000000000
af_alg 28672 14 algif_hash,algif_skcipher, Live 0x0000000000000000
bnep 24576 2 - Live 0x0000000000000000
binfmt_misc 24576 1 - Live 0x0000000000000000
nls_iso8859_1 16384 1 - Live 0x0000000000000000
snd_sof_pci 20480 0 - Live 0x0000000000000000
snd_sof_intel_byt 20480 1 snd_sof_pci, Live 0x0000000000000000
snd_sof_intel_ipc 20480 1 snd_sof_intel_byt, Live 0x0000000000000000
snd_hda_codec_hdmi 61440 1 - Live 0x0000000000000000
snd_sof_intel_hda_common 77824 1 snd_sof_pci, Live 0x0000000000000000
snd_soc_hdac_hda 24576 1 snd_sof_intel_hda_common, Live 0x0000000000000000
snd_sof_xtensa_dsp 16384 2 snd_sof_intel_byt,snd_sof_intel_hda_common, Live 0x0000000000000000
snd_sof_intel_hda 20480 1 snd_sof_intel_hda_common, Live 0x0000000000000000
snd_sof 122880 4 snd_sof_pci,snd_sof_intel_byt,snd_sof_intel_ipc,snd_sof_intel_hda_common, Live 0x0000000000000000
snd_hda_ext_core 32768 3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda, Live 0x0000000000000000
snd_soc_acpi_intel_match 45056 2 snd_sof_pci,snd_sof_intel_hda_common, Live 0x0000000000000000
snd_hda_codec_realtek 131072 1 - Live 0x0000000000000000
snd_hda_codec_generic 81920 1 snd_hda_codec_realtek, Live 0x0000000000000000
snd_soc_acpi 16384 3 snd_sof_intel_byt,snd_sof_intel_hda_common,snd_soc_acpi_intel_match, Live 0x0000000000000000
ledtrig_audio 16384 2 snd_sof,snd_hda_codec_generic, Live 0x0000000000000000
snd_soc_core 278528 3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof, Live 0x0000000000000000
snd_compress 28672 1 snd_soc_core, Live 0x0000000000000000
ac97_bus 16384 1 snd_soc_core, Live 0x0000000000000000
snd_pcm_dmaengine 16384 1 snd_soc_core, Live 0x0000000000000000
snd_hda_intel 53248 2 - Live 0x0000000000000000
snd_intel_dspcfg 24576 3 snd_sof_pci,snd_sof_intel_hda_common,snd_hda_intel, Live 0x0000000000000000
snd_hda_codec 143360 5 snd_hda_codec_hdmi,snd_soc_hdac_hda,snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel, Live 0x0000000000000000
snd_hda_core 94208 9 snd_hda_codec_hdmi,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda,snd_hda_ext_core,snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_codec, Live 0x0000000000000000
mei_hdcp 24576 0 - Live 0x0000000000000000
snd_hwdep 20480 1 snd_hda_codec, Live 0x0000000000000000
intel_pmc_bxt 16384 0 - Live 0x0000000000000000
intel_rapl_msr 20480 0 - Live 0x0000000000000000
intel_telemetry_pltdrv 20480 0 - Live 0x0000000000000000
intel_punit_ipc 16384 1 intel_telemetry_pltdrv, Live 0x0000000000000000
intel_telemetry_core 20480 1 intel_telemetry_pltdrv, Live 0x0000000000000000
x86_pkg_temp_thermal 20480 0 - Live 0x0000000000000000
intel_powerclamp 20480 0 - Live 0x0000000000000000
snd_pcm 118784 9 snd_hda_codec_hdmi,snd_sof_intel_hda_common,snd_sof,snd_soc_core,snd_compress,snd_pcm_dmaengine,snd_hda_intel,snd_hda_codec,snd_hda_core, Live 0x0000000000000000
coretemp 20480 0 - Live 0x0000000000000000
snd_seq_midi 20480 0 - Live 0x0000000000000000
snd_seq_midi_event 16384 1 snd_seq_midi, Live 0x0000000000000000
kvm_intel 282624 0 - Live 0x0000000000000000
kvm 724992 1 kvm_intel, Live 0x0000000000000000
snd_rawmidi 36864 1 snd_seq_midi, Live 0x0000000000000000
crct10dif_pclmul 16384 1 - Live 0x0000000000000000
ghash_clmulni_intel 16384 0 - Live 0x0000000000000000
aesni_intel 372736 10 - Live 0x0000000000000000
snd_seq 73728 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
crypto_simd 16384 1 aesni_intel, Live 0x0000000000000000
i915 2273280 31 - Live 0x0000000000000000
cryptd 24576 5 ghash_clmulni_intel,crypto_simd, Live 0x0000000000000000
glue_helper 16384 1 aesni_intel, Live 0x0000000000000000
rapl 20480 0 - Live 0x0000000000000000
intel_cstate 20480 0 - Live 0x0000000000000000
rt2800usb 32768 0 - Live 0x0000000000000000
rt2x00usb 24576 1 rt2800usb, Live 0x0000000000000000
rt2800lib 135168 1 rt2800usb, Live 0x0000000000000000
rtsx_usb_ms 24576 0 - Live 0x0000000000000000
memstick 24576 1 rtsx_usb_ms, Live 0x0000000000000000
efi_pstore 16384 0 - Live 0x0000000000000000
rt2x00lib 65536 3 rt2800usb,rt2x00usb,rt2800lib, Live 0x0000000000000000
btusb 57344 0 - Live 0x0000000000000000
btrtl 24576 1 btusb, Live 0x0000000000000000
drm_kms_helper 225280 1 i915, Live 0x0000000000000000
btbcm 16384 1 btusb, Live 0x0000000000000000
snd_seq_device 16384 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x0000000000000000
iwlmvm 405504 0 - Live 0x0000000000000000
btintel 28672 1 btusb, Live 0x0000000000000000
cec 53248 2 i915,drm_kms_helper, Live 0x0000000000000000
snd_timer 40960 2 snd_pcm,snd_seq, Live 0x0000000000000000
bluetooth 602112 33 rfcomm,bnep,btusb,btrtl,btbcm,btintel, Live 0x0000000000000000
joydev 28672 0 - Live 0x0000000000000000
rc_core 53248 1 cec, Live 0x0000000000000000
input_leds 16384 0 - Live 0x0000000000000000
mac80211 917504 4 rt2x00usb,rt2800lib,rt2x00lib,iwlmvm, Live 0x0000000000000000
libarc4 16384 1 mac80211, Live 0x0000000000000000
i2c_algo_bit 16384 1 i915, Live 0x0000000000000000
8250_dw 16384 0 - Live 0x0000000000000000
fb_sys_fops 16384 1 drm_kms_helper, Live 0x0000000000000000
mei_me 40960 1 - Live 0x0000000000000000
snd 94208 17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_codec_generic,snd_soc_core,snd_compress,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer, Live 0x0000000000000000
iwlwifi 364544 1 iwlmvm, Live 0x0000000000000000
syscopyarea 16384 1 drm_kms_helper, Live 0x0000000000000000
sysfillrect 16384 1 drm_kms_helper, Live 0x0000000000000000
ecdh_generic 16384 2 bluetooth, Live 0x0000000000000000
ecc 32768 1 ecdh_generic, Live 0x0000000000000000
mei 110592 3 mei_hdcp,mei_me, Live 0x0000000000000000
soundcore 16384 1 snd, Live 0x0000000000000000
cfg80211 782336 4 rt2x00lib,iwlmvm,mac80211,iwlwifi, Live 0x0000000000000000
sysimgblt 16384 1 drm_kms_helper, Live 0x0000000000000000
processor_thermal_device 24576 0 - Live 0x0000000000000000
intel_rapl_common 28672 2 intel_rapl_msr,processor_thermal_device, Live 0x0000000000000000
intel_soc_dts_iosf 20480 1 processor_thermal_device, Live 0x0000000000000000
mac_hid 16384 0 - Live 0x0000000000000000
int3400_thermal 20480 0 - Live 0x0000000000000000
acpi_thermal_rel 16384 1 int3400_thermal, Live 0x0000000000000000
dptf_power 16384 0 - Live 0x0000000000000000
int3403_thermal 20480 0 - Live 0x0000000000000000
int3406_thermal 16384 0 - Live 0x0000000000000000
int340x_thermal_zone 16384 2 processor_thermal_device,int3403_thermal, Live 0x0000000000000000
sch_fq_codel 20480 2 - Live 0x0000000000000000
parport_pc 45056 0 - Live 0x0000000000000000
ppdev 24576 0 - Live 0x0000000000000000
lp 20480 0 - Live 0x0000000000000000
parport 65536 3 parport_pc,ppdev,lp, Live 0x0000000000000000
drm 565248 8 i915,drm_kms_helper, Live 0x0000000000000000
ip_tables 32768 0 - Live 0x0000000000000000
x_tables 45056 5 xt_conntrack,xt_MASQUERADE,xt_addrtype,nft_compat,ip_tables, Live 0x0000000000000000
autofs4 45056 2 - Live 0x0000000000000000
hid_generic 16384 0 - Live 0x0000000000000000
rtsx_usb_sdmmc 36864 0 - Live 0x0000000000000000
usbhid 57344 0 - Live 0x0000000000000000
hid 135168 2 hid_generic,usbhid, Live 0x0000000000000000
rtsx_usb 28672 2 rtsx_usb_ms,rtsx_usb_sdmmc, Live 0x0000000000000000
spi_pxa2xx_platform 32768 0 - Live 0x0000000000000000
dw_dmac 16384 0 - Live 0x0000000000000000
dw_dmac_core 32768 1 dw_dmac, Live 0x0000000000000000
crc32_pclmul 16384 0 - Live 0x0000000000000000
i2c_i801 32768 0 - Live 0x0000000000000000
i2c_smbus 20480 1 i2c_i801, Live 0x0000000000000000
intel_lpss_pci 20480 6 - Live 0x0000000000000000
intel_lpss 16384 1 intel_lpss_pci, Live 0x0000000000000000
xhci_pci 20480 0 - Live 0x0000000000000000
idma64 20480 0 - Live 0x0000000000000000
xhci_pci_renesas 20480 1 xhci_pci, Live 0x0000000000000000
virt_dma 20480 1 idma64, Live 0x0000000000000000
ahci 40960 2 - Live 0x0000000000000000
sdhci_pci 57344 0 - Live 0x0000000000000000
r8169 94208 0 - Live 0x0000000000000000
cqhci 32768 1 sdhci_pci, Live 0x0000000000000000
sdhci 69632 1 sdhci_pci, Live 0x0000000000000000
realtek 24576 1 - Live 0x0000000000000000
libahci 36864 1 ahci, Live 0x0000000000000000
video 49152 2 i915,int3406_thermal, Live 0x0000000000000000
pinctrl_geminilake 24576 0 - Live 0x0000000000000000
pinctrl_intel 28672 1 pinctrl_geminilake, Live 0x0000000000000000

// ...............................................................
cat /proc/ioports
0000-0000 : PCI Bus 0000:00
  0000-0000 : dma1
  0000-0000 : pic1
  0000-0000 : timer0
  0000-0000 : timer1
  0000-0000 : keyboard
  0000-0000 : keyboard
0000-0000 : PCI Bus 0000:00
  0000-0000 : rtc0
0000-0000 : PCI Bus 0000:00
  0000-0000 : dma page reg
  0000-0000 : pic2
  0000-0000 : dma2
  0000-0000 : fpu
  0000-0000 : ACPI PM1a_EVT_BLK
  0000-0000 : ACPI PM1a_CNT_BLK
  0000-0000 : ACPI PM_TMR
  0000-0000 : ACPI GPE0_BLK
  0000-0000 : ACPI PM2_CNT_BLK
  0000-0000 : wdat_wdt
  0000-0000 : wdat_wdt
  0000-0000 : wdat_wdt
  0000-0000 : wdat_wdt
  0000-0000 : pnp 00:00
  0000-0000 : pnp 00:00
  0000-0000 : pnp 00:00
0000-0000 : PCI conf1
0000-0000 : PCI Bus 0000:00
  0000-0000 : pnp 00:00
  0000-0000 : PCI Bus 0000:02
    0000-0000 : 0000:02:00.0
  0000-0000 : 0000:00:02.0
  0000-0000 : 0000:00:1f.1
    0000-0000 : i801_smbus
  0000-0000 : 0000:00:12.0
    0000-0000 : ahci
  0000-0000 : 0000:00:12.0
    0000-0000 : ahci
  0000-0000 : 0000:00:12.0
    0000-0000 : ahci


// ...............................................................
cat /proc/iomem
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
  00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : PCI Bus 0000:00
    00000000-00000000 : System ROM
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : ACPI Tables
00000000-00000000 : ACPI Non-volatile Storage
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
  00000000-00000000 : PCI Bus 0000:00
    00000000-00000000 : Graphics Stolen Memory
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : 0000:00:00.1
  00000000-00000000 : 0000:00:18.2
  00000000-00000000 : 0000:00:02.0
  00000000-00000000 : 0000:00:02.0
  00000000-00000000 : 0000:00:0e.0
    00000000-00000000 : ICH HD audio
  00000000-00000000 : PCI Bus 0000:02
    00000000-00000000 : 0000:02:00.0
    00000000-00000000 : 0000:02:00.0
      00000000-00000000 : r8169
  00000000-00000000 : 0000:00:15.0
    00000000-00000000 : xhci-hcd
  00000000-00000000 : 0000:00:0e.0
    00000000-00000000 : ICH HD audio
  00000000-00000000 : 0000:00:0c.0
    00000000-00000000 : iwlwifi
  00000000-00000000 : 0000:00:12.0
    00000000-00000000 : ahci
  00000000-00000000 : 0000:00:1f.1
  00000000-00000000 : 0000:00:1e.0
  00000000-00000000 : 0000:00:1e.0
    00000000-00000000 : mmc1
  00000000-00000000 : 0000:00:1c.0
  00000000-00000000 : 0000:00:1c.0
    00000000-00000000 : mmc0
  00000000-00000000 : 0000:00:19.2
  00000000-00000000 : 0000:00:19.2
    00000000-00000000 : lpss_dev
      00000000-00000000 : pxa2xx-spi.14 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.14
      00000000-00000000 : idma64.14 idma64.14
  00000000-00000000 : 0000:00:19.1
  00000000-00000000 : 0000:00:19.1
    00000000-00000000 : lpss_dev
      00000000-00000000 : pxa2xx-spi.13 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.13
      00000000-00000000 : idma64.13 idma64.13
  00000000-00000000 : 0000:00:19.0
  00000000-00000000 : 0000:00:19.0
    00000000-00000000 : lpss_dev
      00000000-00000000 : pxa2xx-spi.12 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.12
      00000000-00000000 : idma64.12 idma64.12
  00000000-00000000 : 0000:00:18.3
  00000000-00000000 : 0000:00:18.3
    00000000-00000000 : lpss_dev
      00000000-00000000 : serial
    00000000-00000000 : lpss_priv
  00000000-00000000 : 0000:00:18.1
  00000000-00000000 : 0000:00:18.1
    00000000-00000000 : lpss_dev
      00000000-00000000 : serial
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.9
      00000000-00000000 : idma64.9 idma64.9
  00000000-00000000 : 0000:00:18.0
  00000000-00000000 : 0000:00:18.0
    00000000-00000000 : lpss_dev
      00000000-00000000 : serial
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.8
      00000000-00000000 : idma64.8 idma64.8
  00000000-00000000 : 0000:00:17.3
  00000000-00000000 : 0000:00:17.3
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.7 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.7
      00000000-00000000 : idma64.7 idma64.7
  00000000-00000000 : 0000:00:17.2
  00000000-00000000 : 0000:00:17.2
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.6 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.6
      00000000-00000000 : idma64.6 idma64.6
  00000000-00000000 : 0000:00:17.1
  00000000-00000000 : 0000:00:17.1
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.5 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.5
      00000000-00000000 : idma64.5 idma64.5
  00000000-00000000 : 0000:00:17.0
  00000000-00000000 : 0000:00:17.0
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.4 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.4
      00000000-00000000 : idma64.4 idma64.4
  00000000-00000000 : 0000:00:16.3
  00000000-00000000 : 0000:00:16.3
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.3 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.3
      00000000-00000000 : idma64.3 idma64.3
  00000000-00000000 : 0000:00:16.2
  00000000-00000000 : 0000:00:16.2
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.2 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.2
      00000000-00000000 : idma64.2 idma64.2
  00000000-00000000 : 0000:00:16.1
  00000000-00000000 : 0000:00:16.1
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.1 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.1
      00000000-00000000 : idma64.1 idma64.1
  00000000-00000000 : 0000:00:16.0
  00000000-00000000 : 0000:00:16.0
    00000000-00000000 : lpss_dev
      00000000-00000000 : i2c_designware.0 lpss_dev
    00000000-00000000 : lpss_priv
    00000000-00000000 : idma64.0
      00000000-00000000 : idma64.0 idma64.0
  00000000-00000000 : 0000:00:12.0
    00000000-00000000 : ahci
  00000000-00000000 : 0000:00:12.0
    00000000-00000000 : ahci
  00000000-00000000 : 0000:00:0f.0
    00000000-00000000 : mei_me
00000000-00000000 : Reserved
  00000000-00000000 : INT3453:00
    00000000-00000000 : INT3453:00 INT3453:00
  00000000-00000000 : INT3453:01
    00000000-00000000 : INT3453:01 INT3453:01
  00000000-00000000 : INT3453:03
    00000000-00000000 : INT3453:03 INT3453:03
  00000000-00000000 : INT3453:02
    00000000-00000000 : INT3453:02 INT3453:02
00000000-00000000 : Reserved
00000000-00000000 : PCI MMCONFIG 0000 [bus 00-ff]
  00000000-00000000 : Reserved
    00000000-00000000 : PCI Bus 0000:00
      00000000-00000000 : pnp 00:01
00000000-00000000 : Reserved
00000000-00000000 : Reserved
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : 0000:00:18.2
    00000000-00000000 : lpss_dev
      00000000-00000000 : serial
    00000000-00000000 : lpss_priv
00000000-00000000 : Reserved
  00000000-00000000 : IOAPIC 0
00000000-00000000 : HPET 0
  00000000-00000000 : PNP0103:00
    00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : Reserved
  00000000-00000000 : PCI Bus 0000:00
    00000000-00000000 : pnp 00:01
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : pnp 00:01
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : pnp 00:01
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : pnp 00:01
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : pnp 00:01
00000000-00000000 : MSFT0101:00
  00000000-00000000 : MSFT0101:00
00000000-00000000 : dmar0
00000000-00000000 : dmar1
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : pnp 00:01
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : Local APIC
    00000000-00000000 : Reserved
00000000-00000000 : Reserved
00000000-00000000 : System RAM
  00000000-00000000 : Kernel code
  00000000-00000000 : Kernel rodata
  00000000-00000000 : Kernel data
  00000000-00000000 : Kernel bss


// ...............................................................
lspci -vvv
00:00.0 Host bridge: Intel Corporation Gemini Lake Host Bridge (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Gemini Lake Host Bridge
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0

00:00.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Dynamic Platform and Thermal Framework Processor Participant (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Dynamic Platform and Thermal Framework Processor Participant
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
Latency: 0
Interrupt: pin B routed to IRQ 24
Region 0: Memory at 80000000 (64-bit, non-prefetchable) [size=32K]
Capabilities: <access denied>
Kernel driver in use: proc_thermal
Kernel modules: processor_thermal_device

00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 605 (rev 03) (prog-if 00 [VGA controller])
DeviceName: Onboard - Video
Subsystem: Device 1e50:8003
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 134
Region 0: Memory at a0000000 (64-bit, non-prefetchable) [size=16M]
Region 2: Memory at 90000000 (64-bit, prefetchable) [size=256M]
Region 4: I/O ports at f000 [size=64]
Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:0c.0 Network controller: Intel Corporation Device 31dc (rev 03)
DeviceName: Onboard - Ethernet
Subsystem: Intel Corporation Device 02a4
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 44
Region 0: Memory at a1214000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: iwlwifi
Kernel modules: iwlwifi

00:0e.0 Audio device: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio (rev 03) (prog-if 80)
DeviceName: Onboard - Sound
Subsystem: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 135
Region 0: Memory at a1210000 (64-bit, non-prefetchable) [size=16K]
Region 4: Memory at a1000000 (64-bit, non-prefetchable) [size=1M]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel, snd_sof_pci

00:0f.0 Communication controller: Intel Corporation Celeron/Pentium Silver Processor Trusted Execution Engine Interface (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Trusted Execution Engine Interface
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 133
Region 0: Memory at a123d000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: mei_me
Kernel modules: mei_me

00:12.0 SATA controller: Intel Corporation Device 31e3 (rev 03) (prog-if 01 [AHCI 1.0])
DeviceName: Onboard - SATA
Subsystem: Intel Corporation Device 7270
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 125
Region 0: Memory at a1218000 (32-bit, non-prefetchable) [size=8K]
Region 1: Memory at a123c000 (32-bit, non-prefetchable) [size=256]
Region 2: I/O ports at f090 [size=8]
Region 3: I/O ports at f080 [size=4]
Region 4: I/O ports at f060 [size=32]
Region 5: Memory at a123b000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: ahci
Kernel modules: ahci

00:13.0 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f3) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 122
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000f000-00000fff [disabled]
Memory behind bridge: fff00000-000fffff [disabled]
Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff [disabled]
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16+ MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport

00:13.1 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f3) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin B routed to IRQ 123
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
I/O behind bridge: 0000e000-0000efff [size=4K]
Memory behind bridge: a1100000-a11fffff [size=1M]
Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff [disabled]
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16+ MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport

00:15.0 USB controller: Intel Corporation Device 31a8 (rev 03) (prog-if 30 [XHCI])
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 126
Region 0: Memory at a1200000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: xhci_hcd
Kernel modules: xhci_pci

00:16.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 27
Region 0: Memory at a123a000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1239000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:16.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin B routed to IRQ 28
Region 0: Memory at a1238000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1237000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:16.2 Signal processing controller: Intel Corporation Device 31b0 (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin C routed to IRQ 29
Region 0: Memory at a1236000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1235000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:16.3 Signal processing controller: Intel Corporation Device 31b2 (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin D routed to IRQ 30
Region 0: Memory at a1234000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1233000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:17.0 Signal processing controller: Intel Corporation Device 31b4 (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 31
Region 0: Memory at a1232000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1231000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:17.1 Signal processing controller: Intel Corporation Device 31b6 (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin B routed to IRQ 32
Region 0: Memory at a1230000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a122f000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:17.2 Signal processing controller: Intel Corporation Device 31b8 (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin C routed to IRQ 33
Region 0: Memory at a122e000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a122d000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:17.3 Signal processing controller: Intel Corporation Device 31ba (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin D routed to IRQ 34
Region 0: Memory at a122c000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a122b000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:18.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 4
Region 0: Memory at a122a000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1229000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:18.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin B routed to IRQ 5
Region 0: Memory at a1228000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1227000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:18.2 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin C routed to IRQ 6
Region 0: Memory at fea10000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at 80008000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:18.3 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin D routed to IRQ 7
Region 0: Memory at a1226000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1225000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:19.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 35
Region 0: Memory at a1224000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1223000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:19.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin B routed to IRQ 36
Region 0: Memory at a1222000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a1221000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:19.2 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin C routed to IRQ 37
Region 0: Memory at a1220000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a121f000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: intel-lpss
Kernel modules: intel_lpss_pci

00:1c.0 SD Host controller: Intel Corporation Celeron/Pentium Silver Processor SDA Standard Compliant SD Host Controller (rev 03) (prog-if 01)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor SDA Standard Compliant SD Host Controller
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 39
Region 0: Memory at a121e000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a121d000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: sdhci-pci
Kernel modules: sdhci_pci

00:1e.0 SD Host controller: Intel Corporation Device 31d0 (rev 03) (prog-if 01)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 42
Region 0: Memory at a121c000 (64-bit, non-prefetchable) [size=4K]
Region 2: Memory at a121b000 (64-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: sdhci-pci
Kernel modules: sdhci_pci

00:1f.0 ISA bridge: Intel Corporation Device 31e8 (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Device 7270
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0

00:1f.1 SMBus: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model (rev 03)
DeviceName: Onboard - Other
Subsystem: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model
Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Interrupt: pin A routed to IRQ 20
Region 0: Memory at a121a000 (64-bit, non-prefetchable) [size=256]
Region 4: I/O ports at f040 [size=32]
Kernel driver in use: i801_smbus
Kernel modules: i2c_i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 23
Region 0: I/O ports at e000 [size=256]
Region 2: Memory at a1104000 (64-bit, non-prefetchable) [size=4K]
Region 4: Memory at a1100000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169


// ...............................................................
/proc/scsi/scsi
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: KINGSTON RBUSNS8 Rev: 61D1
  Type:   Direct-Access                    ANSI  SCSI revision: 05

```

---

### Post by chili555 on 2020-11-27
We see this clue in your dmesg:

> Conflict between TLV & NVM regarding enabling LAR (TLV = enabled NVM =disabled)

I suggested that you try a driver parameter:

```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi lar_disable=Y
```
If seems to have solved the issue, then I suggest that you make it permanent:

```
sudo -i
echo "options iwlwifi lar_disable=Y"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```
Please post back your success.

---

### Post by *g!t5^_)*(H on 2020-11-29
No, it does not work. Also tried combinations of:

11n_disable=1
power_save=0
bt_coex_active=0
swcrypto=1

Without success

---

