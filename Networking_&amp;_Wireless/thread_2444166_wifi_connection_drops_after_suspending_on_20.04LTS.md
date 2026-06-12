---
title: "wifi connection drops after suspending on 20.04LTS"
date: 2020-05-26
forum: Networking &amp; Wireless
---

### Post by rlothbrock on 2020-05-26
Hi.

Right now I'm using Ubuntu 20.04 LTS on a DELL Inspiron laptop, but I used to have the same issue when using 18.04 LTS on the same machine.
The fact is that anytime my machine gets suspended, wifi connection gets lost, and the only way to bring it back it's by rebooting my machine

I've made a huge search before posting this thread. I've also tried many of the solutions provided on the 'solved' ones, even those from this forum.
None of them has worked for me so far.
So, I'll really appreciate any solution that you can give me. 

I can handle the terminal, but I'm not a skilled user, so I could appreciate if you can explain your solution details, so I can understand.

Thanks a lot.

P.S. I've also searched on a Dell community forum, and they have the same problem on this model.

---

### Post by CelticWarrior on 2020-05-26
Welcome.

Solutions are hardware specific. The fact that you didn't post anything that identifies your WiFi chipset suggests you are unaware of the aforementioned specificity and whatever you've tried so far is likely not applicable, does nothing or even makes things worse.

Please read this sticky and follow instructions there to run a script that will gather all the information required: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by rlothbrock on 2020-05-27
thanks dude for your reply, I've run the script as you told me and this is what I've got.       **[https://paste.ubuntu.com/p/vYZvx3tt6x/](https://paste.ubuntu.com/p/vYZvx3tt6x/)**

I'm sending the complete log, because as you said I'm not aware of what you could need for finding a solution.

It has been a really helpfull reply....


and this is also a small resume...
```


########## wireless info START ##########

Report from: 27 May 2020 13:36 EDT -0400

Booted last: 27 May 2020 00:00 EDT -0400

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.4.0-31-generic #35-Ubuntu SMP Thu May 7 20:20:34 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020e]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e005 Qualcomm Atheros Communications 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0bda:5689 Realtek Semiconductor Corp. Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

dell_laptop            24576  0
ledtrig_audio          16384  4 snd_hda_codec_generic,snd_hda_codec_realtek,snd_sof,dell_laptop
ath3k                  24576  0
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k_common,ath9k
ath                    36864  3 ath9k_common,ath9k,ath9k_hw
mac80211              843776  1 ath9k
cfg80211              704512  4 ath9k_common,ath9k,ath,mac80211
libarc4                16384  1 mac80211
bluetooth             581632  32 btrtl,btintel,btbcm,bnep,ath3k,btusb,rfcomm
dell_wmi               20480  0
dell_smbios            28672  2 dell_wmi,dell_laptop
wmi_bmof               16384  0
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
sparse_keymap          16384  2 intel_hid,dell_wmi
wmi                    32768  4 dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
video                  49152  4 dell_wmi,dell_laptop,int3406_thermal,i915

```

---

