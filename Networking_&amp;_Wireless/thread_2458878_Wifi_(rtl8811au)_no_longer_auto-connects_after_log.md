---
title: "Wifi (rtl8811au) no longer auto-connects after login (Ubuntu 20.04 LTS)"
date: 2021-03-05
forum: Networking &amp; Wireless
---

### Post by gigabyte56 on 2021-03-05
Until a few weeks ago, my wifi connection has been absolutely reliable, and in particular, it has always connected automatically on login. Now, it fails to connect automatically, and I have to re-enter my wifi password each time, and that is becoming very tedious. I can see that others have reported something very similar (eg. [https://ubuntuforums.org/showthread.php?t=2458231](https://ubuntuforums.org/showthread.php?t=2458231)), but I haven't found a solution to the problem.

I have run the wireless-info script, and the output can be found here: [URL="https://paste.ubuntu.com/p/FQB2wJh3GJ/"]https://paste.ubuntu.com/p/FQB2wJh3GJ/

[/URL]Any ideas on how to resolve this, please?

---

### Post by morrownr on 2021-03-09
I did not see anything obvious in the script output. If it were me, I would uninstall the existing driver and go to the following site:

[https://github.com/morrownr/8821au](https://github.com/morrownr/8821au)

This driver is modern and is solid. It is a clean compile and leaves a clean log. Installation instructions and a lot of good information is included at the site.

Good luck.

---

### Post by gigabyte56 on 2021-03-20
Thanks for the advice, morrownr. The new driver works fine, but sadly it doesn't resolve the auto-connect problem.

---

### Post by ajgreeny on 2021-03-20
Have a look at the settings for network-manager, assuming that is what you are using, and make sure it is still set to autocennect  and for all users if that's what you want.
I have absolutely no idea why they might have changed but it's worth a quick look-see.

All those settings are in the General Tab-  see my screenshot.

---

### Post by gigabyte56 on 2021-03-20
Thanks ajgreeny. Yes, it is still set to 'autoconnect for all users'. In the past, I've changed this value to other possible values and applied my changes, before finally reverting to 'all users', but this has not helped.

I've just posted a comment to the thread at [https://ubuntuforums.org/showthread.php?t=2458231](https://ubuntuforums.org/showthread.php?t=2458231), to say that I too see a different output from iwconfig after each boot, which may provide a clue. That is, the device identifier (?) changes, for example, from wlx00e04c508a9a to wlx00e04c050c6f. This may explain why I see multiple entries in the list of known networks which are all prefixed with my SSID, followed by a unique integer that increases after each connection is made. If my computer never sees the same network twice, then this may be why I have to enter my password each time I connect?

---

### Post by ajgreeny on 2021-03-20
It almost sounds like a router problem.

Might be worth rebooting the router and double checking the settings of that.

---

### Post by gigabyte56 on 2021-03-21
It does look like the problem was due to Ubuntu renaming the network interface each boot, from "wlan0" to something variable of the form "wlx00e04c508a9a". My googling activity took me to [https://unix.stackexchange.com/questions/491754/why-is-my-wlan-device-being-renamed](https://unix.stackexchange.com/questions/491754/why-is-my-wlan-device-being-renamed), which suggested that interface renaming could be disabled by updating /etc/default/grub. The guidance stated the following:

Put "net.ifnames=0" into the kernel command line (e. g. in   /etc/default/grub's GRUB_CMDLINE_LINUX_DEFAULT, then run "update-grub")

Having made this change and rebooted the machine, the wifi interface now remains "wlan0", and my password is being saved.

---

