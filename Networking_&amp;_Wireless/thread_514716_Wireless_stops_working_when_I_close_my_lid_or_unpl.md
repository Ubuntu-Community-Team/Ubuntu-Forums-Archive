---
title: "Wireless stops working when I close my lid or unplug my laptop"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by JJFO on 2007-08-01
Sometimes when I close my lid or unplug my laptop, my wireless drops, and when I go into network manager it says wired connection where it used to say wireless connection. The only way I've found to fix it is to restart my computer, but this is really frustrating. Anyone have any ideas?

Thanks

---

### Post by cobalt blue on 2007-08-01
I am having this problem also.  My wireless connection stops working when I close the laptop lid.  I need to reboot to get it working again.

Does anyone know if there is a way to fix this problem?

Thank you!

---

### Post by JJFO on 2007-08-03
Is this a known bug, or is there a way to fix it?

---

### Post by noob12 on 2007-08-03
What wireless card and what driver?  Posting the results of ```
lspci -nn
``` and ```
lshw -C network
``` would tell us.

If you can run the following commands before and after you close your lid, save the results and post them when you've recovered, it could help diagnose the problem
```

iwconfig

iwlist scan

cat /sys/class/net/*/driver/rf_kill

```

---

### Post by noob12 on 2007-08-04
In **System|Preferences|Power Management** do you have the option set to suspend when the lid is closed?

If you haven't set it to suspend, then most likely this is due to power management on the wireless device causing it.  Hence the requests for that information.  We may be able to solve it if you provide more info.

I'm also assuming you don't have any custom ACPI stuff that you've put in /etc/acpi/local/lid.sh?  If you have, let me know.

---

