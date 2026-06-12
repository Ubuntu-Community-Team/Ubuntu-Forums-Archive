---
title: "I can't connect to the internet"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by Ruiizu1990 on 2017-10-22
Hi
I'm using Ubuntu Mate and a tp-link tl-wn722n wireless adapter. 

There is no connection at all. 

I can't use the sudo apt command to get additional packages because I'm offline. I am only able to post this message via dual boot Windows 10, otherwise I would have no access to the internet.

Is there any way to fix this? I'm desperate to dump Windows 10 for good.

---

### Post by wondringaloud on 2017-10-22
Did you just upgrade to 17.10? 
[https://ubuntuforums.org/showthread.php?t=2374857&page=2&p=13700631#post13700631](https://ubuntuforums.org/showthread.php?t=2374857&page=2&p=13700631#post13700631)

sudo dpkg-reconfigure resolvconf

Say yes to "prepare /etc/resolve.conf for dynamic updates?"

sudo reboot

---

### Post by Ruiizu1990 on 2017-10-23
No, it was a fresh install.

I tried the fix but no difference, network is still not appearing :(

---

### Post by wildmanne39 on 2017-10-23
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Ruiizu1990 on 2017-10-23
```
 louise1990@louise1990-B150M-DS3H:~$ cat /etc/lsb-release; uname -a
 DISTRIB_ID=Ubuntu
 DISTRIB_RELEASE=17.04
 DISTRIB_CODENAME=zesty
 DISTRIB_DESCRIPTION="Ubuntu 17.04"
 Linux louise1990-B150M-DS3H 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
 louise1990@louise1990-B150M-DS3H:~$ lspci -nnk | grep -iA2 net
 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
     Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
     Kernel driver in use: r8169
     Kernel modules: r8169
 louise1990@louise1990-B150M-DS3H:~$ lsusb
 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 006: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
 Bus 001 Device 005: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
 Bus 001 Device 004: ID 17ef:6054 Lenovo  
 Bus 001 Device 003: ID 2357:010c   
 Bus 001 Device 002: ID 0951:1665 Kingston Technology Digital DataTraveler SE9 64GB
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 louise1990@louise1990-B150M-DS3H:~$ iwconfig
 enp2s0    no wireless extensions.
 

 lo        no wireless extensions.
 

 louise1990@louise1990-B150M-DS3H:~$ rfkill list all
 louise1990@louise1990-B150M-DS3H:~$ lsmod
 Module                  Size  Used by
 bnep                   20480  2
 nls_iso8859_1          16384  2
 snd_hda_codec_hdmi     49152  1
 joydev                 20480  0
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
 pcbc                   16384  0
 aesni_intel           167936  0
 aes_x86_64             20480  1 aesni_intel
 snd_hda_codec_realtek    90112  1
 crypto_simd            16384  1 aesni_intel
 glue_helper            16384  1 aesni_intel
 snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
 cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
 intel_cstate           20480  0
 intel_rapl_perf        16384  0
 snd_hda_intel          36864  5
 snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
 snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
 snd_hwdep              16384  1 snd_hda_codec
 snd_seq_midi           16384  0
 snd_seq_midi_event     16384  1 snd_seq_midi
 snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
 snd_rawmidi            32768  1 snd_seq_midi
 snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              32768  2 snd_seq,snd_pcm
 snd                    77824  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
 hci_uart               98304  0
 btbcm                  16384  1 hci_uart
 btqca                  16384  1 hci_uart
 btintel                16384  1 hci_uart
 bluetooth             557056  11 hci_uart,btintel,btqca,bnep,btbcm
 intel_lpss_acpi        16384  0
 intel_lpss             16384  1 intel_lpss_acpi
 mei_me                 40960  0
 mei                   102400  1 mei_me
 shpchp                 36864  0
 soundcore              16384  1 snd
 tpm_infineon           20480  0
 mac_hid                16384  0
 acpi_als               16384  0
 kfifo_buf              16384  1 acpi_als
 industrialio           69632  2 acpi_als,kfifo_buf
 acpi_pad              180224  0
 parport_pc             32768  1
 ppdev                  20480  0
 lp                     20480  0
 parport                49152  3 lp,parport_pc,ppdev
 ip_tables              24576  0
 x_tables               36864  1 ip_tables
 autofs4                40960  2
 hid_generic            16384  0
 usbhid                 53248  0
 uas                    24576  0
 usb_storage            69632  2 uas
 nouveau              1601536  2
 mxm_wmi                16384  1 nouveau
 i2c_algo_bit           16384  1 nouveau
 ttm                    98304  1 nouveau
 drm_kms_helper        151552  1 nouveau
 syscopyarea            16384  1 drm_kms_helper
 sysfillrect            16384  1 drm_kms_helper
 sysimgblt              16384  1 drm_kms_helper
 fb_sys_fops            16384  1 drm_kms_helper
 drm                   352256  5 nouveau,ttm,drm_kms_helper
 r8169                  81920  0
 ahci                   36864  2
 mii                    16384  1 r8169
 libahci                32768  1 ahci
 wmi                    16384  2 mxm_wmi,nouveau
 video                  40960  1 nouveau
 pinctrl_sunrisepoint    28672  0
 i2c_hid                20480  0
 pinctrl_intel          20480  1 pinctrl_sunrisepoint
 hid                   114688  3 i2c_hid,hid_generic,usbhid
 fjes                   73728  0
 louise1990@louise1990-B150M-DS3H:~$ 
 
```

---

### Post by Ruiizu1990 on 2017-10-24
Any thoughts? I'm desperate to get online :(

---

### Post by wildmanne39 on 2017-10-24
Can you get online with a wired connection or tether your cell phone to your computer? if so please click on the link in my signature and follow the directions for running the wireless script and pasting the pastbin link here.

Thanks

---

### Post by Ruiizu1990 on 2017-10-24
> **wildmanne39 said:**
> Can you get online with a wired connection or tether your cell phone to your computer? if so please click on the link in my signature and follow the directions for running the wireless script and pasting the pastbin link here.

Thanks

I can't do either of those things. My ISP doesn't support tethering, and wired is not possible.

---

### Post by wildmanne39 on 2017-10-24
Unless your ISP is your cell phone provider they do not have anything to do with you tethering your cell phone to your computer through an usb port.

---

### Post by Ruiizu1990 on 2017-10-24
OK, I assumed it did. I will give it a go and get back to you.

---

