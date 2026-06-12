---
title: "Set WiFi to low power mode by default?"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Schalken on 2008-06-08
According to lesswatts.org , I can throw my WiFi card into a low power, low performance mode with the command ```
echo 5 > /sys/bus/pci/drivers/iwl4965/*/power_level
```
and this seems to save from 2 to 4 watts! :O

How can I make this the default when I turn the computer on and resume from suspend?

---

