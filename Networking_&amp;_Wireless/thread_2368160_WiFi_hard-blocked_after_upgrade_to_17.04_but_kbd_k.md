---
title: "WiFi hard-blocked after upgrade to 17.04 but kbd key is ignored"
date: 2017-08-07
forum: Networking &amp; Wireless
---

### Post by teledyn on 2017-08-07
There have been several posts here and on StackExchange with issues of soft-blocked wifi after an upgrade, but I've been unable to find a solution for a hard-blocked interface. This is using Network controller Intel Centrino Wireless-N 1030 [Rainbow Peak] (rev 34) which has been in use on this laptop without issue since perhaps Ubuntu 12.04, but on upgrading from 16.10 to 17.04 the WiFi vanished.

#ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

pressing the radio-toggle key on the keyboard (on this zareason strata laptop it is Fn-F2):
Aug  7 18:10:59 strata kernel: [ 1510.585649] atkbd serio0: Unknown key pressed (translated set 2, code 0x84 on isa0060/serio0).
Aug  7 18:10:59 strata kernel: [ 1510.585656] atkbd serio0: Use 'setkeycodes e004 <keycode>' to make it known.
Aug  7 18:10:59 strata kernel: [ 1510.585649] atkbd serio0: Unknown key pressed (translated set 2, code 0x84 on isa0060/serio0).
Aug  7 18:10:59 strata kernel: [ 1510.585656] atkbd serio0: Use 'setkeycodes e004 <keycode>' to make it known.
Aug  7 18:10:59 strata kernel: [ 1510.600611] atkbd serio0: Unknown key released (translated set 2, code 0x84 on isa0060/serio0).
Aug  7 18:10:59 strata kernel: [ 1510.600619] atkbd serio0: Use 'setkeycodes e004 <keycode>' to make it known.
Aug  7 18:10:59 strata kernel: [ 1510.600611] atkbd serio0: Unknown key released (translated set 2, code 0x84 on isa0060/serio0).
Aug  7 18:10:59 strata kernel: [ 1510.600619] atkbd serio0: Use 'setkeycodes e004 <keycode>' to make it known.

The gnome-shell key configuration does not include the radio toggle as a button option, likely because it is a hardware switch.  The BIOS shows WiFi enabled.  I tried sudo setkeycodes e004 0x84 not knowing at all what it might do, but it does nothing.  rfkill unblock does nothing to a hard-blocked device.

Is it possible to have Ubuntu recognize the hardware radio toggle?  Is there any way to simulate it?

---

### Post by chili555 on 2017-08-08
There may be a better way. Please run and post:```
rfkill list all
lsmod
```

---

### Post by teledyn on 2017-08-20
rfkill list all doesn't tell us anything we don't already know ;) and the rfkill unblock commands are useless against hard-block (this is also reported in the other posts)

```
 phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

removing the bluetooth usb device doesn't change anything.  lsmod follows, but considering this laptop has been in continuous use with wifi support for many years, and considering the WiFi-enable hardware key is the only Fn key that is unknown and that this situation is new in 17.04, I'm not sure how we might narrow down the module involved.  The absense of the enable-key (and the kernel reporting that this issue is hardware-blocking) maybe suggests it is the keyboard drivers?

```
$ lsmod
Module                  Size  Used by
nls_utf8               16384  1
isofs                  40960  1
ums_realtek            20480  0
uas                    24576  0
usb_storage            69632  2 uas,ums_realtek
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                  102400  0
msdos                  20480  0
jfs                   184320  0
xfs                  1191936  0
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
libcrc32c              16384  2 xfs,nf_nat
nf_conntrack_ipv4      16384  5
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          131072  6 nf_conntrack_ipv4,ipt_MASQUERADE,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                139264  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
snd_hrtimer            16384  1
rfcomm                 77824  4
cmac                   16384  1
bnep                   20480  2
dm_crypt               28672  1
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             557056  33 btrtl,btintel,bnep,btbcm,rfcomm,btusb
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
arc4                   16384  2
iwldvm                233472  0
snd_hda_codec_hdmi     49152  4
mac80211              782336  1 iwldvm
input_leds             16384  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
joydev                 20480  0
snd_hda_codec_realtek    90112  1
serio_raw              16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
iwlwifi               229376  1 iwldvm
mac_hid                16384  0
cfg80211              602112  3 iwlwifi,mac80211,iwldvm
mei_me                 40960  0
snd_hda_intel          36864  6
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  5 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
mei                   102400  1 mei_me
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  3 snd_seq,snd_hrtimer,snd_pcm
snd                    77824  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
lpc_ich                24576  0
soundcore              16384  1 snd
shpchp                 36864  0
tpm_infineon           20480  0
nvidia_uvm            647168  0
binfmt_misc            20480  1
cuse                   16384  3
parport_pc             32768  0
sunrpc                335872  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               36864  11 ipt_REJECT,iptable_mangle,ip_tables,ebtables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_CHECKSUM,ip6table_filter,xt_conntrack,ip6_tables
autofs4                40960  2
btrfs                1093632  0
xor                    24576  1 btrfs
raid6_pq              114688  1 btrfs
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
nvidia_drm             45056  1
nvidia_modeset        790528  5 nvidia_drm
nvidia              12304384  92 nvidia_modeset,nvidia_uvm
drm_kms_helper        151552  1 nvidia_drm
psmouse               139264  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ahci                   36864  3
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   352256  4 nvidia_drm,drm_kms_helper
r8169                  81920  0
mii                    16384  1 r8169
fjes                   73728  0
video                  40960  0
```

---

### Post by teledyn on 2017-08-20
rfkill list all doesn't tell us anything we don't already know ;) and the rfkill unblock commands are useless against hard-block (this is also reported in the other posts)

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

removing the bluetooth usb device doesn't change anything.  lsmod follows, but considering this laptop has been in continuous use with wifi support for many years, and considering the WiFi-enable hardware key is the only Fn key that is unknown and that this situation is new in 17.04, I'm not sure how we might narrow down the module involved.  The absense of the enable-key (and the kernel reporting that this issue is hardware-blocking) maybe suggests it is the keyboard drivers?

$ lsmod
Module                  Size  Used by
nls_utf8               16384  1
isofs                  40960  1
ums_realtek            20480  0
uas                    24576  0
usb_storage            69632  2 uas,ums_realtek
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                  102400  0
msdos                  20480  0
jfs                   184320  0
xfs                  1191936  0
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
libcrc32c              16384  2 xfs,nf_nat
nf_conntrack_ipv4      16384  5
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          131072  6 nf_conntrack_ipv4,ipt_MASQUERADE,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                139264  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
snd_hrtimer            16384  1
rfcomm                 77824  4
cmac                   16384  1
bnep                   20480  2
dm_crypt               28672  1
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             557056  33 btrtl,btintel,bnep,btbcm,rfcomm,btusb
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
arc4                   16384  2
iwldvm                233472  0
snd_hda_codec_hdmi     49152  4
mac80211              782336  1 iwldvm
input_leds             16384  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
joydev                 20480  0
snd_hda_codec_realtek    90112  1
serio_raw              16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
iwlwifi               229376  1 iwldvm
mac_hid                16384  0
cfg80211              602112  3 iwlwifi,mac80211,iwldvm
mei_me                 40960  0
snd_hda_intel          36864  6
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  5 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
mei                   102400  1 mei_me
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  3 snd_seq,snd_hrtimer,snd_pcm
snd                    77824  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
lpc_ich                24576  0
soundcore              16384  1 snd
shpchp                 36864  0
tpm_infineon           20480  0
nvidia_uvm            647168  0
binfmt_misc            20480  1
cuse                   16384  3
parport_pc             32768  0
sunrpc                335872  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               36864  11 ipt_REJECT,iptable_mangle,ip_tables,ebtables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_CHECKSUM,ip6table_filter,xt_conntrack,ip6_tables
autofs4                40960  2
btrfs                1093632  0
xor                    24576  1 btrfs
raid6_pq              114688  1 btrfs
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
nvidia_drm             45056  1
nvidia_modeset        790528  5 nvidia_drm
nvidia              12304384  92 nvidia_modeset,nvidia_uvm
drm_kms_helper        151552  1 nvidia_drm
psmouse               139264  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ahci                   36864  3
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   352256  4 nvidia_drm,drm_kms_helper
r8169                  81920  0
mii                    16384  1 r8169
fjes                   73728  0
video                  40960  0

---

### Post by teledyn on 2017-08-20
checking in a console window with Ctrl-Alt-F1 confirms that the kernel is not seeing this key, so it isn't xwindows and probably isn't specifically WiFi, but somehow the Linux kernel has lost the ability to {handle, passthru} the hardware WiFi toggle?  Or maybe more likely is that the linux kernel is believing the toggle to be set regardless how it is toggled?  That seems more likely as I would have had no reason to toggle the setting myself before any upgrade.

the situation persists regardless whether I use Gnome or Unity on 17.04, and also occurs using Gnome 16.04 (I don't yet have a unity 16.04 live CD to test but will do that later today)

---

### Post by jeremy31 on 2017-08-20
So what model computer is this?  Have you gone into BIOS and tried resetting to defaults?
Please use code tags on terminal output, see the link in my signature for details

---

### Post by teledyn on 2017-08-20
Thanks for helping out on this.  I have a ZaReason 'Strata' laptop, which probably doesn't help you much but ZaReason.com machines were designed for Linux, and this situation is new with Ubuntu 17.04 or possibly 16.04 in gnome-shell only. The hardware has been running Ubuntu since about 12.04

I checked the bios, WiFi is enabled and to be certain I disabled and re-enabled and still no change -- I have seen in other reports of the same symptom that Windows will work fine, but I do not have a Windows to test with so cannot say.  I noticed just now though, testing by inserting a USB Wifi dongle (Belkin N150) that the WiFi is still considered hardware blocked, only now it actually says in the Gnome shell status menu that it is blocked and to use hardware enable, and I further noticed that the Airplane Mode icon was now visible on the status line.  If, however, I removed the Bluetooth USB, the WiFi remains hard blocked, and an airplane icon comes on again, but if I remove the bluetooth, still no wifi but airplane icon vanishes.

---

### Post by jeremy31 on 2017-08-20
Did wireless work in Ubuntu 14.04?  It might be worth trying 14.04 or 14.04.1 and see if it works with the 3.13 kernel.  If nothing else you may have to remove the wireless card and use a small piece of electrical tape on 1 of the pins 
Video at [https://www.youtube.com/watch?v=yzAKcmlaH1M](https://www.youtube.com/watch?v=yzAKcmlaH1M)

These things aren't easy to track down as it normally is something in the BIOS or a vendor specific module that gets changed

---

### Post by chili555 on 2017-08-20
I notice there is no *-wmi or *-acpi or *-laptop module loaded. They are the usual helper modules that translate key presses, in your case Fn+F2 into action; namely, turn on the wireless please. Jeremy and I are interested to see if another Ubuntu version loads some such thing.

An example from my machine:```
<snip>
snd_hda_codec_realtek    90112  1
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
nvram                  16384  1 [COLOR="#FF0000"]thinkpad_acpi[/COLOR]
btintel                16384  1 btusb
memstick               16384  1 rtsx_pci_ms
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
<snip>
```Of course, yours is not a Thinkpad, so we must try to identify the missing module.

---

### Post by teledyn on 2017-08-21
I think we may be on a wild goose chase here: using the 14.04 live CD gives the same result now, and that leads me to believe it is a hardware error, perhaps my WiFi chip simply gave up -- I disabled WiFi in the bios and now find I can use a USB dongle no problems, and also curious, while I had never used BT before, when I recently got BT speakers to use, I found the bluetooth would not turn on, so I had assumed it didn't have any and used a USB, but there in the bios was also a switch for BT, active, yet none were detected.  So is it likely the two services are on the same wireless chip and that chip is now toast?

---

### Post by praseodym on 2017-08-21
Checked a BIOS reset to default setting?

---

### Post by chili555 on 2017-08-21
> So is it likely the two services are on the same wireless chip and that chip is now toast?My strong suspicion is yes and yes.

---

