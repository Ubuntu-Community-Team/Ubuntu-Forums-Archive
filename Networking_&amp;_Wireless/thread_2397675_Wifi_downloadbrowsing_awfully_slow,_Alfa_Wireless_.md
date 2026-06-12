---
title: "Wifi download/browsing awfully slow, Alfa Wireless adapter | Ubuntu 18.04"
date: 2018-08-01
forum: Networking &amp; Wireless
---

### Post by ris-tlp on 2018-08-01
Installed Ubuntu 18.04 LTS using a live USB, dual boot with Windows 10.

Wifi speed is exceptionally slow for both downloading and browsing anything and often randomly disconnects as well. I'm using Alfa Wireless adapter AWUS036NHR v.2

The speed on Win10 is as it should be, I get around 1MB/s which is normal. Ubuntu gives me an average of 35kb/s which is really weird. Sometimes even around 10~15kbps.
I ran the script in one of the stickied posts and here's the output: [http://paste.ubuntu.com/p/yrfYfTnpgh/](http://paste.ubuntu.com/p/yrfYfTnpgh/)

If more information is needed, please let me know and I'll try my best to provide it. 
Thanks, cheers!

---

### Post by jeremy31 on 2018-08-01
Try ```
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl8192.conf
```
Reboot

---

### Post by ris-tlp on 2018-08-01
Oh wow, thank you so much! Worked.

---

