---
title: "Acer 5051 / Atheros / WLAN"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by .len on 2007-04-14
Hi,

few days ago I bought an Acer 5051AWXMi. I Thought it would be easy to set up my network, but it isn't :(

I'm using Feisty 7.04 with all updates installed.

Following device is detected :

```
lspci | grep Atheros
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01) 
```

```
*-network UNCLAIMED
                description: Ethernet controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:d0200000-d020ffff irq:19 
```

Restricted modules are installed, but the device cannot be detected. So I tried to use the latest drivers from madwifi.org, but the lspci-output doesn't change.

Ifconfig/iwconfig doesn't show ath0 or wlan0, so i can't try to set it up.
These modules are actually loaded:

```
lsmod | grep ath
ath_pci                97184  0
wlan                  203632  1 ath_pci
ath_hal               192592  1 ath_pci 
```

I also tried to install the acer_acpi module ([http://ubuntuforums.org/showthread.php?t=224349](http://ubuntuforums.org/showthread.php?t=224349)) but i got the same error like some other users (FATAL: Error inserting acer_acpi: No such device).

I don't know which Atheros-Chip is in my notebook, but it seems that it is actually unsupported.

Is there anything else I can do, or should I wait for a new madwifi-release?

Thanks for your help :(

---

### Post by elamericano on 2007-04-14
You can go get the 0.9.3 release from the madwifi.org website.

Here is someone who got it working with Debian, so Ubuntu will work too:
[http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi#wireless_lan](http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi#wireless_lan)

---

### Post by .len on 2007-04-14
Thanks for your response,

I already tried to compile version 0.9.3, using [this]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") Tutorial, but I also got the same message (unknown Device).

In addition to that, I downloaded the latest version via subversion and compiled it - same output.

I got the same results as I installed madwifi on an edgy-sytem.

Maybe there are several chips inside the acer notebooks :(

---

### Post by elamericano on 2007-04-15
Restricted modules may be already providing you with the wrong HAL. I'm just guessing at this point, since you seem to have done a lot on your own. Did you follow the distro-specific instructions?

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by .len on 2007-04-16
Thanks for this link, haven't seen it before.

This time I followed the instructions ;)

I have disabled the module and compiled again, but nothing has changed :(
I still get the same output, it seems like the latest drivers doesn't support my device.

I will try to reach somenone at the Acer-hotline. Maybe he/she is able to tell me, which chip is inside my notebook.

---

