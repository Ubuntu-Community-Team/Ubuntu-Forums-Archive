---
title: "Disabling laptop bluetooth from Windows cannot be enabled in Ubuntu 20.04"
date: 2020-08-30
forum: Networking &amp; Wireless
---

### Post by nehalmistry on 2020-08-30
I have an Acer V5-531 Laptop.

In Ubuntu when I press FN+F3 on the keyboard, it toggles WiFi.
In Windows, FN+F3 launches this small dialog called 'Launch Manager' where you can either disable WiFi or Bluetooth.

[ATTACH=CONFIG]286842[/ATTACH]

If I disable Bluetooth from the Launch Manager, it's disabling it at a very low level. It gets removed from Device Manager. Then when I boot into Ubuntu it doesn't recognize the device at all. It doesn't show in either 'dmesg' or 'rfkill'. The only way to enable it again is to go back into Windows.

My question is: anyone have any ideas how I would enable Bluetooth from Ubuntu?

Not really a problem at all as you can simply leave this enabled from Windows. But I was curious so thought I would ask anyway. Please let me know if you have any questions.

Thanks!

---

### Post by CelticWarrior on 2020-08-30
Welcome.

Try again after disabling Fast Startup in Windows. Always recommended and a must if dual-booting because in reality it's just hibernation and hibernation tens to do that to some devices.

---

### Post by nehalmistry on 2020-08-30
> **CelticWarrior said:**
> Try again after disabling Fast Startup in Windows. Always recommended and a must if dual-booting because in reality it's just hibernation and hibernation tens to do that to some devices.

I should have clarified that it's Windows 7 (it's an older laptop). There is no Fast Startup setting and I don't have any equivalent enabled.
Also, if I shutdown, unplug the power, unplug the battery, then plug everything in again and cold boot into Ubuntu, it retains the last setting from Windows.

It almost feels like the 'switch' is at the BIOS level, even though the only way to change it is within Windows.

---

