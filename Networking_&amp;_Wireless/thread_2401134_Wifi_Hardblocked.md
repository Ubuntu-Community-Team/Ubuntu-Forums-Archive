---
title: "Wifi Hardblocked"
date: 2018-09-13
forum: Networking &amp; Wireless
---

### Post by gobbie2 on 2018-09-13
I have installed Ubuntu 18.04.1 LTS on a Toshiba Qosmio laptop.

My issue is that my wifi adapter is blocked

it is showing a hard block on phy0 Wireless LAN

lspci -nnk | grep 0280 -A3

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

rfkill list all

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by wildmanne39 on 2018-09-13
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by yetimon_64 on 2018-09-13
> **gobbie2 said:**
> I have installed Ubuntu 18.04.1 LTS on a Toshiba Qosmio laptop.

My issue is that my wifi adapter is blocked

...

Having had an intel wireless hard blocked on a previous laptop myself many years ago, a hardware switch on the side of your laptop may need resetting.

Sometimes there may be a slider switch usually on the very edge of the laptop somewhere that needs resetting.

I am not familiar with the layout of Toshiba laptops, here is a link that may help you find it (either a switch or by using the "Fn" keys etc)... [[COLOR=#0000ff]--link--[/COLOR]]("https://smallbusiness.chron.com/locate-wireless-connection-switch-toshiba-laptop-52136.html")

---

### Post by gobbie2 on 2018-09-14
Been there done that and no, not the answer.

:)

Thank-you anyway.

There is a bug I have been through several processes, just cannot seem to get this bug cleared.

---

### Post by gobbie2 on 2018-09-14
I might add I am setup with desktop and a dual boot situation :)

Here is someone else with the SAME issue and they found a resolution.

I am not skilled enough to determine which drivers I might need if that is the case.

[https://ubuntuforums.org/showthread.php?t=2353227](https://ubuntuforums.org/showthread.php?t=2353227)

I tried to reverse engineer the solution, however there is no wireless driver which came up

mark@mark-Qosmio-X770:~$ lsmod  | grep -e toshiba -e wmi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    81920  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
toshiba_acpi           45056  0
sparse_keymap          16384  1 toshiba_acpi
industrialio           69632  1 toshiba_acpi
toshiba_haps           16384  0
mxm_wmi                16384  1 nouveau
video                  45056  3 toshiba_acpi,nouveau,i915
wmi                    24576  3 toshiba_acpi,mxm_wmi,nouveau

then I tried using the name of the driver INTEL

  mark@mark-Qosmio-X770:~$ lsmod  | grep -e intel -e wmi
intel_rapl             20480  0
intel_powerclamp       16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
ghash_clmulni_intel    16384  0
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
aesni_intel           188416  2
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
snd_rawmidi            32768  1 snd_seq_midi
intel_rapl_perf        16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
btintel                16384  1 btusb
bluetooth             548864  43 btrtl,btintel,bnep,btbcm,rfcomm,btusb
snd                    81920  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
mxm_wmi                16384  1 nouveau
wmi                    24576  3 toshiba_acpi,mxm_wmi,nouveau
  

As you can see bluetooth is no issue, only wifi

I believe the intel board is both bluetooth & wifi.

---

### Post by gobbie2 on 2018-09-14
mark@mark-Qosmio-X770:~$ iwconfig
enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
         
lo        no wireless extensions.

---

### Post by chili555 on 2018-09-14
If you have tried the wireless function key and there is no change in the hard block, then we suspect that the helper module that translates key presses into action ("Turn on the wireless radio, please, Mr. Kernel.") is not operating correctly. We see the module here:> mark@mark-Qosmio-X770:~$ lsmod | grep -e toshiba -e wmi
snd_rawmidi 32768 1 snd_seq_midi
snd_seq_device 16384 3 snd_seq,snd_rawmidi,snd_seq_midi
snd 81920 23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_ timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec _generic,snd_seq_device,snd_hda_codec_realtek,snd_ pcm
[COLOR="#FF0000"]toshiba_acpi[/COLOR] 45056 0
sparse_keymap 16384 1 toshiba_acpi
industrialio 69632 1 toshiba_acpi
toshiba_haps 16384 0
mxm_wmi 16384 1 nouveau
video 45056 3 toshiba_acpi,nouveau,i915
wmi 24576 3 toshiba_acpi,mxm_wmi,nouveauThe first thing we can try is to remove the module altogether:```
sudo modprobe -r toshiba_acpi
sudo rfkill unblock all
rfkill list all
```Is there any improvement? If so, we'll blacklist the module and you will be all set.

If not, let's try the one and only parameter available. Please check:```
modinfo toshiba_acpi
```We see:```
filename:       /lib/modules/4.15.0-34-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
license:        GPL
description:    Toshiba Laptop ACPI Extras Driver
author:         John Belmonte
srcversion:     3FF6AAEF15ED90399B65B47
<snip>
depends:        industrialio,video,sparse-keymap,wmi
retpoline:      Y
intree:         Y
name:           toshiba_acpi
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
[COLOR="#FF0000"]parm:           disable_hotkeys:Disables the hotkeys activation (bool)[/COLOR]

```Since, after the first step above, the module is now unloaded, we'll reload it with the parameter:```
sudo modprobe toshiba_acpi disable_hotkeys=Y
sudo rfkill unblock all
rfkill list all
```Any improvement?

---

### Post by gobbie2 on 2018-09-14
No improvements with any of the commands

```
mark@mark-Qosmio-X770:~$ sudomodprobe -r toshiba_acpi
[sudo] password for mark: 
mark@mark-Qosmio-X770:~$ sudo rfkill unblock all
mark@mark-Qosmio-X770:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
mark@mark-Qosmio-X770:~$ modinfo toshiba_acpi
filename:      /lib/modules/4.15.0-34-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
license:        GPL
description:    Toshiba Laptop ACPI Extras Driver
author:         John Belmonte
srcversion:     3FF6AAEF15ED90399B65B47
alias:          acpi*:TOS1900:*
alias:          acpi*:TOS6208:*
alias:          acpi*:TOS6207:*
alias:          acpi*:TOS6200:*
depends:       industrialio,video,sparse-keymap,wmi
retpoline:      Y
intree:         Y
name:           toshiba_acpi
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:          disable_hotkeys:Disables the hotkeys activation (bool)
mark@mark-Qosmio-X770:~$ 
mark@mark-Qosmio-X770:~$ 
mark@mark-Qosmio-X770:~$ sudo modprobe toshiba_acpi disable_hotkeys=Y
mark@mark-Qosmio-X770:~$ sudo rfkill unblock all
mark@mark-Qosmio-X770:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
mark@mark-Qosmio-X770:~$
```

---

### Post by gobbie2 on 2018-09-14
I might add that when I use the hotkey I see airplane mode.  

Under the power the Bluetooth is turned on
The wifi will not turn on

---

### Post by gobbie2 on 2018-09-14
The hotkeys for the wifi no longer trigger airplane mode :)

---

### Post by wildmanne39 on 2018-09-14
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by gobbie2 on 2018-09-14
I performed a reboot and now I can no longer toggel the wifi
The dropdown had an option to turn on wifi as it was set to off now that entire on/off no longer exists on the drop down menu.
Only 2 options instead of the 3

---

### Post by gobbie2 on 2018-09-14
[LEFT][COLOR=#222222][FONT=Verdana]I performed a reboot and now I can no longer toggel the wifi[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana] The dropdown had an option to turn on wifi as it was set to off now that entire on/off no longer exists on the drop down menu.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana] Only 2 options instead of the 3[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I enabled the hotkey and now I am able to turn on and off airplane mode.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]The wifi is a touch button and that will glow when I am booting and I can toggle that off and on until the system boots at which time it is off and stays off.[/FONT][/COLOR][/LEFT]

---

### Post by gobbie2 on 2018-09-14
Okay, no idea what I did no more issued commands.

I rebooted and I did notice that if I hit that button for wifi (the lighted one) it turned the wifi on and off.

I am now up and running 100%

Very interesting!!!

---

### Post by chili555 on 2018-09-14
We're glad it's working by whatever means! Have fun!

---

