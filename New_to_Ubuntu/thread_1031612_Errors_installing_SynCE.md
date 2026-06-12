---
title: "Errors installing SynCE"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by abu123 on 2009-01-05
I'm trying to install SYNCE 

So installed in following order

sudo apt-get install synce-hal librapi2-tools
sudo apt-get install librra-tools

on synce-pls got error as below.

installed synce-kpm then tried above still same error.

so then installed synce-trayicon and again same error.


```

~$ synce-pls

** (process:7586): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.name for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.name on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00

** (process:7586): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pls: Could not find configuration at path '(Default)'
```

Any pointers would be great. thanks

---

