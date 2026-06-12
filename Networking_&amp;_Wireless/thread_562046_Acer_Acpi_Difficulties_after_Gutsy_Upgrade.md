---
title: "Acer_Acpi Difficulties after Gutsy Upgrade"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by mrgnash on 2007-09-28
The only way I was able to get wireless working on my Travelmate 4402 was to use ndiswrapper and acer_acpi, and despite a few difficulties along the way it did work pretty well. Now, however, I'm not having much luck at all. I can get as far with the process as runninng 'modprobe acer_acpi' without returning any errors, and ndiswrapper reports my device as present -- I can also see wlan0 in iwconfig -- but the LED will just not switch on; when I enter:

```
 echo "enabled: 1">/proc/acpi/acer/wireless
```

I get:

```
bash: echo: write error: Invalid argument
enabled: 1

```

And no change in the LED status :(

Dmesg reports the following:

```
[  127.916000] acer_acpi: Acer Laptop ACPI Extras version 0.9.0
[  127.916000] acer_acpi: Detected Acer AMW0 interface
[  127.916000] acer_acpi: No EC data for reading bluetooth - bluetooth value when read will be a 'best guess'
[  127.916000] acer_acpi: No EC data for reading wireless - wireless value when read will be a 'best guess'
[  127.916000] acer_acpi: No EC data for reading mail LED - mail LED value when read will be a 'best guess'
[  127.916000] acer_acpi: We need more data from your laptop's Embedded Controller (EC) to better support it
[  127.916000] acer_acpi: Please see http://code.google.com/p/aceracpi/wiki/EmbeddedController on how to help

```

Any help would be greatly appreciated because I don't know what to do next :(

---

### Post by mrgnash on 2007-09-28
Nevermind. The issue has been resolved thanks to the help of one of the acer_acpi developers :)

---

### Post by vangelm on 2007-09-29
and please, how??? I have same problem.

---

### Post by moosesoom on 2007-10-25
Think the right command is:

```
echo "1" >/proc/acpi/acer/wireless
```

---

