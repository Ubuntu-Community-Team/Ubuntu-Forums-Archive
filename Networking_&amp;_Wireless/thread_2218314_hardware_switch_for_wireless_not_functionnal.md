---
title: "hardware switch for wireless not functionnal"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by quentin6 on 2014-04-20
Hello,

This is NOT a "wireless disable by hardware switch" issue :).

I just installed ubuntu 14.04, all is nearly functionnal and i really love that OS. Though, i encounter the following problem :

The hardware switch for wireless network is not working on this version. It used to be functionnal on lubuntu 12.04. It basically does nothing, while it should hardware-disable the wifi/bluetooth. The "software" switch (right click on the icon, disable networking) is working though. The main problem is that the "software" switch-off of the wireless card does not seem to improve battery duration, and you may think of it as a detail, but the battery life is an important issue for me.

To be concise : is there a way to hardware-disable the wireless card that i don't know ? if so, is there a way to fix the hardware switch, since it is much more convenient ? 

My config : 
- HP elitebook 9470m 
- wireless card : Centrino Advanced-N 6235 (according to lshw -C network) 
- OS : ubuntu 14.04 64 bits 
- to be completed : i'll edit if further informations are needed

Much thanks for reading :) 
Quentin

---

### Post by praseodym on 2014-04-20
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of
```

lsmod
iwconfig
rfkill list
```
Any BIOS option to activate it?

---

### Post by quentin6 on 2014-04-20
Thanks for you amazingly fast answer,

The results of the commands you asked :
```

quentin@quentin-Laptop:~$ lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
nvram                  14411  0 
joydev                 17381  0 
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_idt      54645  1 
btusb                  32412  0 
rfcomm                 69160  12 
bnep                   19624  2 
bluetooth             395423  22 bnep,btusb,rfcomm
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
arc4                   12608  2 
iwldvm                232285  0 
mac80211              626584  1 iwldvm
intel_rapl             18773  0 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
kvm                   451519  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_hda_intel          52355  1 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
aesni_intel            55624  2 
snd_hwdep              13602  1 snd_hda_codec
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse               101945  0 
serio_raw              13462  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  13 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
iwlwifi               169932  1 iwldvm
i915                  783483  2 
lpc_ich                21080  0 
cfg80211              490477  3 iwlwifi,mac80211,iwldvm
drm_kms_helper         52758  1 i915
soundcore              12680  1 snd
drm                   302631  3 i915,drm_kms_helper
mei_me                 18627  0 
i2c_algo_bit           13413  1 i915
mei                    82274  1 mei_me
wmi                    19177  1 hp_wmi
tpm_infineon           17372  0 
hp_accel               26012  0 
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
video                  19421  1 i915
mac_hid                13205  0 
coretemp               13435  0 
lp                     17759  0 
parport                42348  1 lp
ahci                   25819  1 
e1000e                254433  0 
libahci                32168  1 ahci
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
ptp                    18933  1 e1000e
pps_core               19382  1 ptp

quentin@quentin-Laptop:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Livebox-3970"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:33:8E:D2:AD:B3   
          Bit Rate=39 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:102  Invalid misc:23   Missed beacon:0

quentin@quentin-Laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

 as for the bios, whith my previous linux, all used to work correctly, and with the same bios settings, the switch does not function with ubuntu 14.04. Just to try, i did reset the BIOS to the original state, and the switch still works fine with windows 7 (dual boot), but still doesn't work with ubuntu 14.04. The wireless devices are correctly activeted as far as I know, so i don't think there is a problem there, but if you need a check, just tell me what to do :)

---

### Post by praseodym on 2014-04-20
Wireless does not seem to be "blocked". What hardware is it?
```

lspci -nnk | grep -iA2 net
dmesg | grep iwl
```
The card is on and seems to run, but the power management is "on", deactivate it via:
```

sudo iwconfig wlan0 power off
```

> ```
wlan0     IEEE 802.11abgn  ESSID:"Livebox-3970"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:33:8E:D2:AD:B3   
          Bit Rate=39 Mb/s   [COLOR="#FF0000"]Tx-Power=15 dBm [/COLOR]  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:[COLOR="#FF0000"]on[/COLOR]
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:102  Invalid misc:23   Missed beacon:0
```

---

### Post by quentin6 on 2014-04-20
> Wireless does not seem to be "blocked". What hardware is it?
I'm quite not sure I understand the question. The thing i'm talking about is a hardware switch to turn the wireless card on and off. I actually can turn the wifi on and of via the software button in the system tray. I also found out that the battery duration does not change a lot wether the wifi if disabled or not, so i thought that hardware button actually "disabled" the wireless card whereas the icon in the system tray only shut down the acces to the wifi. Is it wrong ? 
If it is not, i am actually looking for a way to disable the wireless card similar the the "hardware button" way, for better power saving. And if it's possible, tu fix the button so that he acts like he did in windows 7, or lubuntu 12.04.
if it's wrong, sorry for my ignorance.

```
sudo iwconfig wlan0 power off
```
This doesn't affect the behavior of the button, but power management for the card is now off

And this is the output of the commands :
```
quentin@quentin-Laptop:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:18df]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
	Kernel driver in use: iwlwifi
quentin@quentin-Laptop:~$ dmesg | grep iwl
[    9.510574] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    9.510660] iwlwifi 0000:03:00.0: irq 47 for MSI/MSI-X
[    9.513896] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    9.548841] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.548846] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.548848] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.548852] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[    9.548979] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    9.581506] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.912149] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   10.919216] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[   11.190901] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.197538] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 1406.136018] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1406.142705] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
```

---

### Post by praseodym on 2014-04-20
You could unload the driver on the fly

```
sudo modprobe -rfv iwlwifi
```

Reloading:
```

sudo modprobe -v iwlwifi
```

---

### Post by grahammechanical on 2014-04-20
> [COLOR=#000000]is there a way to hardware-disable the wireless card that i don't know ?[/COLOR]

Short of opening the machine's case and pulling out the card, how can any of us know the answer to that? Turning off WiFi through the OS is supposed to do more than breaking the wireless connection.

This explains what the software method is trying to do.

[http://wireless.kernel.org/en/users/Documentation/rfkill](http://wireless.kernel.org/en/users/Documentation/rfkill)

> [COLOR=#000000][FONT=Arial]the Linux kernel also exposes software rfkill capabilities that allows userspace to mimic a hardware rfkill event and turn on or off RF.[/FONT][/COLOR]

Why anyone would want to disable WiFi at startup I do not know but this post does introduce us to the power of ifconfig

[http://www.upubuntu.com/2012/01/how-to-disable-your-network-adapter.html](http://www.upubuntu.com/2012/01/how-to-disable-your-network-adapter.html)

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

I suspect that the Network manager disable wireless option just runs the first command and that the disable networking option runs a combination of ifconfig eth0 down and ifconfig wlan0 down. Or may be Network manger is using a combination RFKILL instructions.

It should have an effect on power consumption.

Regards.

---

### Post by quentin6 on 2014-04-20
Ok i'll take some time to look a that. Thank you very much for your answers :)

---

