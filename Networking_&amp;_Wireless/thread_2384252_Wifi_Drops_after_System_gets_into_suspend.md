---
title: "Wifi Drops after System gets into suspend"
date: 2018-02-04
forum: Networking &amp; Wireless
---

### Post by edenah on 2018-02-04
hello
EVERY TIME my machine goes into suspend mode my wifi connection drops.
when i go into wifi settings it shows me "no wifi adapter found".
 i own an alienware 15 r2.


i tried using "sudo service network-manager restart" and it doesn't work.
also i have noticed that after my machine is suspended, when i "use sudo lshw -class network" my wifi adapter and its drivers do miss.

the network only returns when i restart the laptop. and its a bummer to restart it every time i leave it alone for 15 mins lol.

please help :)

---

### Post by ajgreeny on 2018-02-04
Here's a script, including all the details needed to save it and place it in your system which solved this problem for me.
God luck, and let us know if it works for you as well.
```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Save this script as: /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh
# then
#   - chmod +x /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh

# DESCRIPTION
#
#   Restarting the NetworkManager as a workaround for the following bug:
# 
#   &#8729; https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480


# 3 or 4 seconds delay is necessary apparently.  May be shorter or longer and needs to be
# tested.  But if no delay is implemented, nm-applet crashes.  Seams that we
# need to leave the system resume completely before attempting a restart of
# NetworkManager.
(sleep 4; systemctl restart NetworkManager.service) &
disown

```

---

### Post by edenah on 2018-02-05
> **ajgreeny said:**
> Here's a script, including all the details needed to save it and place it in your system which solved this problem for me.
God luck, and let us know if it works for you as well.
```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Save this script as: /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh
# then
#   - chmod +x /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh

# DESCRIPTION
#
#   Restarting the NetworkManager as a workaround for the following bug:
# 
#   &#8729; https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480


# 3 or 4 seconds delay is necessary apparently.  May be shorter or longer and needs to be
# tested.  But if no delay is implemented, nm-applet crashes.  Seams that we
# need to leave the system resume completely before attempting a restart of
# NetworkManager.
(sleep 4; systemctl restart NetworkManager.service) &
disown

```


Thanks for the try matei tried it and it didn't work though :(
i want to emphasize that "systemctl restart NetworkManager.service" was tried billion times and it has no effect on my computer. it even gives it bugs when i use this command while my computer's wifi works fine.
is there any log file i can produce for you guys?

---

### Post by edenah on 2018-02-08
nobody knows how to help?
i tried installing ubuntu 16 instead of 17 but it didn't work.
are there maybe some drivers that i can install?

---

### Post by wildmanne39 on 2018-02-08
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by edenah on 2018-02-11
[http://paste.ubuntu.com/=QBrtVZ947y/](http://paste.ubuntu.com/=QBrtVZ947y/)

---

### Post by wildmanne39 on 2018-02-11
After you suspend your computer and you do not have wifi connection please run:
```
lsmod
```
so we can see of your driver is loaded while your wifi connection is not working.

Thanks

---

### Post by edenah on 2018-02-12
> **wildmanne39 said:**
> After you suspend your computer and you do not have wifi connection please run:
```
lsmod
```
so we can see of your driver is loaded while your wifi connection is not working.

Thanks

Here you go:
```
lsmod
Module                  Size  Used by
ccm                    20480  0
rfcomm                 77824  2
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
nf_conntrack_ipv4      16384  5
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          131072  6 nf_conntrack_ipv4,ipt_MASQUERADE,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
libcrc32c              16384  2 nf_conntrack,nf_nat
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                143360  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
ebtable_filter         16384  0
ebtables               32768  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
snd_hda_codec_hdmi     49152  1
cmac                   16384  1
bnep                   20480  2
snd_hda_codec_ca0132    49152  1
arc4                   16384  0
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
snd_hda_intel          40960  6
intel_powerclamp       16384  0
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_ca0132
coretemp               16384  0
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_ca0132
kvm_intel             204800  0
snd_hwdep              20480  1 snd_hda_codec
kvm                   581632  1 kvm_intel
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_seq_midi           16384  0
crc32_pclmul           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           188416  2
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
ath10k_pci             45056  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               90112  0
ath10k_core           352256  1 ath10k_pci
intel_cstate           20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_vmalloc      16384  1 uvcvideo
ath                    28672  1 ath10k_core
intel_rapl_perf        16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_timer              32768  2 snd_seq,snd_pcm
videobuf2_v4l2         24576  1 uvcvideo
mac80211              778240  1 ath10k_core
dell_wmi               16384  0
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd                    81920  22 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_seq_device,snd_hda_codec_ca0132,snd_pcm
dell_smbios            16384  1 dell_wmi
joydev                 20480  0
input_leds             16384  0
rndis_host             16384  0
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
dcdbas                 16384  1 dell_smbios
cdc_ether              16384  1 rndis_host
serio_raw              16384  0
soundcore              16384  1 snd
sparse_keymap          16384  1 dell_wmi
media                  40960  2 uvcvideo,videodev
usbnet                 45056  2 rndis_host,cdc_ether
cfg80211              610304  3 mac80211,ath,ath10k_core
rtsx_pci_ms            20480  0
mii                    16384  1 usbnet
wmi_bmof               16384  0
memstick               16384  1 rtsx_pci_ms
btusb                  45056  0
btrtl                  16384  1 btusb
mei_me                 40960  0
hci_uart              106496  0
shpchp                 36864  0
mei                    98304  1 mei_me
processor_thermal_device    16384  0
btbcm                  16384  2 hci_uart,btusb
intel_pch_thermal      16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
serdev                 20480  1 hci_uart
int3403_thermal        16384  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
bluetooth             540672  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
intel_lpss_acpi        16384  0
acpi_als               16384  0
int3400_thermal        16384  0
kfifo_buf              16384  1 acpi_als
intel_lpss             16384  1 intel_lpss_acpi
acpi_thermal_rel       16384  1 int3400_thermal
mac_hid                16384  0
tpm_crb                16384  0
dell_rbtn              16384  0
industrialio           69632  2 acpi_als,kfifo_buf
acpi_pad              180224  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               40960  11 ipt_REJECT,iptable_mangle,ip_tables,ebtables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_CHECKSUM,ip6table_filter,xt_conntrack,ip6_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
nouveau              1638400  2
i915                 1798144  36
rtsx_pci_sdmmc         24576  0
mxm_wmi                16384  1 nouveau
ttm                    94208  1 nouveau
i2c_algo_bit           16384  2 nouveau,i915
drm_kms_helper        167936  2 nouveau,i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
psmouse               147456  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   356352  12 nouveau,i915,ttm,drm_kms_helper
ahci                   36864  3
alx                    45056  0
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
mdio                   16384  1 alx
libahci                32768  1 ahci
wmi                    24576  4 dell_wmi,wmi_bmof,mxm_wmi,nouveau
video                  40960  3 dell_wmi,nouveau,i915
i2c_hid                20480  0
pinctrl_sunrisepoint    28672  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
pinctrl_intel          20480  1 pinctrl_sunrisepoint
```

---

### Post by wildmanne39 on 2018-02-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Suspend your computer then try:
```
sudo su
echo 1 > /sys/bus/pci/rescan
```
Does your wifi resume now? If so we will need to write a small script.

---

### Post by edenah on 2018-02-13
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Suspend your computer then try:
```
sudo su
echo 1 > /sys/bus/pci/rescan
```
Does your wifi resume now? If so we will need to write a small script.



OMG IT WORKED! <3
How do i make a script out of it?
 i tried putting this script in the "[COLOR=#000000]/etc/pm/sleep.d" folder with the name "15_wifion":
[/COLOR]```
[COLOR=#000000]
[/COLOR][COLOR=#000000]#!/bin/bash
[/COLOR]
[COLOR=#000000]case "$1" in[/COLOR]
[COLOR=#000000]suspend | hibernate)[/COLOR]
[COLOR=#000000]# executed on suspend[/COLOR]
[COLOR=#000000];;[/COLOR]
[COLOR=#000000]resume | thaw) [/COLOR]
[COLOR=#000000]# executed on resume[/COLOR]
[COLOR=#000000]sudo su & [/COLOR][COLOR=#000000][FONT=&amp]echo 1 > /sys/bus/pci/rescan[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000];;[/COLOR]
[COLOR=#000000]*)[/COLOR]
[COLOR=#000000];;[/COLOR]
[COLOR=#000000]esac
[/COLOR]
```[COLOR=#000000]

what have i done wrong?[/COLOR]

---

### Post by wildmanne39 on 2018-02-13
Please do:
```
sudo -H gedit /lib/systemd/system-sleep/wpasupplicant

```
The file will open and change the file to read:
```
#!/bin/sh
set -e

if [ "$2" = "suspend" ] || [ "$2" = "hybrid-sleep" ]; then
case "$1" in
#pre) /sbin/wpa_cli suspend ;;
#post) /sbin/wpa_cli resume ;;
post) echo 1 > /sys/bus/pci/rescan ;;
esac
fi

```
save gedit, close and reboot, let us know if that works if not we may have to rename the file.

Thanks

---

### Post by edenah on 2018-02-13
I LOVE YOU MAN! :D
it works! 
Thank you so much! :)

---

### Post by wildmanne39 on 2018-02-13
Your welcome, glad it worked, please use thread tools at the top of the page to mark the thread solved.

Enjoy!

---

