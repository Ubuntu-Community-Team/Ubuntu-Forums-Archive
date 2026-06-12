---
title: "eth0 disappeared, disabled? Can't modify rf_kill"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by jayman76 on 2007-06-21
Wireless has been working on my IBM x60 since the get go, this morning I booted up and the interface just vanished. It does not show up in iwconfig or ifconfig -a. dmesg shows the that "kill switch must be off to start wireless". I found something abuot modifying the rf_kill file, but am unable to edit the file... visudo says "fsync failed" and any echo attempt to it failes with permission denied (with sudo). The value of rf_kill is 2... which I gather means the radio is off. I also tried fn+f5 which seems to do nothing. 

I also tried removing and readding the ipw3945 module.
I checked bios and found the wireless lan card is enabled.

I am truely stumped.  Please help!

---

### Post by darwin_te on 2007-07-16
Hi,

For 7.04 using the latest kernel 2.6.22, I found the following script responsible for setting rf_kill to 2 (hardware radio frequecny off):

/etc/init.d/acpi-support which called:
/usr/share/acpi-support/state-funcs

The script state-funcs checked /sys/class/net/$DEVICE/device/power/state, which has different directory structure in latest kernel, and will flag wireless state as disabled if not found, which in turn will set rf_kill to 2.

Just modify the script state-funcs and it will now work.

---

