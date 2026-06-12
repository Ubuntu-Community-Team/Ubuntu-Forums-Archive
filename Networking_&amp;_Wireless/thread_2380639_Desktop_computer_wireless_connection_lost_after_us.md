---
title: "Desktop computer wireless connection lost after usb connected BBBL upgrade"
date: 2017-12-20
forum: Networking &amp; Wireless
---

### Post by k3nden on 2017-12-20
I installed Ubuntu 1604 on to a BeageBoneBlue (BBBL) while connect via usb to my Desktop computer. After update/upgrade/restart of BBBL, i could no longer SSH to BBBL via USB or wireless from desktop. During investigation, i have lost wireless connection on the Desktop. I am lost at this point and somehow renamed wlp2s0 to wlp2s0b1 and decided i needed to ask for help.  I think my drivers are ok - unless i overwrote them.  

Wireless-info.txt based on sticky is found at   [http://paste.ubuntu.com/26219388/](http://paste.ubuntu.com/26219388/)

How can I get wireless reconnected? and did the upgrade for the BBBL cause it or is the desktop problem the reason it will no longer connect...

---

### Post by praseodym on 2017-12-20
You may be affected by the NWM bug:

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot. Wireless driver and firmware is shown and loaded correctly. alternatively, use the Broadcom-STA driver ("Additional Drivers" in the update manager)

---

### Post by k3nden on 2017-12-20
thanks for the response. I competed the two adds suggested. The second added [connection] / wifi.powersave = 2, is that as expected? 
After rebooting, nothing changed - ie no wireless access. So, I tried to change to the Broadcom-STA as suggested but the computer froze/locked-up, requiring hard reboot.  wireless is still nojoy.

[COLOR=#000000]New wireless-info.txt based on sticky is found at  [/COLOR]http://paste.ubuntu.com/26223552/

Something during this process,  a new more urgent problem developed in that the kernel - [COLOR=#000000]Linux 4.10.0-42-generic #46~16.04.1-Ubuntu is corrupted and I have only managed to reboot the machine using kernel [/COLOR][COLOR=#000000]Linux 4.10.0-38-generic #42~16.04.1-Ubuntu.  some what afraid to try rebooting but i am researching how to re-install kernel??
[/COLOR] [COLOR=#000000]
This is a triple boot mac mini, with 7 partitions but I don't think this is a HW issue. Wireless works fine on the windows participation. 
[/COLOR]

---

### Post by praseodym on 2017-12-20
Try in kernel "42":
```

sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) build-essential dkms broadcom-sta-dkms
```
Worked? Then restart, deactivate Secure-Boot and reboot

---

### Post by k3nden on 2017-12-20
Thanks - that seemed to fix the kernel and update the BCM drivers.  Is the kernel driver (wl) what the b43 installer setup or do I need to do  update the firmware with the b43 installer? 
wifi is still not connected.

new wireless-info posted: [http://paste.ubuntu.com/26224659/](http://paste.ubuntu.com/26224659/)     some permissions may have changed during the updates because after the "wireless-info' saved ---  [sudo] password for ken: came up.  After ctrl-c to exit the prompt, the "Results" were saved and Pastebin successful was displayed. 

What service starts the wifi and where are the settings? 
I played wpa_supplicant  and connmanctl on the BBBL but i see no evidence on this desktop that would indicate either of these services are used.

---

### Post by k3nden on 2017-12-23
assuming that the drivers are correctly installed. I have not been able to use correctly nmcli connection to reload so that wlp2s0 its uuid. I think this is necessary to make wifi operational. When I try
```
nmcli con up {UUID}
```  it returns "Error: Connection activation failed: No suitable device found for this connection. "

```
nmcli con reload
```
returns "Error: failed to reload connections: Rejected send message, 4 matched rules; type="method_call", sender=":1.191" (uid=1000 pid=8788 comm="nmcli con reload ") interface="org.freedesktop.NetworkManager.Settings" member="ReloadConnections" error name="(unset)" requested_reply="0" destination=":1.11" (uid=0 pid=807 comm="/usr/sbin/NetworkManager --no-daemon ")."

Help getting my wireless connection would be greatly appreciated.

---

### Post by praseodym on 2017-12-24
"Soft block" is turned on. Lets check
```

sudo rfkill unblock all
lsmod
rfkill list
iwconfig
```
Did you deactivate SecureBoot?

---

### Post by k3nden on 2017-12-26
```
Module                  Size  Used bycfg80211              565248  0
nls_utf8               16384  1
hfsplus               106496  1
rfcomm                 69632  0
bnep                   20480  2
binfmt_misc            20480  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
kvm                   544768  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
btusb                  45056  0
btrtl                  16384  1 btusb
ghash_clmulni_intel    16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
aesni_intel           167936  0
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
applesmc               20480  0
input_polldev          16384  1 applesmc
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_hda_codec_hdmi     53248  1
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_cirrus    20480  1
snd_hda_codec_generic    77824  1 snd_hda_codec_cirrus
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_cirrus
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_hda_codec_cirrus
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0
input_leds             16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
thunderbolt            53248  0
mei_me                 36864  0
shpchp                 36864  0
apple_gmux             16384  0
lpc_ich                24576  0
apple_bl               16384  1 apple_gmux
soundcore              16384  1 snd
mei                    98304  1 mei_me
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_appleir            16384  0
hid_generic            16384  0
i915                 1208320  181
firewire_ohci          40960  0
i2c_algo_bit           16384  1 i915
tg3                   163840  0
ahci                   36864  4
libahci                32768  1 ahci
drm_kms_helper        155648  1 i915
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sdhci_pci              28672  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
sdhci                  45056  1 sdhci_pci
usbhid                 49152  0
ptp                    20480  1 tg3
drm                   364544  6 i915,drm_kms_helper
hid                   118784  3 hid_generic,usbhid,hid_appleir
pps_core               20480  1 ptp
fjes                   28672  0
video                  40960  2 i915,apple_gmux

```
iwconfig

lo        no wireless extensions.


enp1s0f0  no wireless extensions.

---

### Post by k3nden on 2017-12-26
According to output of mokutil --sb-state

"This system does't support Secure Boot"

Thanks for your time and responses

---

### Post by praseodym on 2017-12-26
So, SB is deactivated?

---

### Post by k3nden on 2017-12-26
yes as far as i can tell. [COLOR=#000000]mokutil --sb-state is the only way that I found to check[/COLOR]

---

