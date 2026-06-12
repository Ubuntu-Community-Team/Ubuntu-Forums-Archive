---
title: "Related 8821 WiFi driver"
date: 2016-07-16
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2016-07-16
Folks,

Still running 12.04 LTS as main system due to reliability.

Recently changed computers to a Toshiba Satellite but system not recognising the Realtek  8821 AE pci-e-nic wifi

I can see there are a few issues with this device but what is puzzling me is on the Realtek web site I can find no reference to this device.

Any suggestions appreciated - fortunately Ethernet OK &#128514;

Geffers

---

### Post by Frogs Hair on 2016-07-16
Moved to *Hardware*

---

### Post by Yellow Pasque on 2016-07-16
I believe it should work on Precise if you run a 3.13 or later kernel. Don't quote me on that though: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1287298](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1287298)

If you don't already have them, you may need to grab the two rtl8821ae files from here: [http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/rtlwifi](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/rtlwifi)
Place them in /lib/firmware/rtlwifi/

---

### Post by Geoff_Lane on 2016-07-17
Folks,

Still running 12.04 LTS as it is stable.

Changed computers and new one has a Realtek 8821 adapter, NOT recognised at all.

Suggestions are that 8812au would work so followed the excellent instruction as follows;
[https://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/](https://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/)

No errors given but still no WiFi.

This is the land read out I get;
geoff@mercury:~$ sudo modprobe 8812au
geoff@mercury:~$ lsmod | grep 8812au
 8812au*************** 889414* 0 
cfg80211************* 178877* 1 8812au
geoff@mercury:~$ 

Any suggestions appreciated.

Geffers

---

### Post by slickymaster on 2016-07-17
*Thread moved to **Networking & Wireless**.*

---

### Post by jeremy31 on 2016-07-17
Please post the result of ```
lspci -nnk | grep -iA2 net; uname -r
```
There may be a couple of ways to solve this, backports or updating the HWE(Hardware Enablement Stack)
Updating the HWE involves a much newer kernel but backports would have to be reinstalled with every kernel update

---

### Post by Yellow Pasque on 2016-07-17
Please don't post duplicates: [https://ubuntuforums.org/showthread.php?t=2330907](https://ubuntuforums.org/showthread.php?t=2330907)
Did you verify that you have the correct firmware files in place as I asked in that thread?

Also, verify what kernel you're using (so we don't have to guess):
```
uname -a
```

---

### Post by QIII on 2016-07-17
Threads merged.

After inserting the module, are you using ifdown and ifup?

Are you rebooting?  That may require reloading manually unless you change your conf files.

My Odroid has the same 8821 chip and I use the 8812au driver.  The module has to be loaded via configuration at startup and with that particilar adapter I have to script shutting off the power management.

---

### Post by Geoff_Lane on 2016-07-19
> **jeremy31 said:**
> Please post the result of ```
lspci -nnk | grep -iA2 net; uname -r
```


```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:f840]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8821]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:2162]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
3.2.0-105-generic-pae



```

Geffers

---

### Post by Geoff_Lane on 2016-07-19
For some reason I cannot reply to and/or quote [COLOR=#000000]Temüjin previous enquiry as to the following;[/COLOR]

[COLOR=#000000]Did you verify that you have the correct firmware files in place as I asked in that thread?

Yes and the uname -r  gives [/COLOR]3.2.0-105-generic-pae

Geffers


[COLOR=#000000]

[/COLOR]

---

### Post by Geoff_Lane on 2016-07-19
For some odd reason I went to edit this message and get NO TEXT so will have to repeat the message which may appear twice.


Original post xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
[COLOR=#000000]For some reason I cannot reply to and/or quote [/COLOR][COLOR=#000000][COLOR=#000000]Temüjin previous enquiry as to the following;[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Did you verify that you have the correct firmware files in place as I asked in that thread?

Yes and the uname -r gives [/COLOR][/COLOR][COLOR=#000000]3.2.0-105-generic-pae[/COLOR]

[COLOR=#000000]Geffers
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Intended to add, still doesn't show wifi

Geffers

[/COLOR]

---

