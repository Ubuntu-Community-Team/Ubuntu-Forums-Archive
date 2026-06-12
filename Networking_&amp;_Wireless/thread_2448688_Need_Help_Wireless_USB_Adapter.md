---
title: "Need Help Wireless USB Adapter"
date: 2020-08-12
forum: Networking &amp; Wireless
---

### Post by xmodx2 on 2020-08-12
Hello,

  i just installed Ubuntu 20.04 and i cant make my USB Adapter to work the device model name is:  TOTO-LINK N300RH 

[https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.dscomputer.co.id%2Fupload%2FN300RH_Photo001_20141020125846.jpg&f=1&nofb=1](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.dscomputer.co.id%2Fupload%2FN300RH_Photo001_20141020125846.jpg&f=1&nofb=1)

please help. thanks in advance

[https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.6tJNQ4iWNY7uysSwwn8KbgHaHa%26pid%3DApi&f=1](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.6tJNQ4iWNY7uysSwwn8KbgHaHa%26pid%3DApi&f=1)

---

### Post by coffeecat on 2020-08-12
*Thread moved to **Networking & Wireless**.*

@xmodx2, I've reduced your oversized images to hyperlinks. Please be mindful of those using mobile devices and avoid the use of large images. If you need to include images in a post, instead of using off-site image hosting, please upload images to the forum using the paperclip icon in the advanced message editor. That way you get clickable thumbnails.

That being said, the images you provided were for your router. You state that your problem is getting your Wireless USB Adaptor to work, which is a very different thing. Have a read through the sticky at the top of this sub-forum - [here](https://ubuntuforums.org/showthread.php?t=370108) - and post your wireless-info.txt file. Make sure the USB device is plugged in when you run the script. Without that information no one will be able to help.

---

### Post by xmodx2 on 2020-08-12
Thank you so much Sir for the help and modify my post,

here is my pastebin result of wireless-info.txt file.
[https://pastebin.com/pKdi5FxQ](https://pastebin.com/pKdi5FxQ)

---

### Post by CelticWarrior on 2020-08-12
With an alternative internet connection (Ethernet, USB tethering, ...), please try:

```
sudo apt update
sudo apt full-upgrade
sudo apt install rtl8812au-dkms
```

---

### Post by xmodx2 on 2020-08-12
Thanks for the reply, i did this steps and here is the result:
**rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu12).**

> **CelticWarrior said:**
> With an alternative internet connection (Ethernet, USB tethering, ...), please try:

```
sudo apt update
sudo apt full-upgrade
sudo apt install rtl8812au-dkms
```

---

### Post by CelticWarrior on 2020-08-12
If already installed then you may need to disable Secure Boot in UEFI as this settings prevents certain drivers to load.

---

### Post by xmodx2 on 2020-08-12
> **CelticWarrior said:**
> If already installed then you may need to disable Secure Boot in UEFI as this settings prevents certain drivers to load.

sorry for newbie question but where do i exactly disable this?

---

### Post by CelticWarrior on 2020-08-12
At UEFI ("BIOS").

---

### Post by xmodx2 on 2020-08-12
attached images on my BIOS

---

### Post by xmodx2 on 2020-08-12
another 2 screens


[https://ibb.co/njdmKGQ](https://ibb.co/njdmKGQ)

---

### Post by chili555 on 2020-08-12
> **CelticWarrior said:**
> If already installed then you may need to disable Secure Boot in UEFI as this settings prevents certain drivers to load.Please see the paste:

> ##### secure boot #######################
 
SecureBoot disabled
Platform is in Setup Mode
Please let us see:

```
sudo modprobe 8812au
dmesg | grep -i -e rtl -e 8812
modinfo 8812au | grep 8812

```

---

### Post by xmodx2 on 2020-08-12
> **chili555 said:**
> Please see the paste:

Please let us see:

```
sudo modprobe 8812au
dmesg | grep -i -e rtl -e 8812
modinfo 8812au | grep 8812

```

gee@tux:~$ sudo modprobe 8812au _**(no results)**_
gee@tux:~$ dmesg | grep -i -e rtl -e 8812
```
[    0.619065] r8169 0000:06:00.0 eth0: RTL8168g/8111g, e0:d5:5e:48:c4:bd, XID 4c0, IRQ 52
[    2.316353] usb 1-9: New USB device found, idVendor=0bda, idProduct=8812, bcdDevice= 0.00
[    9.209451] 8812au: loading out-of-tree module taints kernel.
[    9.209832] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[    9.214478] RTL871X: module init start
[    9.214479] RTL871X: rtl8812au v4.3.8_12175.20140902
[    9.214480] RTL871X: build time: Jul 25 2020 21:24:25
[    9.214551] Modules linked in: 8812au(OE+) btusb btrtl btbcm btintel cfg80211 bluetooth crct10dif_pclmul ecdh_generic ecc uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 input_leds videobuf2_common videodev snd_usb_audio(+) ghash_clmulni_intel snd_usbmidi_lib mc amdgpu(+) aesni_intel snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep snd_pcm crypto_simd cryptd snd_seq_midi amd_iommu_v2 snd_seq_midi_event gpu_sched snd_rawmidi ttm glue_helper drm_kms_helper snd_seq i2c_algo_bit snd_seq_device snd_timer fb_sys_fops syscopyarea snd k10temp sysfillrect sysimgblt soundcore wmi_bmof mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_jabra hid_generic usbhid hid uas usb_storage crc32_pclmul r8169 i2c_piix4 realtek ahci libahci wmi video gpio_amdpt gpio_generic
[    9.214608]  ? _rtw_malloc+0x2d/0x2f [8812au]
[    9.214623]  ? _rtw_memcpy+0x10/0x12 [8812au]
[    9.214639]  ? rtw_5g_rates_init+0x1a/0x1c [8812au]
[    9.214654]  ? rtw_spt_band_alloc+0xb0/0xb2 [8812au]
[    9.214668]  rtw_wdev_alloc+0xf6/0x29c [8812au]
[    9.214683]  rtw_usb_if1_init+0xf0/0x20c [8812au]
[    9.214696]  rtw_drv_init+0x246/0x2d3 [8812au]
[    9.214721]  rtw_drv_entry+0x65/0x1000 [8812au]
[    9.640602] usbcore: registered new interface driver rtl8812au
[    9.640604] RTL871X: module init ret=0
```
gee@tux:~$ modinfo 8812au | grep 8812
```
filename:       /lib/modules/5.4.0-42-generic/updates/dkms/8812au.ko
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
name:           8812au

```

---

### Post by chili555 on 2020-08-12
Let's try a newer driver. First, unplug the device. Next:

```
sudo apt purge rtl8812au-dkms
sudo apt install git
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
sudo modprobe 88XXau
```

Plug in the device. Any improvement?

---

### Post by xmodx2 on 2020-08-12
> **chili555 said:**
> Let's try a newer driver. First, unplug the device. Next:

```
sudo apt purge rtl8812au-dkms
sudo apt install git
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
sudo modprobe 88XXau
```

Plug in the device. Any improvement?



thank you, it is now working....   


Question: when doing updates on system would this get affected?

---

### Post by chili555 on 2020-08-12
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

> Question: when doing updates on system would this get affected?Probably not. That's the wonderful thing about dkms.

> DESCRIPTION
       dkms is a framework which allows kernel modules to be dynamically built
       for each kernel on your system in a simplified and organized fashion.

---

