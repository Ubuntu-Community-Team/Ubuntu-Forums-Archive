---
title: "[Hardy] acerhk wont start anymore"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by !GN!T!ON on 2008-08-26
hi, after installing ubuntu 8.04 on my acer aspire 5610Z everything worked except my wireless, after some googling i found acerhk, wich enabled my media buttons and after a reboot also enabled my atheros 5007EG :D

this worked for a week or to, but today i went to school, and in class i found out that my wireless wasnt working anymore

so i tried

```
# modprobe acerhk
```

wich returned:

```
sh: cannot create /proc/driver/acerhk/wirelessled: Directory nonexistent
FATAL: Error running install command for acerhk

```

after cding to /proc/driver i did an ls and the acerhk directory is gone :(

so i tried to reboot, didnt work, then i tried to reinstall acerhk, didnt work either :(

then i tried to google for the error, but google found only one page wich seems to give me a 404 :confused:

does anyone have an idea? i could try to use acer-acpi, but i dont realy want to because acerhk used to work fine, and acer-acpi doesnt support my mediakeys

help is much appreciated!

:)

---

