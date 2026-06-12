---
title: "Connected to Wifi Network but Internet not working"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by ataberkbunyat on 2014-02-02
Hey guys total Linux newbie here. Decided to try out Linux after my hate of Windows 8/8.1 on my Acer Aspire M5-M83P.
I tried to download 12.04 but my wireless card was not even recognized with it when I installed it 
over Windows 8.1. So in desperation I downloaded a 32 bit version of 13.10 and everything was 
working fine during installation but now I cant even access the internet. Thank you in advance.

---

### Post by praseodym on 2014-02-02
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```Does LAN work?

---

### Post by ataberkbunyat on 2014-02-02
Here you go.
I cannot test LAN or just a direct plug due to my house not letting me. Only LAN worked in 12.04 when I tried to at a friends house.
```

ataberk@ataberk-Aspire-M5-583P:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 63)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4060]
    Kernel driver in use: iwlwifi
--
05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: r8169

ataberk@ataberk-Aspire-M5-583P:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 018: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 017: ID 04f3:0085 Elan Microelectronics Corp. 
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 002: ID 064e:e330 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ataberk@ataberk-Aspire-M5-583P:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48294  1 
hid_multitouch         17191  0 
usbhid                 47361  0 
hid                    87370  2 hid_multitouch,usbhid
vesafb                 13500  1 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
btusb                  23443  0 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  12 
bnep                   18959  2 
bluetooth             323656  22 bnep,btusb,rfcomm
x86_pkg_temp_thermal    13810  0 
joydev                 17097  0 
coretemp               13195  0 
kvm_intel             128218  0 
arc4                   12536  2 
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
aesni_intel            18156  1 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
iwlmvm                149128  0 
mac80211              517444  1 iwlmvm
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
snd_hda_codec_realtek    45592  1 
snd_hda_codec_hdmi     40373  1 
snd_hda_intel          42658  5 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
microcode              18830  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
psmouse                90642  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13189  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
rtsx_pci_ms            17807  0 
snd_timer              24447  2 snd_pcm,snd_seq
iwlwifi               143736  1 iwlmvm
memstick               16008  1 rtsx_pci_ms
i915                  594380  2 
lpc_ich                16864  0 
cfg80211              401762  3 iwlwifi,mac80211,iwlmvm
snd                    60790  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         46867  1 i915
mei_me                 13933  0 
drm                   242400  2 i915,drm_kms_helper
mei                    66411  1 mei_me
video                  18777  2 i915,acer_wmi
wmi                    18590  1 acer_wmi
i2c_algo_bit           13197  1 i915
intel_smartconnect     12610  0 
soundcore              12600  1 snd
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         22898  0 
r8169                  61562  0 
ahci                   25579  2 
mii                    13654  1 r8169
rtsx_pci               43458  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                26554  1 ahci

ataberk@ataberk-Aspire-M5-583P:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"capulcu"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:81:D8:D5:C5:8C   
          Bit Rate=1 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

ataberk@ataberk-Aspire-M5-583P:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

---

### Post by praseodym on 2014-02-03
Deactivate the N-mode of the driver (bug) and the power management:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo iwconfig wlan0 power off
```
Reboot and check

```
dmesg | grep iwl
```

---

### Post by ataberkbunyat on 2014-02-03
Here is the code that it spurted out. Also update. Wifi works but not optimally when I turn networking on and off. Its a tad and slow and it took a while fo the first page to actually load but it seems ok ish now.

```

ataberk@ataberk-Aspire-M5-583P:~$ dmesg | grep iwl
[   12.254117] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.254173] iwlwifi 0000:04:00.0: irq 64 for MSI/MSI-X
[   12.267485] Modules linked in: snd_hda_intel(+) snd_seq snd_hda_codec iwlwifi psmouse snd_hwdep rtsx_pci_ms serio_raw cfg80211 snd_pcm snd_seq_device memstick mei_me i915 lpc_ich snd_page_alloc mei snd_timer snd drm_kms_helper wmi drm video intel_smartconnect soundcore mac_hid i2c_algo_bit lp parport rtsx_pci_sdmmc ahci r8169 rtsx_pci libahci mii
[   12.473132] iwlwifi 0000:04:00.0: loaded firmware version 22.0.7.0 op_mode iwlmvm
[   12.500623] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[   12.500672] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   12.500813] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   12.697499] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   15.385725] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   15.385869] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[   21.831684] Modules linked in: vesafb uvcvideo hid_multitouch videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev parport_pc ppdev btusb bnep rfcomm bluetooth binfmt_misc x86_pkg_temp_thermal coretemp kvm_intel kvm crc32_pclmul aesni_intel aes_i586 xts lrw gf128mul ablk_helper cryptd joydev arc4 iwlmvm mac80211 acer_wmi sparse_keymap snd_hda_codec_hdmi snd_seq_midi snd_hda_codec_realtek snd_seq_midi_event microcode snd_rawmidi snd_hda_intel snd_seq snd_hda_codec iwlwifi psmouse snd_hwdep rtsx_pci_ms serio_raw cfg80211 snd_pcm snd_seq_device memstick mei_me i915 lpc_ich snd_page_alloc mei snd_timer snd drm_kms_helper wmi drm video intel_smartconnect soundcore mac_hid i2c_algo_bit lp parport rtsx_pci_sdmmc ahci r8169 rtsx_pci libahci mii
[   22.251408] Modules linked in: vesafb uvcvideo hid_multitouch videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev parport_pc ppdev btusb bnep rfcomm bluetooth binfmt_misc x86_pkg_temp_thermal coretemp kvm_intel kvm crc32_pclmul aesni_intel aes_i586 xts lrw gf128mul ablk_helper cryptd joydev arc4 iwlmvm mac80211 acer_wmi sparse_keymap snd_hda_codec_hdmi snd_seq_midi snd_hda_codec_realtek snd_seq_midi_event microcode snd_rawmidi snd_hda_intel snd_seq snd_hda_codec iwlwifi psmouse snd_hwdep rtsx_pci_ms serio_raw cfg80211 snd_pcm snd_seq_device memstick mei_me i915 lpc_ich snd_page_alloc mei snd_timer snd drm_kms_helper wmi drm video intel_smartconnect soundcore mac_hid i2c_algo_bit lp parport rtsx_pci_sdmmc ahci r8169 rtsx_pci libahci mii
[   28.392097] Modules linked in: vesafb uvcvideo hid_multitouch videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev parport_pc ppdev btusb bnep rfcomm bluetooth binfmt_misc x86_pkg_temp_thermal coretemp kvm_intel kvm crc32_pclmul aesni_intel aes_i586 xts lrw gf128mul ablk_helper cryptd joydev arc4 iwlmvm mac80211 acer_wmi sparse_keymap snd_hda_codec_hdmi snd_seq_midi snd_hda_codec_realtek snd_seq_midi_event microcode snd_rawmidi snd_hda_intel snd_seq snd_hda_codec iwlwifi psmouse snd_hwdep rtsx_pci_ms serio_raw cfg80211 snd_pcm snd_seq_device memstick mei_me i915 lpc_ich snd_page_alloc mei snd_timer snd drm_kms_helper wmi drm video intel_smartconnect soundcore mac_hid i2c_algo_bit lp parport rtsx_pci_sdmmc ahci r8169 rtsx_pci libahci mii
[   30.011094] Modules linked in: vesafb uvcvideo hid_multitouch videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev parport_pc ppdev btusb bnep rfcomm bluetooth binfmt_misc x86_pkg_temp_thermal coretemp kvm_intel kvm crc32_pclmul aesni_intel aes_i586 xts lrw gf128mul ablk_helper cryptd joydev arc4 iwlmvm mac80211 acer_wmi sparse_keymap snd_hda_codec_hdmi snd_seq_midi snd_hda_codec_realtek snd_seq_midi_event microcode snd_rawmidi snd_hda_intel snd_seq snd_hda_codec iwlwifi psmouse snd_hwdep rtsx_pci_ms serio_raw cfg80211 snd_pcm snd_seq_device memstick mei_me i915 lpc_ich snd_page_alloc mei snd_timer snd drm_kms_helper wmi drm video intel_smartconnect soundcore mac_hid i2c_algo_bit lp parport rtsx_pci_sdmmc ahci r8169 rtsx_pci libahci mii
[   36.179703] Modules linked in: vesafb uvcvideo hid_multitouch videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev parport_pc ppdev btusb bnep rfcomm bluetooth binfmt_misc x86_pkg_temp_thermal coretemp kvm_intel kvm crc32_pclmul aesni_intel aes_i586 xts lrw gf128mul ablk_helper cryptd joydev arc4 iwlmvm mac80211 acer_wmi sparse_keymap snd_hda_codec_hdmi snd_seq_midi snd_hda_codec_realtek snd_seq_midi_event microcode snd_rawmidi snd_hda_intel snd_seq snd_hda_codec iwlwifi psmouse snd_hwdep rtsx_pci_ms serio_raw cfg80211 snd_pcm snd_seq_device memstick mei_me i915 lpc_ich snd_page_alloc mei snd_timer snd drm_kms_helper wmi drm video intel_smartconnect soundcore mac_hid i2c_algo_bit lp parport rtsx_pci_sdmmc ahci r8169 rtsx_pci libahci mii
ataberk@ataberk-Aspire-M5-583P:~$ 


```

---

### Post by varunendra on 2014-02-04
Does the "Power Management" stay off? Keep an eye on the output of -
```
iwconfig
```

If it seems to be fluctuating (on and off at different times), try creating a blank file in /etc/pm/power.d directory to disable the default wireless power management script -
```
sudo touch /etc/pm/power.d/wireless
```
You may have to log off/log on (or reboot) for the change to take effect.

I think we would also like to see your current driver parameter that are in effect. Please post the output of -
```
grep -R [[:alnum:]] /sys/module/iwlwifi/parameters
```

---

### Post by ataberkbunyat on 2014-02-04
```

/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0

```
Here it is. I am posting this from the laptop it worked fine when I turned it on with no problems. Going to reboot now due to the other line of code.

---

### Post by ataberkbunyat on 2014-02-04
```

ataberk@ataberk-Aspire-M5-583P:~$ grep -R [[:alnum:]] /sys/module/iwlwifi/parameters
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0

```

Here it is after a reboot. Still had to wait a little bit for the page the load though. Also the Software center worked fine when webpages would not load.

---

### Post by varunendra on 2014-02-04
> **ataberkbunyat said:**
> ```

/sys/module/iwlwifi/parameters/**11n_disable:[COLOR="#FF0000"]0[/COLOR]**

```

> **ataberkbunyat said:**
> ```
/sys/module/iwlwifi/parameters/**11n_disable:[COLOR="#FF0000"]0[/COLOR]**
```

Clearly, the code (echo "options iwlwifi....") proposed by praseodym is not in effect. Did you run them correctly?
If yes, there might have been a typo. Please show us the output of -
```
cat /etc/modprobe.d/iwlwifi.conf
```

And the blank file to disable the default power management was a trick that should be ONLY used if the normal method (the one praseodym suggested) fails to keep it off.

So.. was the Power Management fluctuating between on/off by itself? Or turning On again by itself? If not, that "blank file" trick was unnecessary and may even worsen the performance in some cases.

---

### Post by ataberkbunyat on 2014-02-04
Pretty sure the blank file screwed up everything. The echo options iwlwifi was typed correctly as well. How can I delete the blank file? Thanks in advance.

---

### Post by brokenhachi on 2014-02-04
you can just change "touch" in the previous command to "rm"

can you also show the output of *route -n*. Do you know the router ip and can you ping it? Do you have no internet access or just no dns access? Can you try *ping 4.2.2.2*?

---

### Post by varunendra on 2014-02-05
> **ataberkbunyat said:**
> Pretty sure the blank file screwed up everything. The echo options iwlwifi was typed correctly as well. How can I delete the blank file? Thanks in advance.

By replacing "touch" with "rm" as brokenhachi told.

But that file or its result can't affect the effect of the iwlwifi.conf file if its contents were correct. Please post back the output of the 'cat..' command I asked in my previous post.

And maybe better if we also take a look at a detailed report at this point. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by ataberkbunyat on 2014-02-05
```

ataberk@ataberk-Aspire-M5-583P:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disables=1


```
Here it is, the output and the attached file. It actually connected with no hassle for once. 



```
#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: anewguy, chili555, llua
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

FILEBASE="wireless-info"
MODMATCHES="(air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|8192cu|8192du|rt5|rt6|rt7|rtl|r818|r871|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"
exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCould not write target file \"$FILEBASE.txt\", aborting.\n\n"
    exit 1
fi
printf "\n*************** info trace ***************\n"
printf "\n***** uname -a *****\n\n"
uname -a
printf "\n***** lsb_release *****\n\n"
lsb_release -idrc
printf "\n***** lspci *****\n\n"
lspci -nnk | grep -iA2 net
printf "\n***** lsusb *****\n\n"
lsusb
printf "\n***** PCMCIA Card Info *****\n\n"
pccardctl info
printf "\n***** iwconfig *****\n\n"
iwconfig
printf "\n***** rfkill *****\n\n"
rfkill list all
printf "\n***** lsmod *****\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"
printf "\n***** nm-tool *****\n"
nm-tool
printf "\n***** NetworkManager.state *****\n"
cat /var/lib/NetworkManager/NetworkManager.state
printf "\n***** NetworkManager.conf *****\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi
printf "\n***** interfaces *****\n\n"
cat /etc/network/interfaces | sed -r 's/wpa-psk [[:graph:]]+/wpa-psk <WPA key removed>/'
printf "\n***** iwlist *****\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi
printf "\n***** resolv.conf *****\n\n"
grep -v '^#' /etc/resolv.conf
printf "\n***** blacklist *****\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
    BLACKLIST=$(grep '^blacklist' $CONFFILE)
    if [ -n "$BLACKLIST" ]; then
        printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
    fi
    fi
done
printf "\n***** modinfo *****\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done
printf "\n***** udev rules *****\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
printf "\n***** dmesg *****\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"
printf "\n****************** done ******************\n\n"
exec 1>&3 3>&-
exec 2>&4 4>&-
sed -r -i 's/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<MAC address removed>/' $FILEBASE.txt
if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm -f $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi


```

Thank you again guys for showing a newbie the ropes. At least I'm learning some commands while doing this.

---

### Post by praseodym on 2014-02-05
Typo:

> ```
options iwlwifi 11n_disable[COLOR="#FF0000"]s[/COLOR]=1
```
Correction:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by ataberkbunyat on 2014-02-05
Ah that figures. Going to reboot and see how it works out now.

EDIT: Works now. Thank you again.

---

