---
title: "1, maybe 2 problems with Ubuntu Power Management"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by A Student Philosopher on 2009-11-11
I'm on a Dell Vostro 1000 Laptop, relatively new to Ubuntu and using Karmic.

When I unplug my laptop and plug it back in, nothing happens. Unless the battery is under 50% or so (I don't have the exact percentage but at least 35%, a good 20-30 minutes left on the battery.). Once it registers that it is on AC power it notifies me that the battery is critically low as is about to hibernate.

I've messed with the power options but there doesn't seem to be an option for turn the 'critically low' event off, or any indication of why it's not working correctly.

The other problem I've been running too and I don't know if it's related. Is that after my laptop hibernates or suspends and I press the power button. The indicator light comes on but the screen does nothing. I have to then shut it down completely and restart.

Any help would be appreciated.

---

### Post by lavinog on 2009-11-11
This is a bug that many are experiencing with intel video drivers:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/385445](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/385445)
can you post the output of **lspci** (from the terminal).

---

### Post by A Student Philosopher on 2009-11-11
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

---

### Post by lavinog on 2009-11-11
> **A Student Philosopher said:**
> 
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]

Ok you don't have the intel card.  I have a laptop with that same card, but I haven't tested the suspend/hibernate yet.

I will see what I can find out.

---

### Post by lavinog on 2009-11-11
see what the following give you for your battery:
```

cat /proc/acpi/battery/BAT?/info

cat /proc/acpi/battery/BAT?/state

```

---

### Post by lavinog on 2009-11-11
the suspend issue looks like a kernel issue.
it can be debugged following this:[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

I will try this later, but I have to go at the moment.

---

### Post by lavinog on 2009-11-11
I do suffer from the same issue.
Plugging in the power cord causes the reported charge to drop significantly.
[img]http://ubuntuforums.org/attachment.php?attachmentid=135851&stc=1&d=1257992332[/img]
The yellow area is when I plugged in the charger.

I will check to see if a bug report needs to be filed.

---

### Post by A Student Philosopher on 2009-11-11
```
cat /proc/acpi/battery/BAT?/info
present:                 yes
design capacity:         2900 mAh
last full capacity:      2057 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 250 mAh
design capacity low:     50 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            DELLTM7877
serial number:           10
battery type:            LION
OEM info:                Sanyo
```

```
cat /proc/acpi/battery/BAT?/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            813 mA
remaining capacity:      1128 mAh
present voltage:         16079 mV
```Thanks for your efforts, I didn't know information like this on my battery existed. That's awesome!

I would never have suspected my video card, how does that affect my reported charge?

---

### Post by lavinog on 2009-11-12
> **A Student Philosopher said:**
> Thanks for your efforts, I didn't know information like this on my battery existed. That's awesome!

I would never have suspected my video card, how does that affect my reported charge?

The video card can cause the suspend the fail.  I don't know a lot of details, but the issue can be memory address space related (the video card on a laptop shares memory,) or there can be a bug in the kernel module.


The battery issue only seems to happen if I discharge for a long period of time (from 90% to 20%.)  If I put it on the charger every now and then for a short period of time, it doesn't do it.

another command to get battery info is:
```
devkit-power -d
```

I noticed that a lot of the code in the power manager is similar to devkit-power.  I found a bug report (lost the link) that mentioned that power manager will deviate from the acpi over time.  I think the deviation is corrected when there is a change in the charge state, and that correction is what is causing the hibernation sometimes.

There are numerous bug reports requesting not to hibernate if it is detected that the battery is charging.  So it should be fixed sometime.

---

### Post by coffeeshawn on 2010-01-10
I also have a Dell Vostro 1000 and was seeing these same issues.

I still have the problem with the battery's report charge after plugin.

However, I did come across a recent post in these forums for dealing with the suspend/hibernate issue.  Basically, it involves downgrading the ati/radeon drivers to the jaunty version.

The post with instructions is here:

[S]http://ubuntuforums.org/showthread.php?t=137184[/S]  - [Edited 1/17/2010, posted incorrect URL]

[http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

---

### Post by A Student Philosopher on 2010-01-10
Thanks for the idea, but can you double check the link you provided? I wasn't seeing instructions.

---

### Post by coffeeshawn on 2010-01-17
Sorry... accidentally lopped off a digit when I copied the URL.

[http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

Thread name:  [SOLVED] No Resume after Suspend on Dell Vostro 1000

---

### Post by A Student Philosopher on 2010-01-26
Thanks for the tip, but I found this morning when my batter went down to %20 and plugged it in. It worked! WOOT! I never thought I'd be happy to have a low charge on my battery!

I'm thinking it was the regular updates because I haven't touched my power settings.

---

