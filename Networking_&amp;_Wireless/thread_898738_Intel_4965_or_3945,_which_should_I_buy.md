---
title: "Intel 4965 or 3945, which should I buy?"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by Zorael on 2008-08-23
I have an Advent 4211 (rebranded MSI Wind) with a bothersome Realtek 8187SE card that I'm looking to replace. I have a 3945 card on my other laptop which I know works (after compiling new drivers and/or passing options to the iwl3945 module), but now that I suddenly have a choice of what to get to my new system I'm exploring my options.

The 4965 supports draft-N which is a bonus, though it doesn't seem to support B? Does N work at all in linux yet, with the iwlwifi drivers?

The wiki page listing supported wireless cards states that 4965s work out-of-the-box, but at the same time I see that some ended up having to ndiswrap the windows driver to get theirs to function. I'm confused.

Should I just go with the 3945 or get the 4965 for the draft-N?

---

### Post by oboedad55 on 2009-08-19
> **Zorael said:**
> I have an Advent 4211 (rebranded MSI Wind) with a bothersome Realtek 8187SE card that I'm looking to replace. I have a 3945 card on my other laptop which I know works (after compiling new drivers and/or passing options to the iwl3945 module), but now that I suddenly have a choice of what to get to my new system I'm exploring my options.

The 4965 supports draft-N which is a bonus, though it doesn't seem to support B? Does N work at all in linux yet, with the iwlwifi drivers?

The wiki page listing supported wireless cards states that 4965s work out-of-the-box, but at the same time I see that some ended up having to ndiswrap the windows driver to get theirs to function. I'm confused.

Should I just go with the 3945 or get the 4965 for the draft-N?

What did you do to get the 3945 to work? I've got one that works under windows and worked under Linux but no longer connects!

Thanks,
Jono

---

### Post by Zorael on 2009-08-20
> **oboedad55 said:**
> What did you do to get the 3945 to work? I've got one that works under windows and worked under Linux but no longer connects!

Thanks,
Jono
By trial and error, I found that I need to disable hardware scanning for it to work.
```
filename:       /lib/modules/2.6.30-10-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.2.26ks
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     E105E33A62BFADD9EA687DA
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        mac80211,iwlcore,led-class,cfg80211
vermagic:       2.6.30-10-generic SMP mod_unload modversions 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           debug:debug output mask (uint)
parm:           **disable_hw_scan**:disable hardware scanning (default **0**) (int)
parm:           queues_num:number of hw queues. (int)
parm:           fw_restart3945:restart firmware in case of error (int)
```
These are the available options you can pass to the iwl3945 driver, copy/pasted from the output of **modinfo iwl3945**.

To get an option toggled on a persistent basis (as opposed to manually specifying it when doing '**modprobe iwl3945 *option=value***'), place a file in **/etc/modprobe.d/** and have it end with a **.conf** extension, such as **/etc/modprobe.d/iwl3945.conf** (or **options.conf** or **fluffybunny.conf**). Paste the following into it.
```
options iwl3945 **disable_hw_scan**=**1**
```
After saving that file, try doing a scan for wireless networks. If it's not done with sudo, it won't perform a new scan (only list the results from the last one).
```
$ sudo iwlist scan
```
As we've not applied our option change yet, it should still not find any. Then reload the driver and try it again.
```
$ sudo modprobe -r iwl3945
$ sudo modprobe iwl3945
$ sudo iwlist scan
```
Repeat the last command (the actual scanning) once or twice if it still doesn't list any networks - perhaps it missed the ssid broadcast.
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:EF:06:92
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=58/70  Signal level=-52 dBm
                    Encryption key:off
                    ESSID:"baracken"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002664089188
                    Extra: **Last beacon: 32ms ago**
                    IE: Unknown: 000862617261636B656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020010

pan0      Interface doesn't support scanning.
```
If it's listed, rejoice, try connecting.

Since you created a file containing the options, the change should persist upon reboot.

---

