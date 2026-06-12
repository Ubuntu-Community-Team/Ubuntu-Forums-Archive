---
title: "Asus N-10 usb wireless driver not installing."
date: 2015-08-12
forum: Networking &amp; Wireless
---

### Post by avishek_arora on 2015-08-12
Hello everyone , 
i just brought a ASUS N-10 usb wireless device.  after plug it in it automatically showing me the wireless network around  the area but when i connect with the network after 10-15 minute the  connection break automatically but the icon show it is connected. i did  not installed any drivers first but when i tried to install then it  gives me this error message --

-- error message while running the install.sh script downloaded from asus website --

```
cc1: some warnings being treated as errors
scripts/Makefile.build:257:  recipe for target  '/home/avishek/Downloads/Linux/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o'  failed
make[2]: ***  [/home/avishek/Downloads/Linux/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o]  Error 1
Makefile:1394: recipe for target  '_module_/home/avishek/Downloads/Linux/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405'  failed
make[1]: ***  [_module_/home/avishek/Downloads/Linux/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405]  Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-25-generic'
Makefile:220: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
```

-

please  solve my problem as i'm a new user of ubuntu and i'm running ubuntu  15.04. i download the drivers from --  [https://www.asus.com/Networking/USBN10/HelpDesk_Download/](https://www.asus.com/Networking/USBN10/HelpDesk_Download/)
the download description says -- ASUS USB-N10 Driver 1.0.0.18 for Linux
Supported OS: Linux kernel 2.4/2.6
Driver updates for Windows and Linux.

---

### Post by chili555 on 2015-08-13
> Supported OS: Linux kernel 2.4/2.6However, you are using a much newer kernel:> [COLOR="#FF0000"]3.19[/COLOR].0-25-genericYou will not improve the performance of your device by installing this stale old antique!

Is the driver in use r8712u? Check:```
lsmod
```If so, let's have a look at some diagnostics:```
dmesg | grep 8712
iwconfig
```Thanks.

---

### Post by avishek_arora on 2015-08-15
but how to fix this problem. please help i have no idea ?

---

### Post by mörgæs on 2015-08-15
> **avishek_arora said:**
> please help i have no idea ?

But the poster above you has.
Please run the commands and post the output in CODE tags.

---

### Post by avishek_arora on 2015-08-15
alright --

The first command lsmod gives this output --

```
avishek@avishek-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1 
ctr                    16384  1 
ccm                    20480  1 
binfmt_misc            20480  1 
arc4                   16384  2 
rtl8192cu              69632  0 
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              724992  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              540672  2 mac80211,rtlwifi
snd_hda_codec_realtek    86016  1 
intel_powerclamp       20480  0 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          36864  3 
coretemp               16384  0 
i915                 1056768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
kvm_intel             151552  0 
snd_hwdep              20480  1 snd_hda_codec
kvm                   483328  1 kvm_intel
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
crct10dif_pclmul       16384  0 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
crc32_pclmul           16384  0 
video                  20480  1 i915
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
ghash_clmulni_intel    16384  0 
drm_kms_helper        126976  1 i915
aesni_intel           172032  2 
snd_timer              32768  2 snd_pcm,snd_seq
aes_x86_64             20480  1 aesni_intel
drm                   344064  5 i915,drm_kms_helper
gpio_ich               16384  0 
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd                    90112  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           16384  1 i915
soundcore              16384  2 snd,snd_hda_codec
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
shpchp                 40960  0 
8250_fintek            16384  0 
serio_raw              16384  0 
lpc_ich                24576  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
uas                    24576  0 
usb_storage            69632  2 uas
pata_acpi              16384  0 
r8169                  81920  0 
mii                    16384  1 r8169

```
and Second command dmesg | grep 8712
iwconfig gives this output --

```
avishek@avishek-desktop:~$ dmesg | grep 8712
avishek@avishek-desktop:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MilnetPrivate"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:6C:F5:27:6E:B6   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

eth1      no wireless extensions.

lo        no wireless extensions.
```

---

### Post by praseodym on 2015-08-15
>  rtl8192cu 69632 0 
Obviously, it is another chipset. Change the driver via LAN:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot and show
```

lsusb
```

---

### Post by chili555 on 2015-08-15
Ah! The notorious rtl8192cu! Please check here: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

---

### Post by praseodym on 2015-08-15
Hi chili555,

meanwhile it is driver version 1.10.

---

### Post by avishek_arora on 2015-08-15
okay praseodym i did what you said.. 
the following command gives this message --

```

avishek@avishek-desktop:~$ lsusb
Bus 002 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0000:0538  
Bus 001 Device 003: ID 0b05:17ba ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

---

### Post by praseodym on 2015-08-15
Ok, this chipset is not automatically supported. You need to add the device-ID:

```
echo 'install 8192cu modprobe --ignore-install 8192cu ; /bin/echo "0b05 17ba" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
```
Reboot

---

### Post by iamjiwjr on 2015-08-15
sudo apt-get install git build-essential linux-headers-generic dkms
git clone [https://github.com/dz0ny/rt8192cu.git](https://github.com/dz0ny/rt8192cu.git) --depth 1
cd rt8192cu
sudo make install

---

### Post by avishek_arora on 2015-08-15
well praseodym i followed your steps and it seems like problem is solved. the connection is stable now though i don't understand clearly why i have this problem in the first place. anyway thank you so much praseodym and everyone for your ultimate support. you guys are best.

---

