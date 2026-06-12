---
title: "Wifi/Bluetooth/Eth are not working on ubuntu 14.04 on HP-Envy-15t-notebook-laptop"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by rdhanunjayaraju on 2015-01-04
Hi,

I recently installed ubuntu 14.04 on my new HP Envy 15t notebook laptop. WiFi, Bluetooth and Ethernet modules not working on it.

WiFi:
- WiFi module is searching for wifi network, but not recognizing any networks that are near by.
- WiFi chip model: Broadcom BCM43142.

Bluetooth:
- Bluetooth module able to search near by devices and can pair with them (android phone). But after 5 seconds, the connection is disabling with out any reason.
- Bluetooth chip model: Broadcom BCM43142.

Ethernet:
- After connecting Ethernet cable to laptop, wired network connection is trying to establish connection for few seconds and then for no reason.
- Ping command is working on loop back network (ping 127.0.0.1). But not working on any other websites (ping [www.google.com](www.google.com))

I'm not able to use any network communication (WiFi/Bt/Eth) on my laptop to download patches or tools for this issue. Please suggest.

Thanks,
Dhanunjay

---

### Post by jeremy31 on 2015-01-04
Can you post the result of ```
lspci -nnk | grep -iA2 net
``` and ```
lsusb
```

---

### Post by praseodym on 2015-01-04
Please run the wireless script from the sticky thread and show the output.

---

### Post by rdhanunjayaraju on 2015-01-04
Here is the output of the commands jeremy:

$[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net[/FONT][/COLOR]01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2230]
	Kernel driver in use: bcma-pci-bridge
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:2290]
	Kernel driver in use: r8169
$lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 138a:0050 Validity Sensors, Inc. 
Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. 
Bus 001 Device 003: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Other commands output (FYI):

$ lsmod
Module                  Size  Used by
rfcomm                 69160  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
uvcvideo               80885  0 
btusb                  32412  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
bluetooth             391196  22 bnep,btusb,rfcomm
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
snd_hda_intel          52355  5 
crc32_pclmul           13113  0 
parport_pc             32701  0 
ghash_clmulni_intel    13216  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
aesni_intel            55624  0 
snd_hwdep              13602  1 snd_hda_codec
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
serio_raw              13462  0 
ppdev                  17671  0 
i915                  783805  5 
bcma                   52096  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
drm_kms_helper         53081  1 i915
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mei_me                 18627  0 
drm                   303102  4 i915,drm_kms_helper
mei                    82276  1 mei_me
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
hp_accel               26012  0 
lis3lv02d              20156  1 hp_accel
video                  19476  1 i915
input_polldev          13896  1 lis3lv02d
hp_wireless            12637  0 
mac_hid                13205  0 
wmi                    19177  1 hp_wmi
intel_smartconnect     12619  0 
ahci                   25819  4 
psmouse               106678  0 
r8169                  67581  0 
libahci                32560  1 ahci
mii                    13934  1 r8169




$ iwconfig 
eth0      no wireless extensions.


lo        no wireless extensions.


$ iwlist scanning
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Also attached dmesg output after system bootup. Thank you very much for your response Jeremy!

---

### Post by praseodym on 2015-01-04
Is it 32 or 64 bit?

---

### Post by jeremy31 on 2015-01-04
Please run the wireless-script from the sticky post [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Is this a dual boot with win 8?

---

### Post by rdhanunjayaraju on 2015-01-04
@jeremy: Yes, its a dual boot with win8.1

@[COLOR=#000000]praseodym: Its a 64 bit laptop.[/COLOR]

---

### Post by rdhanunjayaraju on 2015-01-04
[COLOR=#000000]@[/COLOR][COLOR=#000000][COLOR=#000000]praseodym: Please follow the attachment [/COLOR][/COLOR][COLOR=#000000]of wireless-script [/COLOR][COLOR=#000000][COLOR=#000000]output.[/COLOR][/COLOR]

---

### Post by praseodym on 2015-01-04
Download these files and save them in "Downloads".

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo dpkg -i ~/Downloads/*.deb
```
Reboot. WLAN should work now. LAN driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot. LAN should work now, too.

Check Bluetooth, too.

---

### Post by rdhanunjayaraju on 2015-01-04
Awesome praseodym. Wifi is working fine now. Thanks for your help. Will update you soon, regarding BT and Ethernet status. Thanks for your help!!!

---

### Post by jeremy31 on 2015-01-04
> **rdhanunjayaraju said:**
> Awesome praseodym. Wifi is working fine now. Thanks for your help. Will update you soon, regarding BT and Ethernet status. Thanks for your help!!!

Bluetooth is a different animal considering, check your win 8 install for this file [COLOR=#000000]bcbtums-win8x64-brcm.inf  and search it for 216c and eventually it will lead you to a .hex file, get the hex file to your Ubuntu install and then ```
dmesg | grep -e bluetooth -e firmware
``` and post results

[/COLOR]The bluetooth relies on firmware that has only been released for windows and there is a good chance if you boot into windows and reboot into Ubuntu, your bluetooth might work as the chipset will retain the firmware loaded during Windows to work in Ubuntu.  If we can find the correct hex file, there is a hex2hcd that should work to load the firmware for Ubuntu

You can download it ```
sudo apt-get install git && git clone git://github.com/jessesung/hex2hcd.git
```
```
cd hex2hcd
```
```
make
```
And then wait for the hex file because I can't access it considering the windows install looks for the bluetooth module to be installed before installing the drivers

---

### Post by rdhanunjayaraju on 2015-01-04
Guys, LAN and BT are not working!

With reference to this thread: ubuntuforums.org/showthread.php?t=2239677a, i ran below commands.

$ sudo /etc/init.d/network-manager restart
sudo: /etc/init.d/network-manager: command not found

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 38:b1:db:e6:9b:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=10.0.1.58 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:b2500000-b2507fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:b2404000-b2404fff memory:b2400000-b2403fff

$ sudo ethtool -s eth0 speed 100 duplex full autoneg off
Cannot get current device settings: No such device
  not setting speed
  not setting duplex
  not setting autoneg

$ sudo ethtool eth0
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available


Please suggest further to fix this. Thank you very much for being with be,

---

### Post by rdhanunjayaraju on 2015-01-04
Jeremy, Interestingly BT is not working on Windows too!

Here is the command output on Ubuntu:

$ dmesg | grep -e bluetooth -e firmware
[   11.846581] usb 1-1.3: Direct firmware load failed with error -2
[   11.847109] Bluetooth: can't load firmware, may not work correctly

---

### Post by jeremy31 on 2015-01-05
> **rdhanunjayaraju said:**
> Jeremy, Interestingly BT is not working on Windows too!

Here is the command output on Ubuntu:

$ dmesg | grep -e bluetooth -e firmware
[   11.846581] usb 1-1.3: Direct firmware load failed with error -2
[   11.847109] Bluetooth: can't load firmware, may not work correctly

You will need to download the drivers for Windows from your computer manufacturers website and install.  I found a few downloads but none that support the card, the newest version of the driver is an .exe file that searches for the hardware before it will install

---

### Post by geezee on 2015-02-20
Hi everyone!

My HP Stream x360 has the same Broadcom Hybrid WiFi/Bluetooth chip:

Broadcom Corporation BCM43142 802.11b/g/n (rev 01)

Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. 

I am running Ubuntu 14.10 and both WiFi and Bluetooth are basically working. I installed bcmwl-kernel-source and converted the windows bluetooth firmware as suggested in this thread.

If someone needs the hcd file, feel free to use it. It goes to /lib/firmware/brcm 

[ATTACH]260107[/ATTACH]

I had to gzip it, because hcd file extension seems not to be allowed here.

Anyway. Too good to be true. WiFi works quite fine, Bluetooth as well. Quite well means that there is package loss and sometimes disconnects on WiFi and on Bluetooth audio (A2DP) I get ugly skips. That sucks, because I want to use this device for watching online video streams.

This looks like this in syslog:

Feb 19 19:25:01 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 82295 us (= 14516 bytes) in audio stream
Feb 19 19:25:02 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 77179 us (= 13612 bytes) in audio stream
Feb 19 19:25:03 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 74174 us (= 13084 bytes) in audio stream
Feb 19 19:25:04 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 72142 us (= 12724 bytes) in audio stream
Feb 19 19:25:05 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 76156 us (= 13432 bytes) in audio stream
Feb 19 19:25:06 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 170659 us (= 30104 bytes) in audio stream

I observed that this only happens with WiFi turned on, as soon as I turn off Wifi, Bluetooth audio works just fine.

Maybe the USB bus is overloaded, I don't know. If anyone experiences the same behavior, help would be very much appreciated.

---

### Post by ashok5 on 2015-08-24
Can someone help me? I have Broadcom BCM43142, Bluetooth is not working though wireless driver is working.

Following is the output of - **dmesg | grep -e bluetooth -e error**[INDENT][16716.531578] Modules linked in: rndis_host cdc_ether usbnet mii btusb **bluetooth** pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) rtsx_usb_ms memstick uvcvideo videobuf2_vmalloc wl(POE) videobuf2_memops videobuf2_core v4l2_common videodev media intel_rapl snd_hda_codec_hdmi iosf_mbi snd_hda_codec_conexant snd_hda_codec_generic i915 snd_hda_intel snd_hda_controller snd_hda_codec cfg80211 x86_pkg_temp_thermal intel_powerclamp coretemp snd_hwdep kvm_intel kvm snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq crct10dif_pclmul crc32_pclmul snd_seq_device snd_timer drm_kms_helper mei_me snd drm soundcore i2c_algo_bit shpchp joydev mei ghash_clmulni_intel lpc_ich ideapad_laptop sparse_keymap cryptd mac_hid video serio_raw parport_pc ppdev lp parport autofs4 rtsx_usb_sdmmc rtsx_usb[/INDENT]
[INDENT][16723.497838] Modules linked in: rndis_host cdc_ether usbnet mii btusb **bluetooth** pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) rtsx_usb_ms memstick uvcvideo videobuf2_vmalloc wl(POE) videobuf2_memops videobuf2_core v4l2_common videodev media intel_rapl snd_hda_codec_hdmi iosf_mbi snd_hda_codec_conexant snd_hda_codec_generic i915 snd_hda_intel snd_hda_controller snd_hda_codec cfg80211 x86_pkg_temp_thermal intel_powerclamp coretemp snd_hwdep kvm_intel kvm snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq crct10dif_pclmul crc32_pclmul snd_seq_device snd_timer drm_kms_helper mei_me snd drm soundcore i2c_algo_bit shpchp joydev mei ghash_clmulni_intel lpc_ich ideapad_laptop sparse_keymap cryptd mac_hid video serio_raw parport_pc ppdev lp parport autofs4 rtsx_usb_sdmmc rtsx_usb[/INDENT]

Although there are many similar lines I have posted only 2

---

### Post by Akash Singhal on 2015-08-24
I know that I am late to the party but still posting a trick that worked for me. If you are dual-booting, log in to windows and then reset your wifi-router settings.

Instead of using a 802.11g/n mode, switch to 802.11b. This works perfectly fine atleast for me with Ubuntu 14.04. My connection is now stable and pretty fast.

---

### Post by diegojp on 2015-12-03
> **geezee said:**
> Hi everyone!

My HP Stream x360 has the same Broadcom Hybrid WiFi/Bluetooth chip:

Broadcom Corporation BCM43142 802.11b/g/n (rev 01)

Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. 

I am running Ubuntu 14.10 and both WiFi and Bluetooth are basically  working. I installed bcmwl-kernel-source and converted the windows  bluetooth firmware as suggested in this thread.

If someone needs the hcd file, feel free to use it. It goes to /lib/firmware/brcm 

[ATTACH]260107[/ATTACH]

I had to gzip it, because hcd file extension seems not to be allowed here.

Anyway. Too good to be true. WiFi works quite fine, Bluetooth as well.  Quite well means that there is package loss and sometimes disconnects on  WiFi and on Bluetooth audio (A2DP) I get ugly skips. That sucks,  because I want to use this device for watching online video streams.

This looks like this in syslog:

Feb 19 19:25:01 geezeebook pulseaudio[3222]: [bluetooth]  module-bluetooth-device.c: Skipping 82295 us (= 14516 bytes) in audio  stream
Feb 19 19:25:02 geezeebook pulseaudio[3222]: [bluetooth]  module-bluetooth-device.c: Skipping 77179 us (= 13612 bytes) in audio  stream
Feb 19 19:25:03 geezeebook pulseaudio[3222]: [bluetooth]  module-bluetooth-device.c: Skipping 74174 us (= 13084 bytes) in audio  stream
Feb 19 19:25:04 geezeebook pulseaudio[3222]: [bluetooth]  module-bluetooth-device.c: Skipping 72142 us (= 12724 bytes) in audio  stream
Feb 19 19:25:05 geezeebook pulseaudio[3222]: [bluetooth]  module-bluetooth-device.c: Skipping 76156 us (= 13432 bytes) in audio  stream
Feb 19 19:25:06 geezeebook pulseaudio[3222]: [bluetooth]  module-bluetooth-device.c: Skipping 170659 us (= 30104 bytes) in audio  stream

I observed that this only happens with WiFi turned on, as soon as I turn off Wifi, Bluetooth audio works just fine.

Maybe the USB bus is overloaded, I don't know. If anyone experiences the  same behavior, help would be very much appreciated.



Can you help me? i can't get BT working! i have the same netbook as yours, HP Stream x360 (a sea blue one) with same Broadcom piece-of-crap-hybrid-****-wifi-bt-thingy
I tried to follow your steps but what exactly did you do?

---

### Post by lapicero2 on 2016-02-11
I installed only ubuntu, I have no windows now, is it possible to change  802.11g/n mode  to 802.11b. from linux? I did all the other solutions but wifi works not very well and bluetooth does not work at all thanks a a lot

---

### Post by Rafael_Aguilar on 2016-06-21
> **geezee said:**
> Hi everyone!

My HP Stream x360 has the same Broadcom Hybrid WiFi/Bluetooth chip:

Broadcom Corporation BCM43142 802.11b/g/n (rev 01)

Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. 

I am running Ubuntu 14.10 and both WiFi and Bluetooth are basically working. I installed bcmwl-kernel-source and converted the windows bluetooth firmware as suggested in this thread.

If someone needs the hcd file, feel free to use it. It goes to /lib/firmware/brcm 

[ATTACH]260107[/ATTACH]

I had to gzip it, because hcd file extension seems not to be allowed here.

Anyway. Too good to be true. WiFi works quite fine, Bluetooth as well. Quite well means that there is package loss and sometimes disconnects on WiFi and on Bluetooth audio (A2DP) I get ugly skips. That sucks, because I want to use this device for watching online video streams.

This looks like this in syslog:

Feb 19 19:25:01 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 82295 us (= 14516 bytes) in audio stream
Feb 19 19:25:02 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 77179 us (= 13612 bytes) in audio stream
Feb 19 19:25:03 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 74174 us (= 13084 bytes) in audio stream
Feb 19 19:25:04 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 72142 us (= 12724 bytes) in audio stream
Feb 19 19:25:05 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 76156 us (= 13432 bytes) in audio stream
Feb 19 19:25:06 geezeebook pulseaudio[3222]: [bluetooth] module-bluetooth-device.c: Skipping 170659 us (= 30104 bytes) in audio stream

I observed that this only happens with WiFi turned on, as soon as I turn off Wifi, Bluetooth audio works just fine.

Maybe the USB bus is overloaded, I don't know. If anyone experiences the same behavior, help would be very much appreciated.

Hello pal, I've been experimenting exact same scenario, I'm running Kubuntu 16.04 and as you point, with Wifi turned off, bluetooth communication get's better, it seems it's the Hybrid technologies messing all up,

Have you found any solutions or workaround that helped you?

---

