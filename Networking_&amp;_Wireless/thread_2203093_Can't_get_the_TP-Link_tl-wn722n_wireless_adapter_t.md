---
title: "Can't get the TP-Link tl-wn722n wireless adapter to work"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Gildon on 2014-02-01
I have looked around on numerous posts trying to get this adapter to work. Apparently, the 3.1 linux kernal has troubles with this adapter and so I have to install the firmware and compat-wireless drivers (described here: [http://askubuntu.com/questions/98844/how-do-i-get-a-tp-link-tl-wn722n-wireless-card-working](http://askubuntu.com/questions/98844/how-do-i-get-a-tp-link-tl-wn722n-wireless-card-working)). At this point, I think I really just need somebody I can talk to back and forth to try to figure this out. I should have the firmware in place because I downloaded the new 1.3 version of it but I can't get the compat-wireless drivers installed because I don't have the make command. Any help would be greatly appreciated. Thanks.

---

### Post by praseodym on 2014-02-01
Please show the outputs of:
```

lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
ifconfig -a
```

---

### Post by Gildon on 2014-02-01
kyle@GamingPC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 002: ID 045e:0291 Microsoft Corp. Xbox 360 Wireless Receiver for Windows
Bus 003 Device 003: ID 1532:0015 Razer USA, Ltd 
Bus 003 Device 004: ID 045e:0768 Microsoft Corp. Sidewinder X4
Bus 003 Device 007: ID 046d:0a1f Logitech, Inc. 
Bus 003 Device 011: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180113  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_usb_audio         122982  2 
snd_usbmidi_lib        29476  1 snd_usb_audio
ath9k_htc              92738  0 
mac80211              506862  1 ath9k_htc
psmouse                97519  0 
ath9k_common           14053  1 ath9k_htc
serio_raw              13211  0 
snd_hda_intel          33719  5 
ath9k_hw              411239  2 ath9k_htc,ath9k_common
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    24067  3 ath9k_htc,ath9k_common,ath9k_hw
snd_hwdep              17764  2 snd_usb_audio,snd_hda_codec
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
cfg80211              205774  3 ath9k_htc,mac80211,ath
snd_pcm                97275  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
joydev                 17693  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
xpad                   18179  0 
mac_hid                13253  0 
ff_memless             13097  1 xpad
snd                    79041  26 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
usbhid                 47238  0 
hid                    99636  1 usbhid
nouveau               775039  0 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   241971  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                13021  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19651  1 nouveau
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ iwconfig
lo        no wireless extensions.


kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ iwlist chan
lo        no frequency information.


kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ sudo iwlist scan
[sudo] password for kyle: 
lo        Interface doesn't support scanning.


kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ 
kyle@GamingPC:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10880 (10.8 KB)  TX bytes:10880 (10.8 KB)


kyle@GamingPC:~$

---

### Post by Gildon on 2014-02-01
Anybody know what to do with these results?

---

### Post by praseodym on 2014-02-01
Check:
```

echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
sudo iwconfig wlan0 power off
```

---

### Post by sam30 on 2014-02-01
I'm working on the same thing you are.

You have the same device that I do listed in lsusb: this is the thing in question
```
Bus 003 Device 011: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
```

I grepped the output of your lsmod for Atheros, and it is the same as mine, with no exceptions:
```
lombard@lombard-command:~$ lsmod | grep ath
ath9k_htc              85879  0 
ath9k_common           13619  1 ath9k_htc
ath9k_hw              429197  2 ath9k_common,ath9k_htc
ath                    19187  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              517444  3 b43,brcmsmac,ath9k_htc
cfg80211              401762  5 b43,ath,brcmsmac,mac80211,ath9k_htc
```

I believe ath9k_htc is the driver, so I would guess we're both good on that count. Is there a file called htc_9271.fw in your /lib/firmware/ directory? [This post ]("http://askubuntu.com/questions/98844/how-do-i-get-a-tp-link-tl-wn722n-wireless-card-working")says that both that firmware file and the driver are necessary to drive the TL-WN722N... If you don't have it already maybe dropping it in ([download here]("http://wireless.kernel.org/download/htc_fw/1.3/")) will work for you.

---

### Post by Gildon on 2014-02-01
Yes. I downloaded the firmware version 1.3 from [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/) and put it in my /lib/firmware. At this point, I'm just stuck at compiling compat-wireless. When I try to compile it using the make command I get:

kyle@GamingPC:~$ sudo su
[sudo] password for kyle: 
root@GamingPC:/home/kyle# cd
root@GamingPC:~# cd /home/kyle/Test/test
root@GamingPC:/home/kyle/Test/test# ./scripts/driver-select ath9k_htc
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: drivers/net/wireless/ath/Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/net/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@GamingPC:/home/kyle/Test/test# sudo make
/bin/sh: 1: [: -gt: argument expected
/bin/sh: 1: test: -ge: unexpected operator
make -C /lib/modules/3.2.0-52-generic/build M=/home/kyle/Test/test modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic'
  CC [M]  /home/kyle/Test/test/compat/main.o
In file included from include/linux/if_ether.h:133:0,
                 from include/linux/netdevice.h:29,
                 from /home/kyle/Test/test/include/linux/compat-2.6.29.h:5,
                 from /home/kyle/Test/test/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/skbuff.h: In function ‘nf_reset_trace’:
include/linux/skbuff.h:2372:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/skbuff.h:2372:15: error: missing binary operator before token "("
In file included from /home/kyle/Test/test/include/linux/compat-2.6.29.h:5:0,
                 from /home/kyle/Test/test/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/netdevice.h: At top level:
include/linux/netdevice.h:1150:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:1150:15: error: missing binary operator before token "("
include/linux/netdevice.h: In function ‘netdev_uses_dsa_tags’:
include/linux/netdevice.h:1418:9: error: ‘struct net_device’ has no member named ‘dsa_ptr’
include/linux/netdevice.h:1419:31: error: ‘struct net_device’ has no member named ‘dsa_ptr’
include/linux/netdevice.h: In function ‘netdev_uses_trailer_tags’:
include/linux/netdevice.h:1428:9: error: ‘struct net_device’ has no member named ‘dsa_ptr’
include/linux/netdevice.h:1429:35: error: ‘struct net_device’ has no member named ‘dsa_ptr’
make[3]: *** [/home/kyle/Test/test/compat/main.o] Error 1
make[2]: *** [/home/kyle/Test/test/compat] Error 2
make[1]: *** [_module_/home/kyle/Test/test] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic'
make: *** [modules] Error 2
root@GamingPC:/home/kyle/Test/test#

---

### Post by Gildon on 2014-02-01
When I run sudo iwconfig wlan0 power off, It says that there is no such device. After running ip link, it says:
l: lo: <LOOPBACK, UP, LOWER_UP> mtu 164365 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

---

### Post by sam30 on 2014-02-01
Yeah, I was trying to compile that driver as well and got the same types errors
```
include/linux/skbuff.h: In function &#8216;nf_reset_trace&#8217;:
include/linux/skbuff.h:2372:5: warning: "IS_ENABLED" is not defined [-Wundef]
```
...etc. But if you notice, they're more like syntax errors, which I wouldn't know what to do about in this case. What isn't it finding? The error messages don't say... 

Anyhow our lsmod output is showing the existance of some ath9k_htc which is the same thing that we're trying to build. I think building that thing is unnecessary. Anyone have thoughts on this?

---

