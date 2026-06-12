---
title: "How do I uninstall lwfinger rtlwifi drivers?"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by roquet2 on 2015-08-08
Xubuntu 14.04 on Asus X200MA
Kernel: 3.16.0-45-generic

I'm often getting packet loss with an RTL8188ee wifi card, so I want to see if it's better with this driver:
```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
```
But I read that the lwfinger driver should uninstalled first, as stated in this post:
[http://ubuntuforums.org/showthread.php?t=2283759 ]("http://ubuntuforums.org/showthread.php?t=2283759")

My question is how do I uninstall it? I saw this command: 
```
sudo make uninstall
```
But which directory do I need to be in when I run it?

Perhaps someone could confirm that I do indeed have the new lwfinger rtlwifi drivers installed at the moment. (I've been trying lots things so I'm not sure if I installed them with the commands below or if they were already there as part of the 3.16.0-45 kernel.) 
```
sudo apt-get install build-essential linux-headers-generic git dkms
git clone http://github.com/lwfinger/rtlwifi_new.git
cd /path/to/rtlwifi_new
make
sudo modprobe -rv rtl8188ee
sudo make install
sudo modprobe -v rtl8188ee
```
Here is the relevant section from the wireless-info script:
```
##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/[COLOR="#FF0000"]rtlwifi[/COLOR]/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@[COLOR="#FF0000"]lwfinger[/COLOR].net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     83E9F79B1C7C341263B448E
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512

```

Thanks for any help on this.

---

### Post by praseodym on 2015-08-08
Run:
```

cd /path/to/rtlwifi_new
make clean
make
sudo make uninstall
sudo apt-get install --reinstall rtlwifi-new-dkms linux-firmware

```

---

### Post by roquet2 on 2015-08-08
Thanks for the instructions.

Sorry if this is a silly question, but is "/path/to/rtlwifi_new" the actual path or something I need to fill in myself? I did ```
cd /path/to/rtlwifi_new
``` and it says```
bash: cd: /path/to/rtlwifi_new: No such file or directory
```

I see I've got an rtlwifi folder in /lib, here:
```
/lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi
``` Is that what I should be uninstalling?

---

### Post by Jim_D on 2015-08-10
Hi roquet2,

I also have an Asus X200MA with 14.04 (Ubuntu rather than Xubuntu).  I also have trouble with my wireless and the RTL8188ee adapter (frequent connection drops).  I started a thread about it - [http://ubuntuforums.org/showthread.php?t=2289993](http://ubuntuforums.org/showthread.php?t=2289993) - and in the meantime was also trying the ppa:hanipouspilot/rtlwifi rtlwifi-new-dkms like you, to get an updated, improved driver.  I just installed it this morning (just using the PPA and sudo apt-get install rtlwifi-new-dkms), and didn't have any luck yet.  It seems like it's installed, but wireless can't connect at all to my network, and I uninstalled it again for the time being.

I also made changes to get my X200MA's Focaltech touchpad recognized using ppa:hanipouspilot/focaltech-dkms, including the kernel upgraded to 3.19.  That worked for the touchpad.  But I'm not sure whether I'm having issues related to using rtlwifi-new-dkms with kernel 3.19 instead of 3.16.  Or maybe it's because I didn't install the "linux-firmware" package mentioned below.  Or maybe it's that I haven't properly cleaned up another driver, like you mentioned in the title of your thread.

I'll keep watching your thread to see if you have any luck, and will make sure to update my thread if I can improve things.  I was glad to see someone else trying to work out the same thing at the same time!

Thanks,
Jim

---

