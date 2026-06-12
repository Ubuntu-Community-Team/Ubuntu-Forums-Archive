---
title: "different iwl3945 troubles"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by namelessone on 2008-08-26
I am having trouble with the iwl3945 driver, but my problem is different than most people's problems.

I have a custom kernel, and I compiled compat for it. I ran make load, and it appears to detect my wireless card, but I can't scan for networks.

I tried the disable_hw_scan=1 thing I've seen in other posts, but that doesn't help--I'm pretty sure I've got a different problem. Here's my dmesg output:
```

ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
firmware: requesting iwlwifi-3945-1.ucode
iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
iwl3945: Could not read microcode: -2
```

Any suggestions on how to fix this?

---

### Post by Blackcabs on 2008-09-01
> **namelessone said:**
> I am having trouble with the iwl3945 driver, but my problem is different than most people's problems.

I have a custom kernel, and I compiled compat for it. I ran make load, and it appears to detect my wireless card, but I can't scan for networks.

I tried the disable_hw_scan=1 thing I've seen in other posts, but that doesn't help--I'm pretty sure I've got a different problem. Here's my dmesg output:
```

ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
firmware: requesting iwlwifi-3945-1.ucode
iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
iwl3945: Could not read microcode: -2
```

Any suggestions on how to fix this?

The firmware for your card has failed to load you could try

$ ls -1 /lib/firmware/$(uname -r)/iwl*
/lib/firmware/2.6.24-21-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-21-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-21-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-21-generic/iwlwifi-4965.ucode

---

### Post by slumbergod on 2008-09-01
The only way I managed to solves all my wireless woes with intel 3945 was to install the compat-wireless drivers and use wicd. I considered compiling a kernel but decided that it was a lot of effort without any promise of success.

Amazingly, I now see networks lots of networks that I previously hadn't seen before. And I never get disconnected.

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
[http://ubuntuforums.org/showthread.php?p=5690046](http://ubuntuforums.org/showthread.php?p=5690046)
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

