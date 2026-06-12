---
title: "Re: HP Pavilion TS11 - Realtek RT3290 does not detect wireless networks"
date: 2017-07-11
forum: Networking &amp; Wireless
---

### Post by jet-bundle on 2017-07-11
I have installed Lubuntu 16.04 on this laptop (replacing Windows 8.1), but WiFi now does not work. Wireless info is in pastebin at [http://paste.ubuntu.com/25067107/](http://paste.ubuntu.com/25067107/)
I have looked at the thread "HP Pavilion 17  WiFi adapter Realtek RT3290 does not work" and the symptoms appear similar, in that the response to ```
rfkill list
``` is ```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```
I have tried the various suggestions in that thread with no apparent effect, and so any further advice would be appreciated.

The link to the thread I mentioned above is [https://ubuntuforums.org/showthread.php?t=2353726&highlight=RT3290](https://ubuntuforums.org/showthread.php?t=2353726&highlight=RT3290)

---

### Post by BenginM on 2017-07-11
[FONT=Courier New] Salutations! 

So  i presume wireless was working and enabled in Windows 8!  can you look up / download the user manual for the hp laptop , and find the hotkeys Fn+ combination to enable/disable wifi . isn't there a *Wireless [I]button /* switch[/I] is on the keypad that has a wireless symbol on it! What is the status of the wireless light! I would also look in the BIOS to see if wireless WLAN isn't disabled there . if it's enabled then i would try and reset BIOS to default settings.
[/FONT]

---

### Post by jet-bundle on 2017-07-11
Sorry, I should have said that pressing the F12 key (labelled with a wireless transmitter, and containing an orange LED which turns blue when WiFi is enabled, as it used to when running Windows) was the first thing I tried! Pressing that key now has no effect at all.

[Edit] There's no entry showing WiFi enabled/disabled on the setup screen (F10 in startup). I loaded the default values, but this has had no effect.

---

### Post by BenginM on 2017-07-11
does sudo rfkill unblock 0 , or sudo rfkill unlock all  ..has an effect! i suggest you reboot after that and

sudo rfkill list , to check again!

---

### Post by jet-bundle on 2017-07-11
Unfortunately these have no effect: still hard blocked.

---

### Post by praseodym on 2017-07-11
Install this driver:

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf 5641297-RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot

---

### Post by jet-bundle on 2017-07-12
Thank you. Two problems, second fatal. Line 3 ```
tar xvf RT3290_u16_v3.tar.gz
``` gave an error, so I replaced it by ```
tar xvf 5641297-RT3290_u16_v3.tar.gz
``` and that was successful. But line 8 ```
sudo cp /firmware/rt3290.bin /lib/firmware
``` gave ```
: cannot stat '/firmware/rt3290.bin': No such file or directory
``` I'm not sure what to do next.

---

### Post by praseodym on 2017-07-12
Try

```
sudo cp firmware/rt3290.bin /lib/firmware 
```

---

### Post by praseodym on 2017-07-12
Corrected the installation procedure, thanks

---

### Post by jet-bundle on 2017-07-12
Thank you. No errors from ```
sudo cp firmware/rt3290.bin /lib/firmware
``` now, so I completed the procedure and rebooted. Unfortunately still no WiFi, and now ```
rfkill list
``` produces no output at all, so that is different - previously the response (given in my opening post) was ```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

I've created a new wireless-info.txt file at [http://paste.ubuntu.com/25076558/](http://paste.ubuntu.com/25076558/) in case that helps.

---

### Post by BenginM on 2017-07-12
[FONT=courier new]Honestly , It's "Hard blocked"! i haven't yet seen a solution to change it by software .. this should be interesting!

I would Try reseting the BIOS back to defaults.[/FONT]

---

### Post by jet-bundle on 2017-07-13
As stated in post #3 above, I have already set the BIOS back to its default values.

---

### Post by BenginM on 2017-07-13
> **jet-bundle said:**
> As stated in post #3 above, I have already set the BIOS back to its default values.


[FONT=courier new] Excuse me  as i didn't re-read your edit bit on that post! well then , I suppose you could try with [/FONT]

```
 
[FONT=courier new]FN+F12 , or Alt+F12 ..  and run:$ sudo rm /dev/rfkill[/FONT]

```
[FONT=courier new]
unplug any device cable attached to the machine ..Now Shutdown the machine not reboot. remove the battery 
for a couple minutes.. place the battery back,  Now power on.. while booting hit the F12 key first .. if the wifi is still blocked , try a second shutdown but hit the FN+12 this time .. if nothing,  a third shutdown and hit Alt+12 ... !

# please read varunendra's post #6 here : [https://ubuntuforums.org/showthread.php?t=2178085](https://ubuntuforums.org/showthread.php?t=2178085)

[/FONT]```

  [FONT=courier new]
[/FONT]
[FONT=courier new]$ sudo modprobe -r rt2800pci

$ sudo modprobe rt2800pci

$ sudo rfkill unblock 0 , or all 

$ [/FONT][FONT=courier new]sudo rfkill list
[/FONT]

```[FONT=courier new]

the last bit would be to try booting with the live usb or cd , and see the wifi status there.. if you get the hardware blocked there .. then you might need to install windows again enable wifi shudown windows properly and boot into ubuntu live and reinstall again.[/FONT]

---

### Post by praseodym on 2017-07-13
If it is an UEFI: Deactivate Secure Boot. If it is a BIOS: Reset it to default. Please show
```

lsmod
```
completely

---

### Post by jet-bundle on 2017-07-13
I tried all the F12 options as described, with no effect. I tried the modprobe commands exactly as specified, and still rfkill list produces no output.

Booting from the DVD gives a working system with no WiFi. It might be relevant that, when I installed the system, the RT3290 was detected and I was invited to specify WiFi credentials, but no network connection was actually made during the rest of the installation process.

---

### Post by jet-bundle on 2017-07-13
Here is the result of lsmod (after disabling secure boot): ```
Module                  Size  Used by
uas                    24576  0
usb_storage            73728  2 uas
cfg80211              581632  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
amd_freq_sensitivity    16384  0
snd_hda_codec_realtek    86016  1
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     45056  1
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
snd_hda_intel          36864  0
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
kvm                   598016  0
media                  40960  2 uvcvideo,videodev
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
hp_wmi                 16384  0
snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
irqbypass              16384  1 kvm
sparse_keymap          16384  1 hp_wmi
crct10dif_pclmul       16384  0
snd_seq_midi           16384  0
crc32_pclmul           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
ghash_clmulni_intel    16384  0
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           167936  0
rt3290sta            1159168  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
glue_helper            16384  1 aesni_intel
input_leds             16384  0
joydev                 20480  0
ablk_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_seq,snd_pcm
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
hid_multitouch         20480  0
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
snd                    86016  11 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
serio_raw              16384  0
fam15h_power           16384  0
k10temp                16384  0
soundcore              16384  1 snd
shpchp                 36864  0
i2c_piix4              24576  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
mac_hid                16384  0
input_polldev          16384  1 lis3lv02d
hp_wireless            16384  0
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  3 hid_generic,usbhid,hid_multitouch
rtsx_pci_sdmmc         24576  0
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  2
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
drm_kms_helper        167936  1 radeon
syscopyarea            16384  1 drm_kms_helper
psmouse               139264  0
sysfillrect            16384  1 drm_kms_helper
sdhci_pci              28672  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
sdhci                  45056  1 sdhci_pci
ahci                   36864  3
libahci                32768  1 ahci
drm                   368640  5 radeon,ttm,drm_kms_helper
r8169                  81920  0
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
wmi                    16384  1 hp_wmi
fjes                   28672  0
video                  40960  0

```

---

### Post by praseodym on 2017-07-13
Lets try
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot and show
```

rfkill list
iwconfig
```

---

### Post by jet-bundle on 2017-07-13
```
$ rfkill list
$ iwconfig
enp1s0    no wireless extensions.
lo        no wireless extensions.
eno1      Ralink STA  

```

---

### Post by BenginM on 2017-07-13
interesting .. we see 


```


sparse_keymap          16384  1 hp_wmi

hp_wireless            16384  0


```

[http://cateee.net/lkddb/web-lkddb/HP_WIRELESS.html](http://cateee.net/lkddb/web-lkddb/HP_WIRELESS.html)

---

### Post by BenginM on 2017-07-13
[FONT=tahoma]y[FONT=arial]ou might wanna try this :

sudo modprobe hp-wireless 

**  is the wireless key F12 workin'!**

If not, try:     

sudo modprobe -r hp-wmi

** ## if none of the above brought the wifi to life , then try :**

sudo modprobe -r hp-wmi    
sudo modprobe -r wmi

any changes ..![/FONT][/FONT]

---

### Post by jet-bundle on 2017-07-15
Sorry about the pause, I've been busy elsewhere.

None of the suggestions in post #20 have any effect.

I'm puzzled why the response to rfkill list has changed from showing WiFi as hardware blocked, to not showing it at all.

EDIT: If I boot from the DVD, rfkill list shows both hardware and software blocked; if I then try sudo rfkill unblock 0 then it is still hardware blocked. If, following that, I boot from the hard disk, then rfkill list again gives no response.

---

### Post by praseodym on 2017-07-16
Lets try
```

sudo modprobe -rfv rt3290sta
sudo rfkill unblock all
rfkill list
sudo modprobe -v rt3290sta
```
Please repeat it again with the 4th command being
```

sudo modprobe -v rt2800pci
```

---

### Post by jet-bundle on 2017-07-16
Using sudo modprobe -v rt3290sta gave ```
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/rt3290sta.ko
``` and using sudo modprobe -v rt2800pci gave ```
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko 

```

---

### Post by praseodym on 2017-07-16
What about the respective "rfkill list" outputs?

---

### Post by jet-bundle on 2017-07-16
> **praseodym said:**
> What about the respective "rfkill list" outputs?

Again, no output.

---

### Post by jet-bundle on 2017-07-16
I wondered whether the suggestion "Please repeat it again with the 4th command being sudo modprobe -v rt2800pci" in post #22 needed a similar modification to the first command, so I tried that. Then rfkill list came back to where it was before, and I also received a popup notice "wireless networks are available, select from the network menu" -- but there is no such menu available.

Here is the output: ```
$ sudo modprobe -rfv rt2800pci
rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211
$ sudo rfkill unblock all
$ rfkill list
$ sudo modprobe -v rt2800pci
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.8.0-58-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko 
$ rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
```
And then, on rebooting, rfkill list has reverted to giving no response. So there's some sign of life, but it seems strange and unstable.

---

### Post by praseodym on 2017-07-16
Please open this file
```

gksudo gedit /etc/rc.local
```
Add these lines
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe -r rt3290sta
sleep 5
rfkill unblock all
modprobe rt3290sta

exit 0

```
Make sure the file end with an empty _line_. Save, close the editor and reboot. Check again
```

rfkill list
iwconfig
lsmod
dmesg | egrep 'rt2|rt3'
sudo iwlist scan
```

---

### Post by jet-bundle on 2017-07-16
Here's the response:```
$ rfkill list
$ iwconfig
enp1s0    no wireless extensions.
lo        no wireless extensions.
eno1      Ralink STA  
          
$ lsmod
Module                  Size  Used by
rt3290sta            1159168  0
cfg80211              581632  0
amd_freq_sensitivity    16384  0
kvm                   598016  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
irqbypass              16384  1 kvm
hp_wmi                 16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
sparse_keymap          16384  1 hp_wmi
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_hda_codec_hdmi     45056  1
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_intel          36864  0
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
ghash_clmulni_intel    16384  0
media                  40960  2 uvcvideo,videodev
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
aesni_intel           167936  0
snd_hwdep              16384  1 snd_hda_codec
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
ablk_helper            16384  1 aesni_intel
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
hid_multitouch         20480  0
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0
input_leds             16384  0
rtsx_pci_ms            20480  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
memstick               20480  1 rtsx_pci_ms
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
fam15h_power           16384  0
k10temp                16384  0
snd_timer              32768  2 snd_seq,snd_pcm
snd                    86016  11 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
shpchp                 36864  0
soundcore              16384  1 snd
i2c_piix4              24576  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
mac_hid                16384  0
input_polldev          16384  1 lis3lv02d
hp_wireless            16384  0
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  3 hid_generic,usbhid,hid_multitouch
amdkfd                139264  1
rtsx_pci_sdmmc         24576  0
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  2
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
psmouse               139264  0
drm_kms_helper        167936  1 radeon
sdhci_pci              28672  0
sdhci                  45056  1 sdhci_pci
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
drm                   368640  5 radeon,ttm,drm_kms_helper
libahci                32768  1 ahci
r8169                  81920  0
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
wmi                    16384  1 hp_wmi
video                  40960  0
fjes                   28672  0
uas                    24576  0
usb_storage            73728  2 uas
$ dmesg | egrep 'rt2|rt3'
[    4.305199] usb usb4-port3: hash matches
[   22.227482] rt3290sta: loading out-of-tree module taints kernel.
[   22.227491] rt3290sta: module license 'unspecified' taints kernel.
[   22.228907] rt3290sta: module verification failed: signature and/or required key missing - tainting kernel
[   22.232496] register rt2860
[   22.864965] rt2860 0000:02:00.0 eno1: renamed from ra0
[   41.957132] register rt2860
[   41.963966] rt2860 0000:02:00.0 eno1: renamed from ra0
$ sudo iwlist scan
enp1s0    Interface doesn't support scanning.
lo        Interface doesn't support scanning.
eno1      Interface doesn't support scanning : Network is down

```

---

### Post by praseodym on 2017-07-16
Is it an UEFI? If yes, deactivate Secure Boot there

---

### Post by jet-bundle on 2017-07-16
It is UEFI; I have already disabled Secure Boot, as reported in #16, and haven't re-enabled it.

---

### Post by jet-bundle on 2017-07-18
I've found out how to clear the hardware block - it is, astonishingly, to replace Lubuntu 16.04 by 16.10, and then reinstall 16.04. But I still haven't managed to connect to a wireless network, although I can see them. Here's the sequence of events.

1. I reported in post #21 that booting 16.04 from the DVD showed both hardware and software blocked, and that "sudo rfkill unblock all" removed the software block but retained the hardware block. I wanted to see what would happen if I booted 16.10 from the DVD, and this showed both software and hardware unblocked.

2. I decided to install 16.10 (although I would have preferred 16.04 as an LTS version). The installation was almost complete, but crashed when attempting to install GRUB. I'd had this problem before when installing Lubunto on a different machine ([https://ubuntuforums.org/showthread.php?t=2351628](https://ubuntuforums.org/showthread.php?t=2351628)) but rather than fiddling with partitions I decided to abort the 16.10 installation.

3. I reinstalled 16.04 without using an Ethernet cable. The RT3290 adapter was detected, but I chose not connect to a network at that stage.
 [ATTACH=CONFIG]276036[/ATTACH]

4. On booting for the first time there was an error message about incomplete language support, which I chose to ignore. But there was also a message indicating that wireless networks were available,
[ATTACH=CONFIG]276037[/ATTACH]

5. This was the Network Manager pop-up menu:
[ATTACH=CONFIG]276040[/ATTACH]
Four wireless networks were detected; but I note that the icon for Network Manager was a broken wire link, rather than (as I think I would have expected) a symbol to show the availability of wireless networks. It might also be worth noting that the LED in the F12 key (the hardware switch for WiFi) was showing orange rather than, as I would have expected, blue. 

6. I chose to connect to my network, the fourth in the list above. This gave the authentication dialog box.
[ATTACH=CONFIG]276038[/ATTACH]
Part-way through entering the password, I was given a notification that the network had been disconnected.
[ATTACH=CONFIG]276039[/ATTACH]
I completed the network password and clicked the Connect button, but nothing happened. I checked the Network Manager popup menu again, but it hadn't changed, and rfkill list still showed neither a hardware nor a software block.

7. I wondered whether the orange light on the F12 key had any relevance, so I experimented with pressing it, looking at the Network Manager menu, and entering rfkill list. After I had tried a couple of options, I was left with a hardware block which I couldn't remove. So I was back in the position I was in when I started this thread.

8. I tried reinstalling 16.04, but there was still a hardware block in the new installation.

9. Finally, I repeated step 2 (installing 16.10 up to the crash on failing to install GRUB) and step 3 (installing 16.04 successfully, apart from the problem with language support). Now rfkill list reports no blocks, but the network status is as in step 6: I can see networks, but can't authenticate.


I wonder if this additional information gives anyone any further clues on my problem? As always, any suggestions would be appreciated.

---

### Post by praseodym on 2017-07-18
So, you are back on module rt2800pci?
```

lsmod
```
Try```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by jet-bundle on 2017-07-18
Thank you.

Before trying your suggestion, I opened the Network Manager pop-up menu. Initially it was just like my earlier image 9.jpg, but then - without any input from touchpad or keyboard - the menu suddenly changed, as I was looking at it, to say "Wi-Fi is disabled by hardware switch"; and then rfkill list showed a hardware block, just as before.

Now for your suggested input.```
$ lsmod
Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
nls_iso8859_1          16384  2
amd_freq_sensitivity    16384  0
kvm                   536576  0
uvcvideo               90112  0
hp_wmi                 16384  0
irqbypass              16384  1 kvm
sparse_keymap          16384  1 hp_wmi
videobuf2_vmalloc      16384  1 uvcvideo
crct10dif_pclmul       16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
crc32_pclmul           16384  0
videobuf2_v4l2         28672  1 uvcvideo
arc4                   16384  2
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
rt2800pci              16384  0
aesni_intel           167936  0
v4l2_common            16384  1 videobuf2_v4l2
rt2800mmio             20480  1 rt2800pci
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd_hda_codec_realtek    86016  1
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
aes_x86_64             20480  1 aesni_intel
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
snd_hda_intel          36864  0
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
media                  24576  2 uvcvideo,videodev
lrw                    16384  1 aesni_intel
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_hwdep              16384  1 snd_hda_codec
ablk_helper            16384  1 aesni_intel
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
cryptd                 20480  2 aesni_intel,ablk_helper
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
cfg80211              565248  2 mac80211,rt2x00lib
snd_rawmidi            32768  1 snd_seq_midi
hid_multitouch         20480  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
fam15h_power           16384  0
rtsx_pci_ms            20480  0
edac_mce_amd           24576  0
eeprom_93cx6           16384  1 rt2800pci
edac_core              53248  0
crc_ccitt              16384  1 rt2800lib
memstick               20480  1 rtsx_pci_ms
input_leds             16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 20480  0
serio_raw              16384  0
k10temp                16384  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 36864  0
soundcore              16384  1 snd
i2c_piix4              24576  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
hp_wireless            16384  0
mac_hid                16384  0
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_multitouch,hid_generic,usbhid
rtsx_pci_sdmmc         24576  0
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  2
psmouse               126976  0
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
sdhci_pci              28672  0
drm_kms_helper        147456  1 radeon
sdhci                  45056  1 sdhci_pci
syscopyarea            16384  1 drm_kms_helper
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
r8169                  81920  0
drm                   360448  5 ttm,drm_kms_helper,radeon
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    20480  1 hp_wmi
video                  40960  0
fjes                   28672  0
$ echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
options rt2800pci nohwcrypt=1
$ sudo modprobe -rfv rt2800pci
rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod crc_ccitt
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211
$ sudo modprobe -v rt2800pci
insmod /lib/modules/4.4.0-31-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko nohwcrypt=1 
$ rfkill list
1: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
$ iwconfig
lo        no wireless extensions.
enp1s0    no wireless extensions.
wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
$ sudo iwlist scan
lo        Interface doesn't support scanning.
enp1s0    Interface doesn't support scanning.
wlo1      Scan completed :
          Cell 01 - Address: FC:3F:7C:36:5F:80
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"V7490825336wn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000090fd2f35
                    Extra: Last beacon: 22884ms ago
                    IE: Unknown: 000D5637343930383235333336776E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD810050F204104A0001101044000102103B00010310470010C100097DAED9E71051C0FF01BEDDBF00102100064875617765691023000F4F70656E524720506C6174666F726D10240007566F7820322E351042000D363035323548303030313331321054000800060050F2040001101100064F70656E5247100800020080103C000101
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```
Also, I've noticed that now the response from rfkill list starts with "1: phy0: Wireless LAN" whereas before the reinstallation it started with "0: phy0: Wireless LAN". But on rebooting rfkill list shows a hard block again. Pressing the F12 key toggles soft block on and off, but doesn't affect the hard block. Also, checking "Wi-Fi enabled" on the Network Manager menu makes no difference. (It no longer says "disabled by hardware switch.")

---

### Post by praseodym on 2017-07-18
Please check when hard blocked
```

sudo rmmod hp_wmi
rfkill list
sudo rfkill unblock all
rfkill list
```

---

### Post by jet-bundle on 2017-07-19
Thank you. ```
$ rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
$ sudo rmmod hp_wmi
$ rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
$ sudo rfkill unblock all
$ rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
$
```
I notice that, this morning, we're back to "0: phy0 Wireless LAN".

---

### Post by praseodym on 2017-07-19
[https://richarddouglasdenton.wordpress.com/2011/05/11/how-to-bypass-a-laptop-wireless-switch/](https://richarddouglasdenton.wordpress.com/2011/05/11/how-to-bypass-a-laptop-wireless-switch/)

Maybe this helps

---

### Post by jet-bundle on 2017-07-20
Thank you.

My inclination is to regard a hardware modification (the "sticky-tape solution") as a last resort; and of course there's always the option of buying a dongle. It may well be that we've run out of options for advice at a distance, so I'd like to repeat my appreciation for all the suggestions.

What I now plan to do is to play around with the different versions (I also have 17.04, but that seems to give other problems) and various combinations of the suggestions made here, including installing the genuine rt3290 driver and blacklisting the rt2880, to see if I can get anywhere.

I won't mark the thread as solved just yet, in case anyone has any further ideas.

---

### Post by jet-bundle on 2017-07-27
Hello.

Over the past few days I have tried, without success, several approaches to connecting to a wireless network. (Even trying a USB dongle failed to work.) But of relevance to the preceding discussion is that, as far as I can see, the closest I have been able to get to connecting with the built-in RT3290 card was when I was using the RT2800pci driver, where a hard block suddenly seemed to appear for no obvious reason.

I reinstalled the RT3290sta driver (RT3290_u16_v3) and, as before, rfkill list no longer gave any output. But the following may be of interest: ```
$ dmesg | grep rt3290
[   18.150690] rt3290sta: module license 'unspecified' taints kernel.
[   18.152151] rt3290sta: module verification failed: signature and/or required key missing - tainting kernel
$ uname -r
4.4.0-87-generic
``` Perhaps these messages indicate a possible source of the problem?

(I should say that I found this version of the driver from a different source, see [http://onthim.blogspot.co.uk/2015/06/install-ralink-rt3290-wi-fi-driver-on.html](http://onthim.blogspot.co.uk/2015/06/install-ralink-rt3290-wi-fi-driver-on.html), but that I saw similar messages with the version kindly supplied by praseodym. I have also tried replacing network manager by wicd, as suggested in the linked page, but with no effect.)

I also now have ```
$ iwconfig
lo        no wireless extensions.
enp1s0    no wireless extensions.
eno1      Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

```

---

### Post by praseodym on 2017-07-27
Is your network "hidden"? If yes, broadcast the ESSID. These messages give me the hint for disabling SecureBoot. Is your BIOS/UEFI up to date?

---

### Post by jet-bundle on 2017-07-28
Network: my own network (with the router about 1m away from the laptop) is not hidden, and there are also some other nearby networks.

UEFI: secure boot is disabled (and has been throughout -- I had to enter a four-digit key from the screen when disabling it at the start of these tests). The BIOS/UEFI software is not up-to-date; I have downloaded the latest version to a USB drive but haven't updated just yet.

[EDIT] I see that there is an option for "Legacy boot" which is not enabled.

---

### Post by jet-bundle on 2017-07-29
I've enabled "legacy boot", but that makes no difference. And as for updating the BIOS? Well ...

The HP website claims never to have heard of a "Pavilion TS 11", even though that's what the System Information screen displays; the closest is the "HP Pavilion 11-s000 Notebook PC series". Still, I downloaded the software to a USB drive as suggested. The instructions then gave an option for updating the BIOS from the UEFI (necessary as there's no longer a copy of Windows on the machine). I was supposed to go to the System Diagnostics screen and select the option for updating the BIOS -- but on my diagnostic screen the only options are for a memory test, a disk test, language change, or exit!

My inclination is to give up with the RT3290 driver, unless someone can source a signed version, and to return to the RT2880. In some circumstances it sort-of works, as explained above, so maybe with some more fiddling I can persuade it to go the distance. If not, I guess I'll just have to give up. But thanks to everyone who has offered support.

---

### Post by praseodym on 2017-07-29
Please check
```

sudo dmidecode -t0 -t1 >> system-info.txt
```
and upload the txt file

---

### Post by jet-bundle on 2017-07-29
[https://pastebin.com/Ub6Q12dY](https://pastebin.com/Ub6Q12dY)

---

### Post by praseodym on 2017-07-29
So, you can forward the output to HP which shows the necessary information to support you
```

BIOS Information
    Vendor: Insyde
    Version: F.13
    Release Date: 09/20/2013
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 4096 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        Targeted content distribution is supported
        UEFI is supported
[COLOR="#FF0000"]    BIOS Revision: 15.19
    Firmware Revision: 33.46[/COLOR]

System Information
 [COLOR="#FF0000"]   Manufacturer: Hewlett-Packard
    Product Name: HP Pavilion TS 11 Notebook PC
    Version: 0978110000405E00010320180
    Serial Number: CND4140J21[/COLOR]
    UUID: C524C5C8-FE7B-E311-B737-A01D480E8088
    Wake-up Type: Power Switch
    SKU Number: F5B84EA#ABU
    Family: 103C_5335KV G=N L=CON B=HP S=PAV
```

---

### Post by jet-bundle on 2017-07-30
Thank you. In fact much of the red highlighted information is also shown on the UEFI System Information screen; they both give the Product Name/Notebook Model as [COLOR=#ff0000]HP Pavilion TS 11 Notebook PC[/COLOR], which isn't recognised by the HP support website. But in fact entering the serial number [COLOR=#ff0000]CND4140J21[/COLOR] instead works, and reveals that the correct product name is "HP Pavilion TouchSmart 11-e102sa Notebook PC".

So I now have the correct up-to-date BIOS on a USB drive. But the laptop won't boot from this, even though I've enabled USB booting and given it priority (it is interrogated, but then the machine boots from the hard disk). And, as I mentioned earlier, the claimed option of using the UEFI system diagnostics screen wasn't available.

I'll get another USB drive (the one I used was quite old), and see if that helps. If not, there are some more options on the HP website that I might try.

---

### Post by praseodym on 2017-07-30
You need a bootable USB using the FreeDOS section shown here:

[https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux)

---

### Post by jet-bundle on 2017-08-07
Hello again.

Rather than updating the BIOS from a bootable USB drive, I decided to start afresh and obtained software from HP to reset the machine to its factory state. This installed Windows, of course, but I could use this to update the BIOS directly. So the BIOS is now up-to-date (version F.21 rather than F.13). I also confirmed that the RA3290 wireless card was working in Windows.

Next I installed Lubuntu 16.04.3 alongside Windows. That was entertaining as HP doesn't like dual-boot machines and insisted on booting straight into Windows. I managed to fix that with some careful copying and renaming of .efi files. Now I can boot into Windows from GRUB whenever I choose, to check that the wireless card still works ...

Then I downloaded the RT3290_u16_v3 driver and installed it. At the end of the installation process a message appeared for a brief period (less than a second) which might have said something about network availability, but I didn't have a chance to read it.

But wireless still doesn't work in Lubuntu, whether or not secure boot is enabled. Entering rfkill list again produces no output, and there are the following messages: ```
$ dmesg | grep rt3290
[   16.086436] rt3290sta: module license 'unspecified' taints kernel.
[   16.088183] rt3290sta: module verification failed: signature and/or required key missing - tainting kernel
``` just as reported in post #38. On the other hand, the following seems to be different: when I started to enter the suggestions from post #22, this was the result:```
$ sudo modprobe -rfv rt3290sta
modprobe: FATAL: Module rt3290sta is in use.
``` Here is some other output which might be helpful:```
$ ifconfig -a
eno1      Link encap:Ethernet  HWaddr 9c:d2:1e:c6:50:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:39 

enp1s0    Link encap:Ethernet  HWaddr a0:1d:48:0e:80:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:57312 (57.3 KB)  TX bytes:57312 (57.3 KB)
``````
$ iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

eno1      Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` and ```
$ lsmod
Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
cfg80211              565248  0
uvcvideo               90112  0
snd_hda_codec_realtek    86016  1
amd_freq_sensitivity    16384  0
videobuf2_vmalloc      16384  1 uvcvideo
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
videobuf2_memops       16384  1 videobuf2_vmalloc
hp_wmi                 16384  0
videobuf2_v4l2         28672  1 uvcvideo
snd_hda_intel          40960  0
kvm                   544768  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
sparse_keymap          16384  1 hp_wmi
v4l2_common            16384  1 videobuf2_v4l2
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
irqbypass              16384  1 kvm
media                  24576  2 uvcvideo,videodev
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              16384  1 snd_hda_codec
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
gf128mul               16384  1 lrw
snd_rawmidi            32768  1 snd_seq_midi
glue_helper            16384  1 aesni_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rt3290sta            1155072  1
input_leds             16384  0
joydev                 20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0
edac_mce_amd           24576  0
hid_multitouch         20480  0
snd_timer              32768  2 snd_pcm,snd_seq
edac_core              53248  0
snd                    81920  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
fam15h_power           16384  0
k10temp                16384  0
i2c_piix4              24576  0
shpchp                 36864  0
soundcore              16384  1 snd
hp_accel               28672  0
mac_hid                16384  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
hp_wireless            16384  0
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_multitouch,hid_generic,usbhid
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
rtsx_pci_sdmmc         24576  0
radeon               1515520  2
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
drm_kms_helper        155648  1 radeon
psmouse               131072  0
syscopyarea            16384  1 drm_kms_helper
sdhci_pci              28672  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
sdhci                  45056  1 sdhci_pci
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
drm                   364544  5 ttm,drm_kms_helper,radeon
r8169                  81920  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
wmi                    20480  1 hp_wmi
fjes                   28672  0
video                  40960  0
```

---

### Post by entw on 2017-10-14
> **jet-bundle said:**
> Hello again.
...
But wireless still doesn't work in Lubuntu, whether or not secure boot is enabled. Entering rfkill list again produces no output, and there are the following messages: ```
$ dmesg | grep rt3290
[   16.086436] rt3290sta: module license 'unspecified' taints kernel.
[   16.088183] rt3290sta: module verification failed: signature and/or required key missing - tainting kernel
```
...

```
sudo mokutil --disable-validation
```
Do this, enter the password (can be a couple of numbers, doesn't matter), reboot and follow the instructions of your BIOS (UEFI).

---

