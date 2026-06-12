---
title: "DIY Intel iwl 3945 4965 iwl 5000 iwl 5100 how to get internet"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Tracy177 on 2010-09-02
some people use ndiswrapper or some other things but there is an easy way to get iwl work my does without any problems 


i have iwl 4965 iwl5000 and iwl 5100

this are steps for guys who got no matter what kernel and everything they want is to connect without probs to the internet i tested it on 2.6.32 2.6.34 and 2.6.35 

Linux matrix 2.6.35-19-generic #25~lucid1-Ubuntu SMP Wed Aug 25 04:24:28 UTC 2010 i686 GNU/Linux

if youre already trying to or installed ndiswrapper or something better remove it if u can.

than go to [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads) get firmware for your iwl card unzip it install or put it in your firmwares 

than go to [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

get the latest driver there on this web drivers are updated daily as i said get the latest one.

also each driver from this web page support many different devices rt zd iwl ath etc and bluetooth

donwnload it than cd to compat make sudo make install

after u install it sudo make wlunload sudo make btunload 

after that modprobe iwlagn 

and your card will work without any problems 

ps people who got laptops should remember there is a button to switch network on and off  so switch it on .

and always u can use modinfo iwlagn 

my says 

modinfo iwlagn
filename:       /lib/modules/2.6.35-19-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-1000-3.ucode
srcversion:     8BEA3A15EF75E9324B7D3B9
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005311bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005321bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005301bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005207bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005206bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005201bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005107bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005125bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005115bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005105bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001207bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211,cfg80211
vermagic:       2.6.35-19-generic SMP mod_unload modversions 686 
parm:           swcrypto50:using crypto in software (default 0 [hardware]) (deprecated) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num50:number of hw queues in 50xx series (deprecated) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable50:disable 50XX 11n functionality (deprecated) (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (deprecated) (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart50:restart firmware in case of error (deprecated) (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_announce:Enable BT channel announcement mode (default: enable) (bool)




good luck

---

### Post by Sonic Reducer on 2010-09-07
is this guide for Lucid? i installed wicd and every time i try to connect to my AP it goes through all the steps, all the way up to "done connecting" then it says not connected.

i have an ipw3945abg wireless chip, running a fresh install of lucid.

```
ryan@ryan-laptop:~$ lsmod | grep 3945
iwl3945                70531  0 
iwlcore               116521  1 iwl3945
mac80211              225267  2 iwl3945,iwlcore
cfg80211              144778  3 iwl3945,iwlcore,mac80211
compat_firmware_class     6554  1 iwl3945
```

ps you should format your text a bit to make it easier to read, it's hard to tell what is a terminal command, what is an instruction, and what is bad grammar/typo.

other than that thank you for taking the time to write out such a long guide, and i hope it will let me and other users use their wifi

---

### Post by anewguy on 2010-09-07
From the sounds of this, I imagine it will have to be re-done with each kernel update.  Keep that in mind.

---

### Post by Sonic Reducer on 2010-09-07
> **anewguy said:**
> From the sounds of this, I imagine it will have to be re-done with each kernel update.  Keep that in mind.

thats right, uCode is inserted into the kernel right? so if i update the kernel i'll have to reinsert it into the new kernel.

do you know how to get my wifi working on Lucid?

---

