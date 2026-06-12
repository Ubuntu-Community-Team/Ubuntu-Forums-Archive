---
title: "Intel 3945ABG, new iwlwifi 1.2.26ks and suspend"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by oofnik on 2008-10-09
The fact that the LED on my Thinkpad X60 tablet didn't work with the packaged version of iwl3945 in Hardy finally got to me, so I started looking around for a way to update it thinking someone figured it out. As it turns out, I was right. I found the page for the [compat-wireless]("http://linuxwireless.org/en/users/Download") project on the Intel Linux Wireless site and followed the install instructions. Everything works great with the new driver, including the LED.. awesome.
Until I suspend / resume.

Being in college, I need to suspend/resume multiple times a day between classes. As long as I was careful about what was plugged into USB, I didn't have too many problems. But with the new wireless driver, I've encountered some particularly strange behavior.

The first suspend/resume cycle after a reboot comes back up OK. But if I suspend/resume again, when the system wakes up and starts trying to find a network, everything halts. The mouse moves, but the pen stops working, applications can't be opened, but the GUI responds. It's like something deep down in the kernel is locked up. And the weirdest part: if I turn on the wireless kill switch, the weird behavior stops! I've tried unloading/reloading the iwl3945 module a billion times, turning the kill switch on/off.. nothing but a reboot will work to get my wireless back after the 2nd suspend/resume cycle, and it's consistent.

Usually, third suspend/resume cycle will hang altogether before going fully to sleep and I have to do a hard reset.

I even downloaded the latest microcode off the site just to make sure. And for some even weirder behavior - I used to press the wireless function key on my Thinkpad (Fn + F5) which would cycle like this, as set since IBM's wireless utility in Windows XP:
```

     wifi    bt
a     on    off
b     off   off
c     on    on

```

Now, the switch only activates bluetooth on/off. And super weird: booting back into Windows XP, IBM's wireless connections manager is now totally unable to turn off the wireless radio. What the hell? Does this have to do with something in the updated microcode released with the Linux driver?

But back to Ubuntu, here are some of the things I can grab from logs that may be able to help. First of all, iwl3945 version:
```
iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
```

Errors after second suspend/resume cycle start showing up:
```
[  236.987146] iwl3945: Error sending REPLY_LEDS_CMD: iwl3945_enqueue_hcmd failed: -5
[  264.321357] iwl3945: Error sending REPLY_TX_PWR_TABLE_CMD: iwl3945_enqueue_hcmd failed: -5
```

This comes up occasionally as well: 
```
iwl3945: MAC is in deep sleep!
```

Sorry it's a bit of a mess, I will try to get the errors in chronological order when I have some more time. I googled some of these errors and they seem to occur on several different brands of laptops with this chipset. Please let me know if more information is required. 
If anybody who has an Intel wireless chipset is willing to suspend/resume several times in a row to see if/how wireless breaks on their system, I would appreciate the results!

I'd like to file a bug report if I could get more consistency and a better way of describing the symptoms, i.e. what's causing the strange lockup behavior and why the kill switch fixes it temporarily. Thanks!

---

### Post by oofnik on 2008-10-17
I solved this issue by removing the compat-wireless project and installing the linux-backports-modules-2.6.24-19-generic package from the Hardy backports repository. Version 1.2.25 of the iwl3945 is now installed and works perfectly, rock solid after 6 continuous suspend/resume cycles.
The wireless LED is a solid on, no flashing, but that's better than a solid off.

It seems the 1.2.26ks version frozen in the compat-wireless-old distribution is just buggy. I'm not sure how to go about filing a bug report for this, but I'm happy that it now works.

---

