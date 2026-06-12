---
title: "Intel Centrino Wireless-N 1000"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by yonasbel on 2013-11-19
[COLOR=#000000]Hello everyone, I recently installed Ubuntu 12.04 and Windows 7 (dual boot) on my HP laptop. But the wireless network is not working on Ubuntu 12.04. I can see all the available wireless networks but I'm unable to connect. [I]

Code :     [/I][/COLOR][COLOR=#000000][I]lspci | grep Network

[/I][/COLOR]02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]


Code :    iwconfig

wlan0     IEEE 802.11bg  ESSID:"IJOLE_BALE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:9F:93:FF:14   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



Code:      dmesg | grep iwl

[    9.227002] iwlwifi 0000:02:00.0: irq 47 for MSI/MSI-X
[   10.196417] iwlwifi 0000:02:00.0: Firmware has old API version, expected v5, got v3.
[   10.196427] iwlwifi 0000:02:00.0: New firmware can be obtained from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/).
[   10.196432] iwlwifi 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
[   10.367002] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.367007] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.367009] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.367011] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.367013] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.367016] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   10.367080] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   10.374378] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   10.835017] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.542427] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   18.549839] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   18.682068] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   18.689340] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[  618.695955] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[  618.736039] iwlwifi 0000:02:00.0: Not sending command - RF KILL
[ 2182.641969] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[ 2185.742784] Modules linked in: rfcomm(F) bnep(F) bluetooth(F) parport_pc(F) ppdev(F) binfmt_misc(F) snd_hda_codec_hdmi(F) snd_hda_codec_idt(F) snd_hda_intel(F) snd_hda_codec(F) snd_hwdep(F) snd_pcm(F) snd_seq_midi(F) snd_rawmidi(F) snd_seq_midi_event(F) uvcvideo(F) snd_seq(F) wl(POF) ir_lirc_codec(F) snd_timer(F) lirc_dev(F) arc4(F) videobuf2_core(F) ir_mce_kbd_decoder(F) i915(F) videodev(F) snd_seq_device(F) videobuf2_vmalloc(F) ir_sanyo_decoder(F) snd(F) coretemp(F) soundcore(F) videobuf2_memops(F) ir_sony_decoder(F) joydev(F) iwldvm(F) ir_jvc_decoder(F) ir_rc6_decoder(F) drm_kms_helper(F) ir_rc5_decoder(F) snd_page_alloc(F) drm(F) ir_nec_decoder(F) rc_rc6_mce(F) psmouse(F) hp_accel(F) gpio_ich(F) lis3lv02d(F) ene_ir(F) rc_core(F) serio_raw(F) i2c_algo_bit(F) microcode(F) hp_wmi(F) lpc_ich(F) sparse_keymap(F) lib80211(F) input_polldev(F) iwlwifi(F) video(F) wmi(F) mac_hid(F) brcmsmac(F) mac80211(F) bcma(F) brcmutil(F) cfg80211(F) cordic(F) lp(F) parport(F) ahci(F) libahci(F) r8169(F)
[11925.598417] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[11925.606442] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[11925.614175] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3

---

### Post by chili555 on 2013-11-19
> d(F) brcmsmac(F) mac80211(F) bcma(F) brcmutil(F) cfg80211(F) cordic(F) lp(F) parport(F) ahci(F) libahci(F) r8169(F)Man, oh man! You have a lot of wireless drivers loaded! I suspect most of them are wrong and that they conflict. Please show me:```
lspci -nn | grep -e 0200 -e 0280
cat /etc/modules
lsmod
```Thanks.

---

### Post by yonasbel on 2013-11-20
Code :  lspci -nn | grep -e 0200 -e 0280

```
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02
```)

Code :  cat /etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
brcmsmac
```


Code:   lsmod

```
Module                  Size  Used by
cdc_acm                22415  0 
rfcomm                 38400  0 
bnep                   17852  2 
bluetooth             211552  10 rfcomm,bnep
parport_pc             27612  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     36612  1 
snd_hda_codec_idt      64649  1 
snd_hda_intel          38819  3 
snd_hda_codec         118650  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               72250  0 
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
wl                   2902285  0 
ir_lirc_codec          12739  0 
snd_timer              28931  2 snd_pcm,snd_seq
lirc_dev               18700  1 ir_lirc_codec
arc4                   12509  2 
videobuf2_core         39385  1 uvcvideo
ir_mce_kbd_decoder     12681  0 
i915                  550464  4 
videodev               96131  2 uvcvideo,videobuf2_core
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_vmalloc      12920  1 uvcvideo
ir_sanyo_decoder       12465  0 
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
coretemp               13324  0 
soundcore              12600  1 snd
videobuf2_memops       13042  1 videobuf2_vmalloc
ir_sony_decoder        12462  0 
joydev                 17329  0 
iwldvm                227006  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
drm_kms_helper         47749  1 i915
ir_rc5_decoder         12459  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
drm                   233935  5 i915,drm_kms_helper
ir_nec_decoder         12459  0 
rc_rc6_mce             12454  0 
psmouse                82769  0 
hp_accel               25756  0 
gpio_ich               13278  0 
lis3lv02d              19536  1 hp_accel
ene_ir                 18019  0 
rc_core                21294  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
serio_raw              13031  0 
i2c_algo_bit           13316  1 i915
microcode              18433  0 
hp_wmi                 17748  0 
lpc_ich                17048  0 
sparse_keymap          13658  1 hp_wmi
lib80211               14040  1 wl
input_polldev          13648  1 lis3lv02d
iwlwifi               160771  1 iwldvm
video                  19116  1 i915
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
brcmsmac              534541  0 
mac80211              541819  2 iwldvm,brcmsmac
bcma                   39810  1 brcmsmac
brcmutil               14355  1 brcmsmac
cfg80211              453919  5 wl,iwldvm,iwlwifi,brcmsmac,mac80211
cordic                 12518  1 brcmsmac
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   25631  4 
libahci                26336  1 ahci
r8169                  62532  0
```

---

### Post by chili555 on 2013-11-20
I am quite confident that the conflicting Broadcom drivers are not helping here. Let's fix things up a bit:```
gksudo gedit /etc/modules
```Remove the brcmsmac line, proofread carefully, save and close gedit. Next do:```
sudo apt-get remove --purge bcmwl-kernel-source
```After it is finished, reboot and let me hear your report.

---

### Post by yonasbel on 2013-11-20
I  removed the brcmsmac line and bcmwl-kernel-source and reboot my computer, but it couldn't solve my problem. It tries to connect to the wireless network and prompt "wireless network disconnected" message

---

### Post by chili555 on 2013-11-20
Now please do:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let me have your report. If it is not connecting, please post:```
lsmod
dmesg | grep iwl
```Thanks.

---

### Post by varunendra on 2013-11-20
@ yonasbel,

You should post the command outputs within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, follow the "Using Code Tags" link in my signature. I'm sure you'd like it, as we do. :)

---

### Post by yonasbel on 2013-11-21
It is not connecting 

Code : lsmod
```
Module                  Size  Used bybnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     36612  1 
snd_hda_codec_idt      64649  1 
binfmt_misc            17292  1 
arc4                   12509  2 
snd_hda_intel          38819  3 
snd_hda_codec         118650  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
iwldvm                227006  0 
mac80211              541819  1 iwldvm
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
coretemp               13324  0 
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
i915                  550464  4 
snd_timer              28931  2 snd_pcm,snd_seq
iwlwifi               160771  1 iwldvm
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72250  0 
drm_kms_helper         47749  1 i915
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   233935  5 i915,drm_kms_helper
soundcore              12600  1 snd
ir_lirc_codec          12739  0 
videobuf2_core         39385  1 uvcvideo
lirc_dev               18700  1 ir_lirc_codec
videodev               96131  2 uvcvideo,videobuf2_core
cfg80211              453919  3 iwldvm,mac80211,iwlwifi
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
gpio_ich               13278  0 
ir_mce_kbd_decoder     12681  0 
videobuf2_vmalloc      12920  1 uvcvideo
ir_sanyo_decoder       12465  0 
videobuf2_memops       13042  1 videobuf2_vmalloc
ir_sony_decoder        12462  0 
joydev                 17329  0 
microcode              18433  0 
psmouse                82769  0 
ir_jvc_decoder         12459  0 
i2c_algo_bit           13316  1 i915
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
lpc_ich                17048  0 
serio_raw              13031  0 
ir_nec_decoder         12459  0 
rc_rc6_mce             12454  0 
hp_accel               25756  0 
mac_hid                13077  0 
lis3lv02d              19536  1 hp_accel
ene_ir                 18019  0 
hp_wmi                 17748  0 
rc_core                21294  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
sparse_keymap          13658  1 hp_wmi
input_polldev          13648  1 lis3lv02d
video                  19116  1 i915
wmi                    18744  1 hp_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   25631  2 
libahci                26336  1 ahci
r8169                  62532  0 



```

code :  dmesg | grep iwl

```
[    9.473431] iwlwifi 0000:02:00.0: irq 47 for MSI/MSI-X[    9.708981] iwlwifi 0000:02:00.0: Firmware has old API version, expected v5, got v3.
[    9.708989] iwlwifi 0000:02:00.0: New firmware can be obtained from http://www.intellinuxwireless.org/.
[    9.708994] iwlwifi 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
[   10.046372] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.046373] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.046375] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.046376] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.046377] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.046379] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   10.046442] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   10.053720] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   10.305845] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.767819] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.775269] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   17.910057] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.917343] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3



```

---

### Post by yonasbel on 2013-11-21
@ Varunendra 
Thanks for the tip

---

### Post by chili555 on 2013-11-21
> [    9.473431] iwlwifi 0000:02:00.0: irq 47 for MSI/MSI-X[    9.708981] iwlwifi 0000:02:00.0: Firmware has old API version, expected v5, got v3.
[    9.708989] iwlwifi 0000:02:00.0: [COLOR="#FF0000"]New firmware[/COLOR] can be obtained from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/).
[    9.708994] iwlwifi 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488Ah, haaa!! Let's try updating the firmware. With a working wired ethernet connection, please do:```
sudo apt-get install --reinstall linux-firmware
```Reboot and do:```
dmesg | grep iwl
```Is the same message still there? If so, let's try this. Download this file to your desktop. [http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-39.31.5.1.tgz](http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-39.31.5.1.tgz) Right-click it and select 'Extract Here.' Now open the terminal and do:```
cd Desktop/iwlwifi-ucode-39.31.5.1
sudo cp iwlwifi-1000-5.ucode  /lib/firmware/
```Reboot and see if it is now working.

Notice, for the benefit of the searchers and driver dawgs out there, that dmesg said, "...expected v5, got v3." We are installing iwlwifi-1000-[COLOR="#FF0000"]5[/COLOR].ucode.

---

### Post by varunendra on 2013-11-21
> **chili555 said:**
> Notice, for the benefit of the searchers and driver dawgs out there, that dmesg said, "...expected v5, got v3." We are installing iwlwifi-1000-[COLOR="#FF0000"]5[/COLOR].ucode.

Duly noted here, thank you sir ! :)

---

### Post by yonasbel on 2013-11-21
Now the firmware is updated, but it's still not working 

dmesg | grep iwl

```
[    8.882601] iwlwifi 0000:02:00.0: irq 47 for MSI/MSI-X
[    9.152705] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138
[    9.722782] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.722787] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.722789] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.722791] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    9.722794] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[    9.722797] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.722857] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    9.730150] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   10.057571] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.432860] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.440173] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   17.574109] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.581416] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3

```

---

### Post by chili555 on 2013-11-21
We're making some improvement. Let's see:```
iwconfig
sudo iwlist wlan0 scan
```We don't need to see all the results; just tell us if there are results or any error message if there are no results.

---

### Post by yonasbel on 2013-11-21
for ' iwconfig ' no wireless extension for lo and eth0 AND there is no error message for ' sudo iwlist wlan0 scan '

---

### Post by chili555 on 2013-11-21
> **yonasbel said:**
> for ' iwconfig ' no wireless extension for lo and eth0 AND there is no error message for ' sudo iwlist wlan0 scan 'Whhaaaatt?? The driver iwlwifi ought to see your wireless card and create a wireless interface, ideally wlan0. It obviously does not. Let's dig deeper. Please reboot so we have a clean slate and run:```
dmesg > wifi.txt
cat /etc/modprobe.d/iwlwifi.conf >> wifi.txt
uname -r >> wifi.txt
```Find the text file wifi.txt in your user directory and paste it here. Give us the link in your reply. 

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by yonasbel on 2013-11-22
Okay, here is the link [http://paste.ubuntu.com/6457379/](http://paste.ubuntu.com/6457379/)

---

### Post by chili555 on 2013-11-22
We see this:> [  120.601523] wlan0: authenticate with 00:1a:9f:93:ff:14
[  120.616556] wlan0: send auth to 00:1a:9f:93:ff:14 (try 1/3)
[  120.618992] wlan0: authenticated
[  120.620042] wlan0: associate with 00:1a:9f:93:ff:14 (try 1/3)
[  120.622865] wlan0: RX AssocResp from 00:1a:9f:93:ff:14 (capab=0x411 status=0 aid=1)
[  120.629047] wlan0: associated
[  166.209421] wlan0: deauthenticating from 00:1a:9f:93:ff:14 by local choice (reason=3)In other words, it connects and a few moments later, it drops.

Please try this:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Remove the last line so it reads:```
options iwlwifi 11n_disable=1 bt_coex_active=N
```Proofread, save and close gedit. Next, find out your country code from here: [http://en.wikipedia.org/wiki/ISO_3166-1](http://en.wikipedia.org/wiki/ISO_3166-1) Now do:```
gksudo gedit /etc/rc.local
```Right above exit 0, add this:```
iw reg set XX
```Where XX is your country code. As an example, in the United States, you would use iw reg set US. Proofread, save and close gedit. Reboot and let us have your report.

---

### Post by yonasbel on 2013-11-22
Still unable to connect, I have changed the country code to 'FI' and edited the files but same problem keeps appearing

---

### Post by chili555 on 2013-11-23
We will have to keep digging. Again using paste.ubuntu as above, let's see:```
dmesg > wifi2.txt
cat /var/log/syslog | grep -e etwork -e iwl -e 8021   >> wifi2.txt
iwconfig >> wifi2.txt
```Thanks.

---

### Post by yonasbel on 2013-11-23
content of wifi2.txt   [http://paste.ubuntu.com/6465849/](http://paste.ubuntu.com/6465849/)

---

### Post by chili555 on 2013-11-24
Frankly, I don't see very much wrong here; I see just one thing that is suspicious:> Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <warn> Activation (wlan0) failed for access point (IJOLE_BALE)
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <info> Marking connection 'IJOLE_BALE' invalid.
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <warn> Activation (wlan0) failed.
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <info> [COLOR="#FF0000"](wlan0): deactivating device (reason 'none') [0][/COLOR]
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <info> [COLOR="#FF0000"]Policy set 'Wired connection 1' (eth0) as default[/COLOR] for IPv4 routing and DNS.
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 23 13:10:56 yonas-HP-Pavilion-dv6-Notebook-PC NetworkManager[914]: <info> (wlan0): supplicant interface state: completed -> disconnectedNotice the timestamp is the same 13:10:56 for all of these. I wonder if the ethernet was connected all this time. Network Manager will prefer wired over wireless and will usually not use wireless if wired is available.

Is the behavior the same with the ethernet detached? Do the logs look the same?

I would also suggest you set IPv6 to Ignore in Network Manager.

---

### Post by yonasbel on 2013-11-27
Hey chili555

you are right, I forgot to unplug the ethernet. Now the logs are different [http://paste.ubuntu.com/6484036/](http://paste.ubuntu.com/6484036/) . IPv6 is also ignored in Network Manager

---

### Post by yonasbel on 2013-11-29
Yes, it is fixed!!
Thank you for your help [COLOR=#ff0000]chili555[/COLOR]

---

### Post by chili555 on 2013-11-29
> **yonasbel said:**
> Yes, it is fixed!!
Thank you for your help [COLOR=#ff0000]chili555[/COLOR]Awesome! Great news. Glad it's working now.

---

