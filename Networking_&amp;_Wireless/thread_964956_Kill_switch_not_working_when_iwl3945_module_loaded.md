---
title: "Kill switch not working when iwl3945 module loaded"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by cycore on 2008-10-31
Hi,

I installed Ubuntu Intrepid today. I have trouble getting my wifi to work. It is a "Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)" controller. After boot, dmesg says:

```

[ 1763.810816] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[ 1763.810836] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[ 1763.814405] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1763.814472] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[ 1763.857280] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 1767.884542] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1767.886931] firmware: requesting iwlwifi-3945-1.ucode
[ 1767.895255] iwl3945: Radio disabled by HW RF Kill switch
[ 1767.915646] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1767.916138] iwl3945: Radio disabled by HW RF Kill switch

```

I found a way to get it working:
```

rmmod iwl3945

```
Then, i push the kill switch button, and after waiting a few secs, i reenable the module
```

modprobe iwl3945

```


This is the only way I can get it to work. If i press the killswitch button when wifi is on, it gets disabled just as it is supposed to be:
```

[ 2029.002193] iwl3945: Radio Frequency Kill Switch is On:
[ 2029.002199] Kill switch must be turned off for wireless networking to work.
[ 2029.007067] atkbd.c: Unknown key pressed (translated set 2, code 0xe1 on isa0060/serio0).
[ 2029.007083] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2029.249494] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[ 2029.249512] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2031.909234] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 2031.959193] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 2032.019135] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 2032.183010] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC

```

However, I cannot enable it again by pressing the killswitch button. Noting happens:
```

root@cycore-notebook-linux:/home/cycore# cat /sys/devices/pci0000\:00/0000\:00\:1c.0/0000\:02\:00.0/rfkill/rfkill*/state 
2

after pressing button:
root@cycore-notebook-linux:/home/cycore# cat /sys/devices/pci0000\:00/0000\:00\:1c.0/0000\:02\:00.0/rfkill/rfkill*/state 
2

```

Syslog only says:
```

[ 2190.890590] atkbd.c: Unknown key pressed (translated set 2, code 0xe1 on isa0060/serio0).
[ 2190.890605] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2191.223504] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[ 2191.223519] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
```


As already mentioned, I have to unload iwl3945 first. When unloaded, the button works! When iwl3945 is loaded, it only works to turn the wifi off, but not back on.

Does anyone have a solution for this?
Your help is appreciated!

---

### Post by cycore on 2008-10-31
As explained in some other forum posts, I tried this:
```
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```

Interestingly, the wifi adapter works, as soon as I execute rmmod iwl3945. The module is still loaded, and apparently cannot be unloaded. However, I have to exectue this command every time I use the killswitch button to get my adapter to work

---

### Post by nadalizadeh on 2008-11-03
I've the same problem.

I think this issue needs a launchpad bug report to be opened.

---

### Post by cycore on 2008-11-03
It would be nice if you could do this, because I'm not really experienced in that kind of stuff and tend to get ignored...


I found some more relevant info regarding this bug:

- The killswitch status change works, but isn't registered by anything. So it has no effect. However if you do a 
```
modprobe -r iwl3945 && modprobe iwl3945
```
the state is recognized and Wifi is turned on. Apparently, the state of the switch is only read during module startup, but not polled while its running (or notified via events or something)

- In my case, the kill "switch" is in fact a button, not a switch. It doesn't stay in a position, e.g. in in or out, but is just like any other button on the keyboard.

---

### Post by smbm on 2009-02-27
Does anyone know what the root of this problem is?

Is there a bug report on Launchpad that anyone knows of?

It's still not fixed in Jaunty so far!

I'd like to try and fix it but don't know where to start.

---

### Post by cycore on 2009-02-27
I did not file a new bug report, but back then, when I still cared for this problem, there were plenty of other bug reports. Now, I don't use Ubuntu any more, cause it's just too full of bugs.

---

### Post by smbm on 2009-02-27
What do you use now?

Is this bug fixed in that?

---

### Post by jsegel on 2009-05-22
apparently not fixed. this isn't working for me, though it looked promising. my switch is also a dedicated keyboard key, apparently not recognized my ubuntu...

---

### Post by jsegel on 2009-05-27
from another thread:
You can download the driver from here:
Code:

[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz)

unzip it and copy the iwlwifi-3945-2.ucode file into the /lib/firmware directory


this worked for me on hp compaq nc6320.

---

### Post by kasiopi on 2012-01-09
> **jsegel said:**
> from another thread:
You can download the driver from here:
Code:

[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz)

unzip it and copy the iwlwifi-3945-2.ucode file into the /lib/firmware directory


this worked for me on hp compaq nc6320.

Had the same problem. This fix worked for me too.

---

