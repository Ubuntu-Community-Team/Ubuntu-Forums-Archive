---
title: "TP-Link ACWirel;ess Dual Band USB Adapter"
date: 2017-04-20
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2017-04-20
I have this wireless adapter whicj is compatible with Linux.  I downloaded the driver install program and here is how to do the setup.

```
#prepareUbuntu: sudo apt-get install git build-essential


# how to use
```
$ mkdir ~/src
$ cd ~/src
$ git clone https://github.com/Myria-de/mt7610u_wifi_sta_v3002_dpo_20130916.git
$ make
$ make install
$ cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
$ reboot
```
refer to&#65306;
http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/
On this page you'll find also details about configuration in RT2870STA.dat.


https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916 (TP-Link T2U)



```

My problem occurs when I get to make install.  The following code is what I get.  Could someone please tell me what I'm doing wrong?

```
frank@frank-110-194:~/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master$ make installmake -C /home/frank/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/frank/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master/os/linux'
mkdir: cannot create directory ‘/etc/Wireless’: Permission denied
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
mkdir: cannot create directory ‘/etc/Wireless/RT2870STA’: No such file or directory
Makefile.6:454: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/frank/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master/os/linux'
Makefile:501: recipe for target 'install' failed
make: *** [install] Error 2
frank@frank-110-194:~/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master$ make install
make -C /home/frank/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/frank/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master/os/linux'
mkdir: cannot create directory ‘/etc/Wireless’: Permission denied
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
mkdir: cannot create directory ‘/etc/Wireless/RT2870STA’: No such file or directory
Makefile.6:454: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/frank/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916-master/os/linux'
Makefile:501: recipe for target 'install' failed
make: *** [install] Error 2
```

---

### Post by SeijiSensei on 2017-04-20
You can't create directories outside of your home and /tmp.  Everywhere else you must use sudo.  That's especially true when installing software from source.

Try running "sudo make install" and see if that's enough to fix the problem.

---

### Post by shane_faulkinbury2 on 2017-04-20
sudoi does the trick, but I get the same error 2 in booth src and mt7610u_wifi_sta_v3002_dpo_20130916-master.

---

### Post by wildmanne39 on 2017-04-20
Are you sure that is the correct driver? please post the output of:
> lsusb
lsmod
Thanks

---

### Post by shane_faulkinbury2 on 2017-04-21
I'll do those when I get home, I'm at work right now.

When I run the lusb command this is what I get.

```
o command 'lsub' found, did you mean: Command 'lsusb' from package 'usbutils' (main)

```

I try to install usbutils and my terminal says it's already installed.  So I try to ruin that and it tells me "usbutils: command not found".

This is what lsmod gives me.

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
usbutils is already the newest version (1:007-4).
The following packages were automatically installed and are no longer required:
  python3-pyqt4 python3-sip
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
frank@frank-110-194:~$ usbutils
usbutils: command not found
frank@frank-110-194:~$ lsmod
Module                  Size  Used by
binfmt_misc            20480  1
hid_generic            16384  0
uas                    24576  0
usb_storage            73728  1 uas
xt_recent              20480  0
nls_iso8859_1          16384  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
joydev                 20480  0
input_leds             16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  3
snd_hda_codec         135168  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  3 snd_hda_intel,snd_hda_codec,snd_hda_core
serio_raw              16384  0
intel_cstate           16384  0
intel_rapl_perf        16384  0
shpchp                 36864  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
ie31200_edac           16384  0
snd                    86016  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
edac_core              53248  1 ie31200_edac
mac_hid                16384  0
mei_me                 40960  0
lpc_ich                24576  0
mei                   102400  1 mei_me
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          110592  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  14 xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,xt_limit,ip6t_REJECT,xt_recent,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
hid_logitech_hidpp     28672  0
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
hid_logitech_dj        20480  0
usbhid                 53248  0
hid                   122880  6 hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
i915                 1310720  140
i2c_algo_bit           16384  1 i915
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
drm_kms_helper        167936  1 i915
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               139264  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 i915,drm_kms_helper
r8169                  81920  0
ahci                   36864  3
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    16384  1 hp_wmi
fjes                   28672  0
video                  40960  1 i915



```

Here you go.

```
frank@frank-110-194:~$ lsmodModule                  Size  Used by
binfmt_misc            20480  1
hid_generic            16384  0
uas                    24576  0
usb_storage            73728  1 uas
xt_recent              20480  0
nls_iso8859_1          16384  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
joydev                 20480  0
input_leds             16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  3
snd_hda_codec         135168  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  3 snd_hda_intel,snd_hda_codec,snd_hda_core
serio_raw              16384  0
intel_cstate           16384  0
intel_rapl_perf        16384  0
shpchp                 36864  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
ie31200_edac           16384  0
snd                    86016  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
edac_core              53248  1 ie31200_edac
mac_hid                16384  0
mei_me                 40960  0
lpc_ich                24576  0
mei                   102400  1 mei_me
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          110592  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  14 xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,xt_limit,ip6t_REJECT,xt_recent,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
hid_logitech_hidpp     28672  0
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
hid_logitech_dj        20480  0
usbhid                 53248  0
hid                   122880  6 hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
i915                 1310720  140
i2c_algo_bit           16384  1 i915
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
drm_kms_helper        167936  1 i915
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               139264  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 i915,drm_kms_helper
r8169                  81920  0
ahci                   36864  3
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    16384  1 hp_wmi
fjes                   28672  0
video                  40960  1 i915
frank@frank-110-194:~$ lsusb
Bus 002 Device 006: ID 1050:0116 Yubico.com Yubikey NEO(-N) OTP+U2F+CCID
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

Nevermind the above.  I had a typo and couldn't find delete post.

---

### Post by wildmanne39 on 2017-04-22
When you ran the command:
```
lsusb
```
did you have the usb wifi adapter plugged in because it did not show up? make sure it is plugged into the usb port and not a hub. Then run the command again please.
Thanks

---

### Post by shane_faulkinbury2 on 2017-04-22
Nope, but I'll be sure to plug it in the next I move my desktop down to the router!  Stupid wifi!!!  :)

Okay, I'm down here now and fired it up.  Here it is.

```

Bus 002 Device 004: ID 2357:0103  
Bus 002 Device 007: ID 1050:0116 Yubico.com Yubikey NEO(-N) OTP+U2F+CCID
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
frank@frank-110-194:~$ lsmod
Module                  Size  Used by
hid_generic            16384  0
uas                    24576  0
usb_storage            73728  1 uas
xt_recent              20480  0
nls_iso8859_1          16384  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  3
snd_hda_codec         135168  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
joydev                 20480  0
input_leds             16384  0
snd_hda_core           86016  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
irqbypass              16384  1 kvm
intel_cstate           16384  0
intel_rapl_perf        16384  0
serio_raw              16384  0
shpchp                 36864  0
snd_timer              32768  2 snd_seq,snd_pcm
snd                    86016  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
mei_me                 40960  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
lpc_ich                24576  0
ie31200_edac           16384  0
edac_core              53248  1 ie31200_edac
mac_hid                16384  0
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          110592  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  14 xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,xt_limit,ip6t_REJECT,xt_recent,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
hid_logitech_hidpp     28672  0
hid_logitech_dj        20480  0
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
usbhid                 53248  0
hid                   122880  6 hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
i915                 1310720  121
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
psmouse               139264  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
drm                   368640  6 i915,drm_kms_helper
libahci                32768  1 ahci
r8169                  81920  0
mii                    16384  1 r8169
wmi                    16384  1 hp_wmi
video                  40960  1 i915
fjes                   28672  0



```

The lsusb command had the same results!

---

### Post by wildmanne39 on 2017-04-22
If the command:
```
lsusb
```
does not show your usb adapter then their is no way to help you to get it working. Did you have your computer shutdown when you plugged in the adapter then turned it on?

How did you install 17.04? fresh install or an upgrade?
Thanks.

---

### Post by shane_faulkinbury2 on 2017-04-22
Yes

I was on Facebook and someone else was having a problem with TP-Link and someone on that post recommended this link.  [https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04](https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04)  Do you think that would work on 16.04.2?

---

### Post by wildmanne39 on 2017-04-22
> **shane_faulkinbury2 said:**
> I was on Facebook and someone else was having a problem with TP-Link and someone on that post recommended this link.  [https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04](https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04)  Do you think that would work on 16.04.2?
First nothing will work if your adapter does not show up with lsusb, and you said it did not, but you did not post the results the second time for us to see, also that info is old.

I asked about 3 questions in my last post and you just answered yes, please answer all questions, I have no idea what you answered yes too and post the output of that command for us to see please with the adapter plugged into an usb port not a hub.

Edit:

Never mind on the lsusb you did post it just not in the same post you talk about it.

Thanks

---

### Post by wildmanne39 on 2017-04-22
Please post the results of:
```
dpkg -l | grep linux-image
```
Thanks

---

### Post by shane_faulkinbury2 on 2017-04-23
It's about 9:30 am here and I'll see if I can get the desktop downstairs and run that command tonight.

I haven' tried it yet, but I heard this would work with the TP-Link AC1200.

```
[COLOR=#969896][FONT=SFMono-Regular]#[/FONT][/COLOR][COLOR=#969896][FONT=SFMono-Regular] sudo make -f Makefile.dkms install[/FONT][/COLOR]
```

---

### Post by wildmanne39 on 2017-04-23
Sure give it a shot, you sure are great at finding things to try.:)

---

### Post by shane_faulkinbury2 on 2017-04-23
Here's the dpkg -l grep | linux image.

```
frank@frank-110-194:~$ dpkg -l | grep linux-image
ii  linux-image-4.8.0-36-generic                4.8.0-36.36~16.04.1                           amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-46-generic                4.8.0-46.49~16.04.1                           amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-36-generic          4.8.0-36.36~16.04.1                           amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-46-generic          4.8.0-46.49~16.04.1                           amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-generic-hwe-16.04               4.8.0.46.18                                   amd64        Generic Linux kernel image

```

I'll try the other command in a bit.

Hmm, here's the other one.

```
        amd64        Generic Linux kernel image
frank@frank-110-194:~$ sudo make -f Makefile.dkms install
[sudo] password for frank: 
make: Makefile.dkms: No such file or directory
make: *** No rule to make target 'Makefile.dkms'.  Stop.
frank@frank-110-194:~$ 

```

---

### Post by wildmanne39 on 2017-04-23
That may be leading us toward a solution, please post the output from:
```
uname -a
```
Thanks

---

### Post by shane_faulkinbury2 on 2017-04-23
```
frank@frank-110-194:~$ uname -a
Linux frank-110-194 4.8.0-46-generic #49~16.04.1-Ubuntu SMP Fri Mar 31 14:51:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by shane_faulkinbury2 on 2017-04-26
Hmmm

---

### Post by wildmanne39 on 2017-04-26
I have no further suggestions, you need to understand as long as your adapter does not show up when you run the command:
```
lsusb
```
it does not matter if you install a driver or not wifi will not work and I really do not think the one you are trying to install is the right driver but we can not find that out because the adapter is not showing up which means either there is an issue with the port, the device is being seen as a storage device or it is defective.

---

### Post by shane_faulkinbury2 on 2017-04-27
I went and bought a new j5 Create Dual Band USB Adapter and it was just a plug and play.  I ran a lsusb with both adapters in and the Ralink is the new one, right?  So the other is defective?  What is this Bus 002 Device 007: ID 2357:0103 ?  There's no description.

```
frank@frank-110-194:~$ lsusb
Bus 002 Device 007: ID 2357:0103  
Bus 002 Device 006: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f9:02e9 Brother Industries, Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
frank@frank-110-194:~$ 

```

---

### Post by wildmanne39 on 2017-04-27
> Ralink is the new one
Yes this is the new one.
> What is this Bus 002 Device 007: ID 2357:0103
That is the one we were looking for I never saw it, it only showed up once and I was expecting a description, I have one and I was right it takes a different driver, but it does not work right with Ubuntu, I still get disconnected, so for now you are better off with the ralink. 

If you can I would return the TP-Link.

---

### Post by shane_faulkinbury2 on 2017-04-27
Will do and thank you for your help!  :P

---

### Post by wildmanne39 on 2017-04-27
Your welcome!

---

### Post by jeremy31 on 2017-04-27
I am not sure what the issue is with no description for the USB device as the 2357 should identify as TP-Link but it could be an issue at linux-usb.org.
I just sent an email to the maintainer

---

### Post by wildmanne39 on 2017-04-27
> **jeremy31 said:**
> I am not sure what the issue is with no description for the USB device as the 2357 should identify as TP-Link but it could be an issue at linux-usb.org.
I just sent an email to the maintainer
Thanks Jeremy31

---

