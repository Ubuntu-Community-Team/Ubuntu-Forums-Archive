---
title: "Intel network controller problems"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by cristina.morales4 on 2014-01-09
Hello I have a similar problem and I was trying this solution. Can you please help me!! 

modinfo rtl8192ce

```

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B41EC2D43683C181DF50FB6
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)



```

but nothing happens when I type this 

```

lsmod | grep rtl
or
dmesg | grep rtl

```

When I try this lspci -nn | grep 0280
```

lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Device [8086:08b1] (rev 63)

```
Also, form other solutions that I have seen that use commands that have wlan0, it dosen't work. 

```

iwconfig wlan0

wlan0 No such device

```

BTW, english is not my first language. Sorry for any errors... =]

---

### Post by varunendra on 2014-01-10
Welcome to the forums !

Your wireless device is different than the one discussed in this thread, so it should be discussed in a different thread of its own. I'd request a mod to move your post, as well as replies to it, to a separate thread.

To start troubleshooting it, we need some more detailed info. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions in the linked post, and post back the report it generates.

**PS:**
Your English seems pretty good to me. :)

---

### Post by QIII on 2014-01-10
Hello, cristina.morales4!

Moved to its own thread.  Hopefully you will get some help specific to your issue in your own thread.

Cheers!

---

