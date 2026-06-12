---
title: "Netgear A7000 trouble"
date: 2020-01-21
forum: Networking &amp; Wireless
---

### Post by jmcfadden522 on 2020-01-21
Hi, I followed a different post to get the driver installed for the A7000. All worked for about 10 minutes until it just drop the connection for no reason (as far as I can tell). It is not detecting an routers. I can still see the device using ```
lsubl
``` Double-checked the module to make sure it was still installed. Not sure what else to check. I was messing around with adding my VPN but I had not added it yet.

---

### Post by wildmanne39 on 2020-01-21
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by jmcfadden522 on 2020-01-21
[https://pastebin.com/nN6GaYFN](https://pastebin.com/nN6GaYFN)

---

### Post by wildmanne39 on 2020-01-21
How did you install the driver? it is not loading now, did you run updates and it stopped working after that? is secure boot disabled? if it is enabled follow the directions here to turn it off.

[https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS)

reboot does the driver load?

---

### Post by jmcfadden522 on 2020-01-21
> **wildmanne39 said:**
> How did you install the driver? it is not loading now, did you run updates and it stopped working after that? is secure boot disabled? if it is enabled follow the directions here to turn it off.

[https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS)

reboot does the driver load?

I used this post to do the install... [https://ubuntuforums.org/showthread.php?t=2392760&highlight=netgear+a7000](https://ubuntuforums.org/showthread.php?t=2392760&highlight=netgear+a7000)

How do I go about seeing if the driver loads or not?

I also tried disabling the secure boot and got "EFI variables are not supported on this system". I don't think it's enabled though.

---

### Post by wildmanne39 on 2020-01-21
You can see if the driver is load with:
```
lsmod
```
I missed the driver it is loaded, please go into network manger and set ipv6 to ignore and make sure your ethernet connection is unplugged because it takes priorty over wifi then reboot and see if that helps.

---

### Post by jmcfadden522 on 2020-01-21
What's the name of the driver?

I was able to change the setting on the wired connection but not the wireless connection. Unplugged the connection, rebooted and still no luck.

Is there a way to basically start over (uninstall/reinstall the driver)?

---

