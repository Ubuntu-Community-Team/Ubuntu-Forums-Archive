---
title: "Wireless issues after Update to 14.04"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by john_s3 on 2014-09-09
Hello

I updated my to Ubuntu 14.04 and since then my wireless network loses the connection after every 30 minutes or so.
When I disable it and enable it the connection is established again but it loses the connection again after a while.

I use the RTL8188CE wireless chipset and I already tried the FreedomBen driver from here [COLOR=#006621][FONT=arial]https://github.com/FreedomBen/[/FONT][/COLOR][B]rtl8188ce-[B]linux-[B]driver
[/B][/B][/B]but I get the same issues with that driver.

The output for the wireless-info script are attached.
Before the update from 12.04 I never had a problem and my other devices seem to be fine with the wireless router.

Do you have any other suggestions  I could do?

---

### Post by varunendra on 2014-09-11
Please try -
```
echo "options rtl8192ce ips=N" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
..followed by a reboot.

Additionally, please change the encryption in your router to WPA2-PSK with AES (CCMP) if it supports it. It is currently using WPA (1) with TKIP, which is outdated and inefficient compared to AES. Reboot the router after saving the change.

If this doesn't solve the issue, please post back a fresh report of the wireless_script with the above changes applied, preferably try this one (slightly different than the one you used above) first : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

