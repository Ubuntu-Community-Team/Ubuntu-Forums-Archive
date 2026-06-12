---
title: "No WLAN after standby"
date: 2014-09-14
forum: Networking &amp; Wireless
---

### Post by chris260 on 2014-09-14
Hi all, 

I am running Ubutu 14.04.1 LTS on a Lenovo x220i.

I have a problem where when resuming from standby there does not seem to be an active Wirless Card, I try to disable and reenable but I cannot get it to reconnect.  This isn't always the case, sometimes when coming out of standby the connection resumes, other times I have to reboot the machine.

I've tried:

1) Restarting network services
2) Upgrading from Ubuntu 12 to 14 (current version)
3) A different router (although I don't think this is the cause).

My full specs are:
Lenovo x220i
Intel® Core™ i3-2310M CPU @ 2.10GHz × 4 
8GB RAM

NIC info from lspci -v

[FONT=arial narrow]03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f2400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number a0-88-b4-ff-ff-89-45-10
    Kernel driver in use: iwlwifi[/FONT]

I've just checked and I'm using the Ubutu provided driver for this card so I will check Intel for a Linux driver, any help appreciated,

Thanks

C

---

### Post by varunendra on 2014-09-14
Please try creating a configuration file that is supposed to unload the wifi module before going to suspend/sleep, and reload them at resume -
```
echo 'SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi"' | sudo tee /etc/pm/config/modules
```
Then reboot > go through a suspend/resume cycle and let us know if it works. If not, please post back the output of -
```
cat /var/log/pm-suspend.log
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

