---
title: "Was unable to input my WEP key but now I can"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2007-07-11
Returning from holiday today I downloading and installing the many updates waiting but only after first checking with the Forum for any obvious warnings.
With my rt2500 PCI card under Feisty I've been having to manually input my essid and WEP key only after first downing ra0 as shown below      (waiting a new rt2x00 driver I am)

```
sudo ifconfig ra0 down
sudo iwconfig ra0 essid "myessid" key xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
sudo ifconfig ra0 up
sudo dhclient ra0
```

After installing the updates and a reboot the above method set my essid but no longer my WEP key. I discovered that now to set my WEP key ra0 had to be up.

Has anyone else reported this?

---

