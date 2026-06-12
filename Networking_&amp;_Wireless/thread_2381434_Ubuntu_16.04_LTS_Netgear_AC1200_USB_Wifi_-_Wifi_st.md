---
title: "Ubuntu 16.04 LTS Netgear AC1200 USB Wifi - Wifi stops working after several minutes"
date: 2017-12-31
forum: Networking &amp; Wireless
---

### Post by stoudy on 2017-12-31
Recently decided to make an Ubuntu gaming box.  If this fails, I'm going to go back to Windows... SO please help me stay away from Windows LOL.

I installed a driver for my Netgear AC1200 USB wifi card following the instructions on [https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210).

That almost got my wifi working.  Then I had to edit the NetworkManager.conf to change managed to equal true.

This got my wifi card working.  I thought all was great until the wifi stopped working after a few minutes.  I did not get a wifi disconnected message.  Disabling wifi and restarting it does not work.  I have to reboot in order to get the wifi working again.  When I do so, it only works for a few minutes.

Please help... all of my Googling has been fruitless.

Wireless script info below:
[http://paste.ubuntu.com/26295190/](http://paste.ubuntu.com/26295190/)

Note... wifi not working even after a reboot now.

---

### Post by praseodym on 2018-01-01
Please show the outputs of
```

modprobe -c | grep -i "0846.*9053"
lsmod
dkms status
dmesg | grep taint
```

---

### Post by stoudy on 2018-01-02
A little has changed since my original post.  What I also did not mention was that I was having difficulty install the latest NVIDIA driver for my GPU.  While trying to fix that issue, I completely broke my wireless and had to reinstall Ubuntu.  When I reinstalled Ubuntu, I made sure it was connected to the internet and the NVIDIA driver download and installed correctly.  I was able to get the wireless to work again with similar, but not the same results.  Now, when I boot up, "Wifi Networks Device Not Managed" is displayed for the wifi status.  If I open a term and restart the network-manager service my wifi will work.  Sometimes it will work for several minutes.  Sometimes it will work for several hours.  I also get an error regarding modem manager crashing when I login.  I did manage to fix that error.... but when I did I broke wifi and had to reinstall Ubuntu to get everything working again.  Now I'm just ignoring the error.  Since my config has changed since the original post, I also ran the wireless script again.  Everything below is from before I restart the network manager service.  Thank you for your help!

[http://paste.ubuntu.com/26306592/](http://paste.ubuntu.com/26306592/)

konrad@konrad-All-Series:~$ modprobe -c | grep -i "0846.*9053"
alias usb:v0846p9053d*dc*dsc*dp*ic*isc*ip*in* mt7662u_sta

konrad@konrad-All-Series:~$ lsmod
Module                  Size  Used by
mt7662u_sta          1032192  0
cfg80211              602112  1 mt7662u_sta
joydev                 20480  0
input_leds             16384  0
hid_holtek_mouse       16384  0
snd_hda_codec_hdmi     49152  1
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   593920  0
nvidia_uvm            671744  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
snd_seq_midi           16384  0
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_seq_midi_event     16384  1 snd_seq_midi
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_rawmidi            32768  1 snd_seq_midi
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                24576  0
snd_timer              32768  2 snd_seq,snd_pcm
snd                    77824  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
mei_me                 40960  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
wmi                    16384  1 asus_wmi
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   118784  3 hid_generic,hid_holtek_mouse,usbhid
uas                    24576  0
usb_storage            69632  1 uas
nvidia_drm             45056  1
nvidia_modeset        843776  4 nvidia_drm
nvidia              13004800  180 nvidia_modeset,nvidia_uvm
drm_kms_helper        151552  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
drm                   352256  4 nvidia_drm,drm_kms_helper
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
fjes                   77824  0
video                  40960  1 asus_wmi

konrad@konrad-All-Series:~$ dkms status
bbswitch, 0.8, 4.10.0-28-generic, x86_64: installed
bbswitch, 0.8, 4.10.0-42-generic, x86_64: installed
nvidia-384, 384.90, 4.10.0-28-generic, x86_64: installed
nvidia-384, 384.90, 4.10.0-42-generic, x86_64: installed
nvidia-384, 384.90, 4.4.0-104-generic, x86_64: installed

konrad@konrad-All-Series:~$ dmesg | grep taint
[    0.868059] nvidia: loading out-of-tree module taints kernel.
[    0.868063] nvidia: module license 'NVIDIA' taints kernel.
[    0.868063] Disabling lock debugging due to kernel taint
[    0.871168] nvidia: module verification failed: signature and/or required key missing - tainting kernel

---

### Post by stoudy on 2018-01-04
Bump.  Still having this issue if anyone has time to assist.

---

### Post by praseodym on 2018-01-04
Lets check

```
dmesg | grep mt7662u_sta
```

---

