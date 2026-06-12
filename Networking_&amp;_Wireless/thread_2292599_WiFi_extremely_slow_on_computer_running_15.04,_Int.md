---
title: "WiFi extremely slow on computer running 15.04, Intel Centrino Ultimate-N 6300"
date: 2015-08-29
forum: Networking &amp; Wireless
---

### Post by todd19 on 2015-08-29
Script results: [http://pastebin.com/Gs0ub0Br](http://pastebin.com/Gs0ub0Br)

For a few months now my WiFi has been much slower than other devices connected to the same router. From the same location, other PC's and Macs routinely get ~100Mpbs down while my computer, (3 year old Sony Vaio), maxes out at around 25Mpbs while averaging ~10Mpbs. The problem effects both 2.4GHZ and 5GHZ networks, but 5GHZ is slightly faster (but still no where near where it should be). I installed the Intel Centrino Ultimate-N 6300 over my stock card to remedy the problem, but it didn't seem to help with the speed, only the range. I'm hoping it's a software problem, but I'm unsure as to what would be causing this. The problem persisted even after upgrading from 14.04 up the the latest release.

---

### Post by jeremy31 on 2015-08-29
You may have already tried this parameter ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot and test, with the parameter set to 8 it will enable agg tx and should boost the speed

And you could set the regulatory country setting with
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo iw reg set US
[/FONT][/COLOR]sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```

---

### Post by todd19 on 2015-08-29
I have tried with that parameter, I saw a minor if non-existent speed boost.

---

### Post by jeremy31 on 2015-08-29
Power Management is enabled on the wifi, you can turn it off with```
sudo iwconfig wlan1 power off
```

---

