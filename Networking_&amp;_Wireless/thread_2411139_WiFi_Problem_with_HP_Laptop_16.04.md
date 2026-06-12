---
title: "WiFi Problem with HP Laptop 16.04"
date: 2019-01-25
forum: Networking &amp; Wireless
---

### Post by alexandrosfa on 2019-01-25
Hi! I installed Ubuntu 16.04 to a HP Laptop and though it detects wifi networks it doesn't connect to them (or just connects for some minutes and then never connects again).

It is not a hardware problem as the WiFi was working perfectly on Windows.

I have tried some online guides but to no avail. Can you please help me?

```
~$ lspci | grep -i wireless

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter 
```

```
~$ lsmod
Module                  Size  Used by
ebtable_filter         16384  0
ebtables               32768  1 ebtable_filter
xt_CHECKSUM            16384  2
iptable_mangle         16384  1
ipt_MASQUERADE         16384  4
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
bridge                126976  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
rfcomm                 69632  0
bnep                   20480  2
binfmt_misc            20480  1
arc4                   16384  2
rtl8723be             143360  0
btcoexist             188416  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
snd_hda_codec_hdmi     53248  1
wl                   6447104  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_soc_skl            49152  0
snd_soc_skl_ipc        32768  1 snd_soc_skl
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_soc_core          212992  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
dw_dmac_core           24576  1 snd_soc_sst_dsp
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           77824  7 snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
snd_hwdep              16384  1 snd_hda_codec
hp_wmi                 16384  0
snd_pcm               106496  8 snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_pcm_dmaengine,snd_hda_core
sparse_keymap          16384  1 hp_wmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd_rawmidi            32768  1 snd_seq_midi
media                  24576  2 uvcvideo,videodev
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd                    81920  19 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
cfg80211              565248  3 wl,mac80211,rtlwifi
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
soundcore              16384  1 snd
i2c_i801               28672  0
mei_me                 36864  0
shpchp                 36864  0
mei                    98304  1 mei_me
kvm                   552960  0
processor_thermal_device    16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
intel_soc_dts_iosf     16384  1 processor_thermal_device
irqbypass              16384  1 kvm
int3400_thermal        16384  0
hp_wireless            16384  0
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad               24576  0
mac_hid                16384  0
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  3
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  29
xt_addrtype            16384  4
nf_conntrack_ipv4      20480  10
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  17
ip6table_filter        16384  1
ip6_tables             28672  53 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 28672  3 nf_nat_ftp,nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          106496  10 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         16384  1
ip_tables              24576  13 iptable_filter,iptable_mangle,iptable_nat
parport_pc             32768  0
x_tables               36864  17 ip6table_filter,xt_hl,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ebtables,ip6t_rt,ipt_REJECT,iptable_mangle,ip6_tables,xt_addrtype,ip6t_REJECT
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
drbg                   32768  1
ansi_cprng             16384  0
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  2 hid_generic,usbhid
crct10dif_pclmul       16384  0
amdkfd                131072  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
i915_bpo             1335296  3
amd_iommu_v2           20480  1 amdkfd
aesni_intel           167936  243
radeon               1523712  1
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  124 ghash_clmulni_intel,aesni_intel,ablk_helper
intel_ips              20480  1 i915_bpo
ttm                    98304  1 radeon
i2c_algo_bit           16384  2 i915_bpo,radeon
drm_kms_helper        155648  2 i915_bpo,radeon
psmouse               131072  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  7 ttm,i915_bpo,drm_kms_helper,radeon
r8169                  86016  0
ahci                   40960  3
mii                    16384  1 r8169
libahci                32768  1 ahci
wmi                    20480  1 hp_wmi
video                  40960  1 i915_bpo
fjes                   28672  0
```

---

### Post by kc1di on 2019-01-25
does this machine have secure boot activated if so turn it off.   It is not compatible with the RTL8723be.

---

### Post by alexandrosfa on 2019-01-25
Thank you very much for your answer. How do I check that and if it does, how do I disable it?

---

### Post by kc1di on 2019-01-25
It depends on the make of the machine.  How ever you enter into your bios screen it's usually a F key.
once in bios look for secure boot and turn it off.

---

### Post by kc1di on 2019-01-25
Also please give us the model of your HP that may help.

---

### Post by praseodym on 2019-01-25
Please run

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=[COLOR="#FF0000"]1[/COLOR]" | sudo tee /etc/modprobe.d/rtl8723be_options.conf
```
Reboot. If its not working better, change the red "1" to "2"

---

### Post by alexandrosfa on 2019-01-25
>  sudo dmidecode | grep -A 9 "System Information"

System Information
	Manufacturer: HP
	Product Name: HP Notebook
	Version: Type1ProductConfigId
	Serial Number: CND6200PP5
	UUID: 11AC2D6A-6812-E611-B27E-A08CFD4CABA3
	Wake-up Type: Power Switch
	SKU Number: E9P75EA#AB7
	Family: 103C_5335KV G=N L=CON B=HP      

```
 sudo dmidecode -t system# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.


Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: HP
	Product Name: HP Notebook
	Version: Type1ProductConfigId
	Serial Number: CND6200PP5
	UUID: 11AC2D6A-6812-E611-B27E-A08CFD4CABA3
	Wake-up Type: Power Switch
	SKU Number: E9P75EA#AB7
	Family: 103C_5335KV G=N L=CON B=HP        


Handle 0x0022, DMI type 12, 5 bytes
System Configuration Options
	Option 1: ConfigOptions1
	Option 2: ConfigOptions2
	Option 3: ConfigOptions3
	Option 4: ConfigOptions4
	Option 5: ConfigOptions5
	Option 6: ConfigOptions6
	Option 7: ConfigOptions7
	Option 8: ConfigOptions8


Handle 0x0027, DMI type 15, 29 bytes
System Event Log
	Area Length: 0 bytes
	Header Start Offset: 0x0000
	Header Length: 8192 bytes
	Data Start Offset: 0x2000
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x12345678
	Header Format: OEM-specific
	Supported Log Type Descriptors: 3
	Descriptor 1: POST memory resize
	Data Format 1: None
	Descriptor 2: POST error
	Data Format 2: POST results bitmap
	Descriptor 3: Log area reset/cleared
	Data Format 3: None


Handle 0x0033, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected 
```

---

### Post by alexandrosfa on 2019-01-25
Secure boot is disabled.

---

### Post by jeremy31 on 2019-01-25
Do ```
sudo apt remove bsmwl-kernel-source
```
Post what kernel you are using ```
uname -a
```

---

### Post by alexandrosfa on 2019-01-25
[COLOR=#1D2129][FONT=&quot][FONT=inherit][FONT=inherit][FONT=inherit]I am following this guide: [https://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04](https://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04)

and it seems to work. How about reboots though and kernel updates.

Will it still work?[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]
```
$ sudo git clone https://github.com/lwfinger/rtlwifi_new.git
fatal: destination path 'rtlwifi_new' already exists and is not an empty directory.
```

```
 cd rtlwifi_new/ && git checkout origin/extended -b extended
Branch extended set up to track remote branch extended from origin.
Switched to a new branch 'extended'
angie@angie-HP-Notebook:~/rtlwifi_new$ 
```


```
 ~/rtlwifi_new$ make
make -C /lib/modules/4.4.0-141-generic/build M=/home/angie/rtlwifi_new modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-141-generic'
  CC [M]  /home/angie/rtlwifi_new/base.o
  CC [M]  /home/angie/rtlwifi_new/cam.o
  CC [M]  /home/angie/rtlwifi_new/core.o
/home/angie/rtlwifi_new/core.c:2268:18: warning: initialization from incompatible pointer type [-Wincompatible-pointer-types]
  .ampdu_action = rtl_op_ampdu_action,
                  ^
/home/angie/rtlwifi_new/core.c:2268:18: note: (near initialization for &#8216;rtl_ops.ampdu_action&#8217;)
  CC [M]  /home/angie/rtlwifi_new/debug.o
  CC [M]  /home/angie/rtlwifi_new/efuse.o
  CC [M]  /home/angie/rtlwifi_new/ps.o
  CC [M]  /home/angie/rtlwifi_new/rc.o
  CC [M]  /home/angie/rtlwifi_new/regd.o
  CC [M]  /home/angie/rtlwifi_new/stats.o
  LD [M]  /home/angie/rtlwifi_new/rtlwifi.o
  CC [M]  /home/angie/rtlwifi_new/pci.o
  LD [M]  /home/angie/rtlwifi_new/rtl_pci.o
  CC [M]  /home/angie/rtlwifi_new/usb.o
  LD [M]  /home/angie/rtlwifi_new/rtl_usb.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8192e2ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8723b1ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8723b2ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8821a1ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8821a2ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8822b1ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8822b2ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8822bwifionly.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8723d1ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtc8723d2ant.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/halbtcoutsrc.o
  CC [M]  /home/angie/rtlwifi_new/btcoexist/rtl_btc.o
  LD [M]  /home/angie/rtlwifi_new/btcoexist/btcoexist.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_api.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_api_88xx_usb.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_api_88xx_sdio.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_api_88xx.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_api_88xx_pcie.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_func_88xx.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_8822b/halmac_api_8822b_pcie.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_8822b/halmac_func_8822b.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_8822b/halmac_api_8822b_sdio.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_8822b/halmac_api_8822b.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_8822b/halmac_8822b_phy.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_8822b/halmac_8822b_pwr_seq.o
  CC [M]  /home/angie/rtlwifi_new/halmac/halmac_88xx/halmac_8822b/halmac_api_8822b_usb.o
  CC [M]  /home/angie/rtlwifi_new/halmac/rtl_halmac.o
  LD [M]  /home/angie/rtlwifi_new/halmac/halmac.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_debug.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_antdiv.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_soml.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_smt_ant.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_interface.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_phystatus.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_hwconfig.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_dig.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_pathdiv.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_rainfo.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_dynamictxpower.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_adaptivity.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_cfotracking.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_noisemonitor.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_dfs.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_adc_sampling.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_ccx.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_psd.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_primary_cca.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_cck_pd.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_rssi_monitor.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_auto_dbg.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_math_lib.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_api.o
  CC [M]  /home/angie/rtlwifi_new/phydm/phydm_pow_train.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/halrf.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/halphyrf_ce.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/halrf_powertracking_ce.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/halrf_powertracking.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/halrf_kfree.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/rtl8822b/halrf_8822b.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/rtl8822b/halrf_iqk_8822b.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8822b/halhwimg8822b_bb.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8822b/halhwimg8822b_mac.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8822b/halhwimg8822b_rf.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8822b/phydm_hal_api8822b.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8822b/phydm_regconfig8822b.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8822b/phydm_rtl8822b.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8723d/halhwimg8723d_bb.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8723d/halhwimg8723d_mac.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8723d/halhwimg8723d_rf.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8723d/phydm_regconfig8723d.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl8723d/phydm_rtl8723d.o
  CC [M]  /home/angie/rtlwifi_new/phydm/halrf/rtl8723d/halrf_8723d.o
  CC [M]  /home/angie/rtlwifi_new/phydm/rtl_phydm.o
  LD [M]  /home/angie/rtlwifi_new/phydm/phydm_mod.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/pwrseq.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8188ee/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8188ee/rtl8188ee.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192c/main.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192c/dm_common.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192c/fw_common.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192c/phy_common.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192c/rtl8192c-common.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ce/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192ce/rtl8192ce.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/mac.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192cu/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192cu/rtl8192cu.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192de/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192de/rtl8192de.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/pwrseq.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192ee/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192ee/rtl8192ee.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8192se/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192se/rtl8192se.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/hal_btc.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/hal_bt_coexist.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/pwrseq.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723ae/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723ae/rtl8723ae.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/pwrseq.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723be/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723be/rtl8723be.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723com/main.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723com/dm_common.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723com/fw_common.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723com/phy_common.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723com/rtl8723-common.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/pwrseq.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8723de/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723de/rtl8723de.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/dm.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/pwrseq.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/rf.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/table.o
  CC [M]  /home/angie/rtlwifi_new/rtl8821ae/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8821ae/rtl8821ae.o
  CC [M]  /home/angie/rtlwifi_new/rtl8822be/fw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8822be/hw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8822be/led.o
  CC [M]  /home/angie/rtlwifi_new/rtl8822be/phy.o
  CC [M]  /home/angie/rtlwifi_new/rtl8822be/sw.o
  CC [M]  /home/angie/rtlwifi_new/rtl8822be/trx.o
  LD [M]  /home/angie/rtlwifi_new/rtl8822be/rtl8822be.o
  Building modules, stage 2.
  MODPOST 19 modules
  CC      /home/angie/rtlwifi_new/btcoexist/btcoexist.mod.o
  LD [M]  /home/angie/rtlwifi_new/btcoexist/btcoexist.ko
  CC      /home/angie/rtlwifi_new/halmac/halmac.mod.o
  LD [M]  /home/angie/rtlwifi_new/halmac/halmac.ko
  CC      /home/angie/rtlwifi_new/phydm/phydm_mod.mod.o
  LD [M]  /home/angie/rtlwifi_new/phydm/phydm_mod.ko
  CC      /home/angie/rtlwifi_new/rtl8188ee/rtl8188ee.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8188ee/rtl8188ee.ko
  CC      /home/angie/rtlwifi_new/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192c/rtl8192c-common.ko
  CC      /home/angie/rtlwifi_new/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192ce/rtl8192ce.ko
  CC      /home/angie/rtlwifi_new/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192cu/rtl8192cu.ko
  CC      /home/angie/rtlwifi_new/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192de/rtl8192de.ko
  CC      /home/angie/rtlwifi_new/rtl8192ee/rtl8192ee.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192ee/rtl8192ee.ko
  CC      /home/angie/rtlwifi_new/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8192se/rtl8192se.ko
  CC      /home/angie/rtlwifi_new/rtl8723ae/rtl8723ae.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723ae/rtl8723ae.ko
  CC      /home/angie/rtlwifi_new/rtl8723be/rtl8723be.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723be/rtl8723be.ko
  CC      /home/angie/rtlwifi_new/rtl8723com/rtl8723-common.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723com/rtl8723-common.ko
  CC      /home/angie/rtlwifi_new/rtl8723de/rtl8723de.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8723de/rtl8723de.ko
  CC      /home/angie/rtlwifi_new/rtl8821ae/rtl8821ae.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8821ae/rtl8821ae.ko
  CC      /home/angie/rtlwifi_new/rtl8822be/rtl8822be.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl8822be/rtl8822be.ko
  CC      /home/angie/rtlwifi_new/rtl_pci.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl_pci.ko
  CC      /home/angie/rtlwifi_new/rtl_usb.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtl_usb.ko
  CC      /home/angie/rtlwifi_new/rtlwifi.mod.o
  LD [M]  /home/angie/rtlwifi_new/rtlwifi.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-141-generic' 
```

```
 ~/rtlwifi_new$ sudo make install
make -C /lib/modules/4.4.0-141-generic/build M=/home/angie/rtlwifi_new modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-141-generic'
  Building modules, stage 2.
  MODPOST 19 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-141-generic'
Install rtlwifi SUCCESS 
```

```
  ~/rtlwifi_new$ sudo modprobe -r rtl8723be 
```

```
 ~/rtlwifi_new$ sudo modprobe rtl8723be  
```

---

### Post by jeremy31 on 2019-01-26
If you want that to survive kernel updates do
```
sudo apt install dkms
cd ~/rtlwifi_new
make clean
cd
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

---

### Post by alexandrosfa on 2019-01-26
[SIZE=4]Did that and this was the final output. Is it correct?

```
[/SIZE]~$ sudo dkms add ./rtlwifi_new

Creating symlink /var/lib/dkms/rtlwifi-new/0.6/source ->
                 /usr/src/rtlwifi-new-0.6


DKMS: add completed.
angie@angie-HP-Notebook:~$ sudo dkms install rtlwifi-new/0.6


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area.....(bad exit status: 2)
make KERNELRELEASE=4.4.0-141-generic -C /lib/modules/4.4.0-141-generic/build M=/var/lib/dkms/rtlwifi-new/0.6/build.......................................
cleaning build area.....(bad exit status: 2)


DKMS: build completed.


rtl_pci.ko:
Running module version sanity check.


Good news! Module version  for rtl_pci.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl_usb.ko:
Running module version sanity check.


Good news! Module version  for rtl_usb.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtlwifi.ko:
Running module version sanity check.


Good news! Module version  for rtlwifi.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


btcoexist.ko:
Running module version sanity check.


Good news! Module version  for btcoexist.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


halmac.ko:
Running module version sanity check.


Good news! Module version  for halmac.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


phydm_mod.ko:
Running module version sanity check.


Good news! Module version  for phydm_mod.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8188ee.ko:
Running module version sanity check.


Good news! Module version  for rtl8188ee.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8192c-common.ko:
Running module version sanity check.


Good news! Module version  for rtl8192c-common.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8192ce.ko:
Running module version sanity check.


Good news! Module version  for rtl8192ce.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8192cu.ko:
Running module version sanity check.


Good news! Module version  for rtl8192cu.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8192de.ko:
Running module version sanity check.


Good news! Module version  for rtl8192de.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8192ee.ko:
Running module version sanity check.


Good news! Module version  for rtl8192ee.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8192se.ko:
Running module version sanity check.


Good news! Module version  for rtl8192se.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8723ae.ko:
Running module version sanity check.


Good news! Module version  for rtl8723ae.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8723be.ko:
Running module version sanity check.


Good news! Module version  for rtl8723be.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8723de.ko:
Running module version sanity check.


Good news! Module version  for rtl8723de.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8723-common.ko:
Running module version sanity check.


Good news! Module version  for rtl8723-common.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8821ae.ko:
Running module version sanity check.


Good news! Module version  for rtl8821ae.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


rtl8822be.ko:
Running module version sanity check.


Good news! Module version  for rtl8822be.ko
exactly matches what is already found in kernel 4.4.0-141-generic.
DKMS will not replace this module.
You may override by specifying --force.


depmod.....



DKMS: install completed.[SIZE=4]   
```
[/SIZE]

---

### Post by jeremy31 on 2019-01-26
What does ```
grep [[:alnum:]] /sys/module/rtl8723be/parameters/*
```
show?

The results for the dkms commands looks good

---

### Post by alexandrosfa on 2019-01-26
```
 grep [[:alnum:]] /sys/module/rtl8723be/parameters/*/sys/module/rtl8723be/parameters/ant_sel:1
/sys/module/rtl8723be/parameters/debug:1
/sys/module/rtl8723be/parameters/disable_watchdog:N
/sys/module/rtl8723be/parameters/fwlps:N
/sys/module/rtl8723be/parameters/ips:N
/sys/module/rtl8723be/parameters/msi:N
/sys/module/rtl8723be/parameters/swenc:Y
/sys/module/rtl8723be/parameters/swlps:N 
```

---

### Post by jeremy31 on 2019-01-26
Do ```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be_options.conf
```
Reboot

---

### Post by alexandrosfa on 2019-01-26
Can you please explain why is that necessary?

---

### Post by jeremy31 on 2019-01-26
Your HP laptop likely only uses one antenna and if it wasn't working you likely need ant_sel=2, the other options remain unchanged from what you had

---

### Post by alexandrosfa on 2019-01-26
Thank you for the clarification. It works perfectly now. Should I still do that?

---

### Post by jeremy31 on 2019-01-26
If it works perfectly the way it is, I wouldn't make the change

---

### Post by alexandrosfa on 2019-01-26
So I leave everything as it is and it will survive kernel upgrades?

---

### Post by jeremy31 on 2019-01-26
Yes, that is what the dkms commands provided

---

### Post by alexandrosfa on 2019-01-26
[SIZE=4]**Thank you very much indeed! You were truly helpful!!!**[/SIZE]

---

